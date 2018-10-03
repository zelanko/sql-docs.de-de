---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten in Hadoop | Microsoft-Dokumentation
description: Erläutert das Konfigurieren von PolyBase in Parallel Data Warehouse für die Verbindung mit externen Hadoop.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d87ba02342948d140afb68c2d9d13a2aef9464eb
ms.sourcegitcommit: 5afec8b4b73ce1727e4e5cf875d1e1ce9df50eab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47450352"
---
# <a name="configure-polybase-to-access-external-data-in-hadoop"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in Hadoop

Der Artikel wird erläutert, wie Sie PolyBase auf einer APS-Appliance zum Abfragen von externen Daten in Hadoop verwenden.

## <a name="prerequisites"></a>Erforderliche Komponenten

PolyBase unterstützt zwei Hadoop-Anbieter: Hortonworks Data Platform (HDP) und Cloudera Distributed Hadoop (CDH). Hadoop folgt das Muster "Hauptversion.Nebenversion" neuen Releases, und alle Versionen in einer unterstützten Version von Haupt- und Nebenversionen werden unterstützt. Die folgenden Hadoop-Anbieter werden unterstützt:
 - Hortonworks HDP 1.3 auf Linux/Windows Server  
 - Hortonworks HDP 2.1 – 2.6 unter Linux
 - Hortonworks HDP 2.1 – 2.3 unter Windows Server  
 - Cloudera CDH 4.3 unter Linux  
 - Cloudera CDH 5.1 bis 5.5, 5.9 bis 5.13 unter Linux

### <a name="configure-hadoop-connectivity"></a>Hadoop-Konnektivität konfigurieren

Konfigurieren Sie zuerst installiert wird, um Ihre spezifischen Hadoop-Anbieter verwenden.

1. Führen Sie [Sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) mit "Hadoop Connectivity" und einen entsprechenden Wert für den Anbieter. Der Wert für Ihren Anbieter finden Sie unter [Konfiguration der PolyBase-Netzwerkkonnektivität](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md). 

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. APS-Region, die mithilfe von dienststatusseite auf Neustart [Appliance-Konfigurations-Manager](launch-the-configuration-manager.md).
  
## <a id="pushdown"></a> Aktivieren Sie die Pushdown-Berechnung  

Um die abfrageleistung zu verbessern, aktivieren Sie die Pushdown-Berechnung für Ihren Hadoop-Cluster:  
  
1. Öffnen Sie eine Remotedesktopverbindung mit PDW-Control-Knoten.

2. Suchen Sie die Datei **"Yarn-Site.xml"** auf dem steuerknoten. In der Regel lautet der Pfad:  

   ```xml  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\  
   ```  

3. Suchen Sie auf dem Hadoop-Computer die analoge Datei im Hadoop-Konfigurationsverzeichnis. Suchen Sie in der Datei den Wert des Konfigurationsschlüssels „yarn.application.classpath.“, und kopieren Sie diesen.  
  
4. Auf dem steuerknoten in der **Datei "yarn.site.xml"** finden Sie die **yarn.application.classpath** Eigenschaft. Fügen Sie den Wert vom Hadoop-Computer in das Element „Value“ ein.  
  
5. Für alle CDH 5.X-Versionen müssen Sie die Konfigurationsparameter „mapreduce.application.classpath“ entweder ans Ende der Datei „yarn.site.xml“ oder in die Datei „mapred-site.xml“ einfügen. HortonWorks enthält diese Konfigurationen in den yarn.application.classpath-Konfigurationen. Weitere Beispiele finden Sie unter [PolyBase-Konfiguration](../relational-databases/polybase/polybase-configuration.md).

## <a name="configure-an-external-table"></a>Konfigurieren Sie eine externe Tabelle

Um die Daten in der Hadoop-Datenquelle abzufragen, müssen Sie eine externe Tabelle in Transact-SQL-Abfragen mit definieren. Die folgenden Schritte beschreiben, wie Sie die externe Tabelle zu konfigurieren.

1. Erstellen eines Hauptschlüssels für die Datenbank an. Es ist erforderlich, um die Anmeldeinformationen zu verschlüsseln.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

2. Erstellen Sie datenbankweit gültige Anmeldeinformationen für die Kerberos-gesicherte Hadoop-Cluster.

   ```sql
   -- IDENTITY: the Kerberos user name.  
   -- SECRET: the Kerberos password  
   CREATE DATABASE SCOPED CREDENTIAL HadoopUser1
   WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
   ```

3. Erstellen eine externen Datenquelle mit [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md).

   ```sql
   -- LOCATION (Required) : Hadoop Name Node IP address and port.  
   -- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
   -- CREDENTIAL (Optional):  the database scoped credential, created above.  
   CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
         TYPE = HADOOP,
         LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',
         RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',
         CREDENTIAL = HadoopUser1
   );  
   ```

4. Erstellen Sie ein externes Dateiformat mit [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md).

   ```sql
   -- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

5. Erstellen einer externen Tabelle, die auf Daten in Hadoop mit [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md). In diesem Beispiel enthält die externen Daten Auto Sensordaten.

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
         DATA_SOURCE = MyHadoopCluster,  
         FILE_FORMAT = TextFileFormat  
   );  
   ```

6. Erstellen von Statistiken für eine externe Tabelle.

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

Die folgende ad-hoc-Abfrage verknüpft relationalen mit Hadoop-Daten. Kunden, die schneller als 35 mph, verknüpfte strukturierte Kundendaten, die im APS mit Auto-Sensor-Daten in Hadoop gespeichert Laufwerk ausgewählt.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
OPTION (FORCE EXTERNALPUSHDOWN);   -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
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

Die folgende Abfrage exportiert Daten aus APS mit Hadoop in Azure. Dienen zum Archivieren von relationaler Daten mit Hadoop Zeit immer noch in der Lage, es abzufragen.

```sql
-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] 
WITH (  
      LOCATION='/archive/customer/2009',  
      DATA_SOURCE = HadoopHDP2,  
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

Erkunden Sie weitere Informationen zum Konfigurieren von PolyBase in den folgenden Artikeln:

[PolyBase-Konfiguration und Sicherheit für Hadoop ](../relational-databases/polybase/polybase-configuration.md).  
 
