---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten in Azure Blob Storage | Microsoft-Dokumentation
description: Erläutert das Konfigurieren von PolyBase in Parallel Data Warehouse für die Verbindung mit externen Hadoop.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 09bac30e30a6549dd572b8594e5efeec6473ef2a
ms.sourcegitcommit: 5afec8b4b73ce1727e4e5cf875d1e1ce9df50eab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47450349"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in Azure Blob storage

Der Artikel erläutert die Verwendung von PolyBase in SQL Server-Instanz zum Abfragen von externen Daten im Azure-Blob-Speicher.

> [!NOTE]
> APS unterstützt derzeit nur standard Allgemein v1 lokal redundanten (LRS) Azure-Blob-Speicher.

## <a name="prerequisites"></a>Erforderliche Komponenten

 - Azure Blob Storage in Ihrem Abonnement her.
 - Ein Container in Azure Blob Storage erstellt wird.

### <a name="configure-azure-blob-storage-connectivity"></a>Konfigurieren von Azure Blob Storage-Konnektivität

Konfigurieren Sie zuerst installiert wird, um Azure Blob Storage verwenden.

1. Führen Sie [Sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) mit "Hadoop Connectivity" auf ein Azure-Blob-Speicheranbieter festgelegt. Der Wert für Anbieter finden Sie unter [Konfiguration der PolyBase-Netzwerkkonnektivität](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure Blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. APS-Region, die mithilfe von dienststatusseite auf Neustart [Appliance-Konfigurations-Manager](launch-the-configuration-manager.md).
  
## <a name="configure-an-external-table"></a>Konfigurieren Sie eine externe Tabelle

Um die Daten in Ihrem Azure-Blob-Speicher abzufragen, müssen Sie eine externe Tabelle in Transact-SQL-Abfragen mit definieren. Die folgenden Schritte beschreiben, wie Sie die externe Tabelle zu konfigurieren.

1. Erstellen eines Hauptschlüssels für die Datenbank an. Es ist erforderlich, um die Anmeldeinformationen zu verschlüsseln.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

1. Erstellen Sie datenbankweit gültige Anmeldeinformationen für Azure Blob Storage.

   ```sql
   -- IDENTITY: any string (this is not used for authentication to Azure storage).  
   -- SECRET: your Azure storage account key.  
   CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
   WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';
   ```

1. Erstellen eine externen Datenquelle mit [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md)...

   ```sql
   -- LOCATION:  Azure account storage account name and blob container name.  
   -- CREDENTIAL: The database scoped credential created above.  
   CREATE EXTERNAL DATA SOURCE AzureStorage with (  
         TYPE = HADOOP,
         LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
         CREDENTIAL = AzureStorageCredential  
   );  
   ```

1. Erstellen Sie ein externes Dateiformat mit [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md).

   ```sql
   -- FORMAT TYPE: Type of format in Azure Blob storage (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   -- In this example, the files are pipe (|) delimited
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

1. Erstellen einer externen Tabelle, die auf Daten in Azure Storage mit [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md). In diesem Beispiel enthält die externen Daten Auto Sensordaten.

   ```sql
   -- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
   CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
         [SensorKey] int NOT NULL,
         [CustomerKey] int NOT NULL,
         [GeographyKey] int NULL,
         [Speed] float NOT NULL,
         [YearMeasured] int NOT NULL  
   )  
   WITH (LOCATION='/Demo/',
         DATA_SOURCE = AzureStorage,  
         FILE_FORMAT = TextFileFormat  
   );  
   ```

1. Erstellen von Statistiken für eine externe Tabelle.

   ```sql
   CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
   ```

## <a name="polybase-queries"></a>PolyBase-Abfragen

Es gibt drei Funktionen, für die PolyBase geeignet ist:  
  
- Ad-hoc-Abfragen für externe Tabellen.  
- Importieren von Daten.  
- Exportieren von Daten aus.  

Die folgenden Abfragen geben Sie Beispiel mit fiktiven Auto Sensordaten.

### <a name="ad-hoc-queries"></a>Ad-hoc-Abfragen  

Die folgende ad-hoc-Abfrage joins relationalen Daten im Azure-Blob-Speicher. Er wählt die Kunden, die schneller als 35 mph, verknüpfen strukturierte Kundendaten, die in SQL Server gespeichert sind, Auto-Sensordaten in Azure Blob Storage gespeichert.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
```  

### <a name="importing-data"></a>Importieren von Daten  

Die folgende Abfrage importiert externe Daten in APS. In diesem Beispiel importiert die Daten für schnelle Treiber in APS eine tiefergehende Analyse zu tun. Zur Verbesserung der Leistung nutzt es APS-columnstore-Technologie.  

```sql
CREATE TABLE Fast_Customers
WITH
(CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH (CustomerKey))
AS
SELECT DISTINCT
      Insured_Customers.CustomerKey, Insured_Customers.FirstName, Insured_Customers.LastName,   
      Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
from Insured_Customers INNER JOIN   
(  
      SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
```  

### <a name="exporting-data"></a>Exportieren von Daten  

Die folgende Abfrage exportiert Daten aus APS in Azure Blob Storage. Es kann zum Archivieren von relationalen Daten in Azure Blob Storage, während Sie sich noch Lage sein, es abzufragen.

```sql
-- Export data: Move old data to Azure Blob storage while keeping it query-able via an external table.  
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] 
WITH (  
      LOCATION='/archive/customer/2009',  
      DATA_SOURCE = AzureStorage,  
      FILE_FORMAT = TextFileFormat
)  
AS
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  

## <a name="view-polybase-objects-in-ssdt"></a>Anzeigen von PolyBase-Objekten in SSDT  

In SQL Server Data Tools, externe Tabellen in einem separaten Ordner angezeigt werden **externe Tabellen**. Externe Datenquellen und externe Dateiformate befinden sich in Unterordnern unter **Externe Ressourcen**.  
  
![PolyBase-Objekten in SSDT](media/polybase/external-tables-datasource.png)  

## <a name="next-steps"></a>Nächste Schritte

Erkunden Sie weitere Informationen zum verwenden und Überwachen von PolyBase in den folgenden Artikeln:

[Typzuordnung mit PolyBase](../relational-databases/polybase/polybase-type-mapping.md).  

