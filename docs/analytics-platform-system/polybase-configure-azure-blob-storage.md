---
title: Verwenden von polybase zum Zugreifen auf externe Daten in Azure BLOB Storage
description: Erläutert, wie polybase parallel Data Warehouse zum Herstellen einer Verbindung mit dem externen Hadoop konfiguriert wird.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4ea61ea7e6983f9601783957eee6776f36eccfb4
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400723"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Konfigurieren von polybase für den Zugriff auf externe Daten in Azure BLOB Storage

In diesem Artikel wird erläutert, wie Sie polybase auf einer SQL Server Instanz verwenden, um externe Daten in Azure BLOB Storage abzufragen.

> [!NOTE]
> APS unterstützt derzeit nur den lokal redundanten Standard-Azure-BLOB-Speicher (LRS).

## <a name="prerequisites"></a>Voraussetzungen

 - Azure BLOB Storage in Ihrem Abonnement.
 - Ein Container, der im Azure-BLOB-Speicher erstellt wird.

### <a name="configure-azure-blob-storage-connectivity"></a>Konfigurieren der Azure BLOB Storage-Konnektivität

Konfigurieren Sie zunächst APS für die Verwendung von Azure BLOB Storage.

1. Führen Sie [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) mit "Hadoop Connectivity" aus, die auf einen Azure BLOB Storage-Anbieter festgelegt ist. Informationen zum Ermitteln des Werts für Anbieter finden Sie unter [Konfiguration der PolyBase-Konnektivität](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure Blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Neustart der APS-Region mithilfe der Dienst Status Seite auf [Appliance-Configuration Manager](launch-the-configuration-manager.md).
  
## <a name="configure-an-external-table"></a>Konfigurieren einer externen Tabelle

Zum Abfragen der Daten in Azure BLOB Storage müssen Sie eine externe Tabelle definieren, die in Transact-SQL-Abfragen verwendet werden soll. Die folgenden Schritte beschreiben, wie Sie die externe Tabelle konfigurieren.

1. Erstellen Sie einen Hauptschlüssel in der Datenbank. Es ist erforderlich, um den geheimen Schlüssel für die Anmelde Informationen zu verschlüsseln.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

1. Erstellen Sie Daten Bank weit gültige Anmelde Informationen für Azure BLOB Storage.

   ```sql
   -- IDENTITY: any string (this is not used for authentication to Azure storage).  
   -- SECRET: your Azure storage account key.  
   CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
   WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';
   ```

1. Erstellen Sie eine externe Datenquelle mit der [externen Datenquelle erstellen](../t-sql/statements/create-external-data-source-transact-sql.md).

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

Die folgende Ad-hoc-Abfrage verbindet relationale mit Daten in Azure BLOB Storage. Es wählt Kunden aus, die schneller als 35 mph sind, und verbindet strukturierte Kundendaten, die in SQL Server mit Fahrzeug Sensordaten in Azure BLOB Storage gespeichert sind.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
```  

### <a name="importing-data"></a>Importieren von Daten  

Mit der folgenden Abfrage werden externe Daten in APS importiert. In diesem Beispiel werden Daten für schnelle Treiber in APS importiert, um ausführlichere Analysen durchzuführen. Um die Leistung zu verbessern, nutzt sie columnstore-Technologie in APS.  

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

Mit der folgenden Abfrage werden Daten aus APS in Azure BLOB Storage exportiert. Sie kann verwendet werden, um relationale Daten in Azure BLOB Storage zu archivieren und Sie trotzdem abzufragen.

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

## <a name="view-polybase-objects-in-ssdt"></a>Anzeigen von polybase-Objekten in SSDT  

In SQL Server Data Tools werden externe Tabellen in einem separaten Ordner **externe Tabellen**angezeigt. Externe Datenquellen und externe Dateiformate befinden sich in Unterordnern unter **Externe Ressourcen**.  
  
![Polybase-Objekte in SSDT](media/polybase/external-tables-datasource.png)  

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie unter [Was ist PolyBase?](../relational-databases/polybase/polybase-guide.md). 

