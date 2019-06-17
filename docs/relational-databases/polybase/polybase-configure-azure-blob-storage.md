---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten in Azure Blob Storage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= sql-server-2016 || =sqlallproducts-allversions'
ms.openlocfilehash: 0dfb43a96801fcac3d40e445601d68aab674917e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "64774543"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in Azure Blob Storage

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie PolyBase in einer SQL Server-Instanz verwenden, um externe Daten in Hadoop abzufragen.

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md). Die Voraussetzungen für die Installation werden im entsprechenden Artikel erläutert.

### <a name="configure-azure-blob-storage-connectivity"></a>Konfigurieren der Azure Blob Storage-Konnektivität

Konfigurieren Sie zunächst SQL Server PolyBase für die Verwendung von Azure Blob Storage.

1. Führen Sie [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) aus, wobei „hadoop connectivity“ auf einen Azure Blob Storage-Anbieter festgelegt ist. Informationen zum Ermitteln des Werts für Anbieter finden Sie unter [Konfiguration der PolyBase-Konnektivität](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md). Standardmäßig ist die Hadoop-Konnektivität auf 7 festgelegt.

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Sie müssen SQL Server mithilfe von **services.msc** neu starten. Durch den Neustart von SQL Server werden folgende Dienste neu gestartet:  

   - SQL Server PolyBase-Datenverschiebungsdienst  
   - SQL Server PolyBase-Engine  
  
   ![Beenden und starten Sie PolyBase-Dienste in services.msc](../../relational-databases/polybase/media/polybase-stop-start.png "stop and start PolyBase services in services.msc")  
  
## <a name="configure-an-external-table"></a>Konfigurieren einer externen Tabelle

Um die Daten in Ihrer Hadoop-Datenquelle abzufragen, müssen Sie eine externe Tabelle definieren, die in Transact-SQL-Abfragen verwendet werden soll. Die folgenden Schritte beschreiben, wie Sie die externe Tabelle konfigurieren.

1. Erstellen Sie einen Hauptschlüssel in der Datenbank. Dies ist erforderlich, um das Geheimnis für die Anmeldeinformationen zu verschlüsseln.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

1. Erstellen Sie datenbankweite Anmeldeinformationen für Azure Blob Storage.

   ```sql
   -- IDENTITY: any string (this is not used for authentication to Azure storage).  
   -- SECRET: your Azure storage account key.  
   CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
   WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';
   ```

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle.

   ```sql
   -- LOCATION:  Azure account storage account name and blob container name.  
   -- CREDENTIAL: The database scoped credential created above.  
   CREATE EXTERNAL DATA SOURCE AzureStorage with (  
         TYPE = HADOOP,
         LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
         CREDENTIAL = AzureStorageCredential  
   );  
   ```

1. Erstellen Sie mit [CREATE EXTERNAL FILE FORMAT](../../t-sql/statements/create-external-file-format-transact-sql.md) ein externes Dateiformat.

   ```sql
   -- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE))  
   ```

1. Erstellen Sie mit [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) eine externe Tabelle, die auf in Azure Storage gespeicherte Daten verweist. In diesem Beispiel handelt es sich bei den externen Daten um Kfz-Sensordaten.

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
  
- Ad-hoc-Abfragen von externen Tabellen  
- Importieren von Daten  
- Exportieren von Daten  

Die folgenden Abfragen stellen fiktive Kfz-Sensordaten für das Beispiel bereit.

### <a name="ad-hoc-queries"></a>Ad-hoc-Abfragen  

Die folgende Ad-hoc-Abfrage verknüpft relationale Daten mit Hadoop-Daten. Sie wählt Kunden aus, die schneller als 35 Meilen pro Stunde fahren, und verknüpft in SQL Server gespeicherte strukturierte Daten mit in Hadoop gespeicherten Daten aus Kfz-Sensoren.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
OPTION (FORCE EXTERNALPUSHDOWN);   -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
```  

### <a name="importing-data"></a>Importieren von Daten  

Die folgende Abfrage importiert externe Daten in SQL Server. Dieses Beispiel importiert Daten zu schnellen Fahrern in SQL Server zur genaueren Analyse. Zur Verbesserung der Leistung wird die Columnstore-Technologie verwendet.  

```sql
SELECT DISTINCT
      Insured_Customers.FirstName, Insured_Customers.LastName,   
      Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
INTO Fast_Customers from Insured_Customers INNER JOIN   
(  
      SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
ORDER BY YearlyIncome  
  
CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
```  

### <a name="exporting-data"></a>Exportieren von Daten  

Die folgende Abfrage exportiert Daten aus SQL Server nach Azure Blob Storage. Zu diesem Zweck müssen Sie zuerst den PolyBase-Export aktivieren. Erstellen Sie dann eine externe Tabelle für das Ziel, bevor Sie mit dem Datenexport beginnen.

```sql
-- Enable INSERT into external table  
sp_configure 'allow polybase export', 1;  
reconfigure  
  
-- Create an external table.
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
      [FirstName] char(25) NOT NULL,
      [LastName] char(25) NOT NULL,
      [YearlyIncome] float NULL,
      [MaritalStatus] char(1) NOT NULL  
)  
WITH (  
      LOCATION='/old_data/2009/customerdata',  
      DATA_SOURCE = HadoopHDP2,  
      FILE_FORMAT = TextFileFormat,  
      REJECT_TYPE = VALUE,  
      REJECT_VALUE = 0  
);  

-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
INSERT INTO dbo.FastCustomer2009  
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  

## <a name="view-polybase-objects-in-ssms"></a>Anzeigen von PolyBase-Objekten in SSMS  

In SSMS werden externe Tabellen in einem separaten Ordner **Externe Tabellen**angezeigt. Externe Datenquellen und externe Dateiformate befinden sich in Unterordnern unter **Externe Ressourcen**.  
  
![PolyBase-Objekte in SSMS](media/polybase-management.png)  

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln finden Sie weitere Möglichkeiten zur Verwendung und Überwachung von PolyBase:

[PolyBase-Erweiterungsgruppen](../../relational-databases/polybase/polybase-scale-out-groups.md)  
[Problembehandlung in PolyBase](polybase-troubleshooting.md)  
