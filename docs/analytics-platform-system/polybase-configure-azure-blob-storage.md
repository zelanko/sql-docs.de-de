---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten in Azure Blob Storage | Microsoft-Dokumentation
description: Erläutert das Konfigurieren von PolyBase in Parallel Data Warehouse für die Verbindung mit externen Hadoop.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 82c57ef57a01cabf2786c71fc53aed3660289451
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960286"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in Azure Blob storage

Der Artikel erläutert die Verwendung von PolyBase in SQL Server-Instanz zum Abfragen von externen Daten im Azure-Blob-Speicher.

> [!NOTE]
> APS unterstützt derzeit nur standard Allgemein v1 lokal redundanten (LRS) Azure-Blob-Speicher.

## <a name="prerequisites"></a>Vorraussetzungen

 - Azure Blob Storage in Ihrem Abonnement her.
 - Ein Container in Azure Blob Storage erstellt wird.

### <a name="configure-azure-blob-storage-connectivity"></a>Konfigurieren von Azure Blob Storage-Konnektivität

Konfigurieren Sie zuerst installiert wird, um Azure Blob Storage verwenden.

1. Führen Sie [Sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) mit "Hadoop Connectivity" auf ein Azure-Blob-Speicheranbieter festgelegt. Informationen zum Ermitteln des Werts für Anbieter finden Sie unter [Konfiguration der PolyBase-Konnektivität](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

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
  
## <a name="configure-an-external-table"></a>Konfigurieren einer externen Tabelle

Um die Daten in Ihrem Azure-Blob-Speicher abzufragen, müssen Sie eine externe Tabelle in Transact-SQL-Abfragen mit definieren. Die folgenden Schritte beschreiben, wie Sie die externe Tabelle konfigurieren.

1. Erstellen Sie einen Hauptschlüssel in der Datenbank. Es ist erforderlich, um die Anmeldeinformationen zu verschlüsseln.

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

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle.

   ```sql
   -- LOCATION:  Azure account storage account name and blob container name.  
   -- CREDENTIAL: The database scoped credential created above.  
   CREATE EXTERNAL DATA SOURCE AzureStorage with (  
         TYPE = HADOOP,
         LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
         CREDENTIAL = AzureStorageCredential  
   );  
   ```

1. Erstellen Sie mit [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md) ein externes Dateiformat.

   ```sql
   -- FORMAT TYPE: Type of format in Azure Blob storage (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   -- In this example, the files are pipe (|) delimited
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

1. Erstellen Sie mit [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md) eine externe Tabelle, die auf in Azure Storage gespeicherte Daten verweist. In diesem Beispiel handelt es sich bei den externen Daten um Kfz-Sensordaten.

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

1. Erstellen Sie Statistiken für eine externe Tabelle.

   ```sql
   CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
   ```

## <a name="polybase-queries"></a>PolyBase-Abfragen

Es gibt drei Funktionen, für die PolyBase geeignet ist:  
  
- Ad-hoc-Abfragen für externe Tabellen.  
- Importieren von Daten  
- Exportieren von Daten  

Die folgenden Abfragen stellen fiktive Kfz-Sensordaten für das Beispiel bereit.

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

Weitere Informationen zu PolyBase finden Sie unter [Was ist PolyBase?](../relational-databases/polybase/polybase-guide.md). 

