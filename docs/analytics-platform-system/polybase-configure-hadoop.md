---
title: 'Zugreifen auf externe Daten: Hadoop – PolyBase'
description: Erläutert, wie polybase parallel Data Warehouse zum Herstellen einer Verbindung mit dem externen Hadoop konfiguriert wird.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 12/13/2019
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019, seo-lt-2019
ms.openlocfilehash: dc796ff58c5320e60011dc46dd45468177a98ed8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75245393"
---
# <a name="configure-polybase-to-access-external-data-in-hadoop"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in Hadoop

Der Artikel erläutert die Verwendung von polybase auf einem APS-Gerät zum Abfragen externer Daten in Hadoop.

## <a name="prerequisites"></a>Voraussetzungen

PolyBase unterstützt zwei Hadoop-Anbieter: Hortonworks Data Platform (HDP) und Cloudera Distributed Hadoop (CDH). Hadoop folgt dem Muster „Hauptversion.Nebenversion“ für neue Releases, und alle Versionen, die zu einer unterstützten Haupt- und Nebenversion gehören, werden unterstützt. Folgende Hadoop-Anbieter werden unterstützt:
 - Hortonworks HDP 1.3 auf Linux/Windows Server  
 - Hortonworks HDP 2,1-2,6 unter Linux
 - Hortonworks HDP 3,0-3,1 unter Linux
 - Hortonworks HDP 2.1 – 2.3 unter Windows Server  
 - Cloudera CDH 4.3 unter Linux  
 - Cloudera CDH 5,1-5,5, 5,9-5,13, 5,15 & 5,16 unter Linux

### <a name="configure-hadoop-connectivity"></a>Konfigurieren der Hadoop-Konnektivität

Konfigurieren Sie zunächst APS für die Verwendung Ihres bestimmten Hadoop-Anbieters.

1. Führen Sie [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) mit „hadoop connectivity“ aus, und legen Sie einen geeigneten Wert für Ihren Anbieter fest. Informationen zum Ermitteln des Werts für Ihren Anbieter finden Sie unter [Konfiguration der PolyBase-Konnektivität](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md). 

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 and 3.0 - 3.1 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Neustart der APS-Region mithilfe der Dienst Status Seite auf [Appliance-Configuration Manager](launch-the-configuration-manager.md).
  
## <a name="enable-pushdown-computation"></a><a id="pushdown"></a> Aktivieren der Weitergabeberechnung  

Um die Abfrageleistung zu verbessern, aktivieren Sie die Weitergabeberechnung für Ihren Hadoop-Cluster:  
  
1. Öffnen Sie eine Remote Desktop Verbindung mit dem PDW-Steuerungs Knoten.

2. Suchen Sie die Datei **Yarn-Site. XML** auf dem Steuerelement Knoten. In der Regel lautet der Pfad:  

   ```xml  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\  
   ```  

3. Suchen Sie auf dem Hadoop-Computer die analoge Datei im Hadoop-Konfigurationsverzeichnis. Suchen Sie in der Datei den Wert des Konfigurationsschlüssels „yarn.application.classpath.“, und kopieren Sie diesen.  
  
4. Suchen Sie auf dem Knoten "Steuerelement" in der **Datei "Yarn. Site. XML** " die Eigenschaft **Yarn. Application. classpath** . Fügen Sie den Wert vom Hadoop-Computer in das Element „Value“ ein.  
  
5. Für alle CDH 5.X-Versionen müssen Sie die Konfigurationsparameter „mapreduce.application.classpath“ entweder ans Ende der Datei „yarn.site.xml“ oder in die Datei „mapred-site.xml“ einfügen. HortonWorks enthält diese Konfigurationen in den yarn.application.classpath-Konfigurationen. Weitere Beispiele finden Sie unter [PolyBase-Konfiguration](../relational-databases/polybase/polybase-configuration.md).

## <a name="example-xml-files-for-cdh-5x-cluster-default-values"></a>Beispiel-XML-Dateien für CDH 5. X-Cluster Standardwerte

„Yarn-site.xml“ mit der Konfiguration „yarn.application.classpath“ und „mapreduce.application.classpath“

```xml
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
   <property>
      <name>yarn.resourcemanager.connect.max-wait.ms</name>
      <value>40000</value>
   </property>
   <property>
      <name>yarn.resourcemanager.connect.retry-interval.ms</name>
      <value>30000</value>
   </property>
<!-- Applications' Configuration-->
   <property>
     <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
      <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
      <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
      <name>yarn.application.classpath</name>
      <value>$HADOOP_CLIENT_CONF_DIR,$HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/*,$HADOOP_COMMON_HOME/lib/*,$HADOOP_HDFS_HOME/*,$HADOOP_HDFS_HOME/lib/*,$HADOOP_YARN_HOME/*,$HADOOP_YARN_HOME/lib/,$HADOOP_MAPRED_HOME/*,$HADOOP_MAPRED_HOME/lib/*,$MR2_CLASSPATH*</value>
   </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
   <property>
      <name>yarn.resourcemanager.principal</name>
      <value></value>
   </property>
-->
</configuration>
```

Wenn Sie die beiden Konfigurationseinstellungen in "" mapred-Site. xml "und" Yarn-Site. xml "unterbrechen, lauten die Dateien wie folgt:

**yarn-site.xml**

```xml
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
   <property>
      <name>yarn.resourcemanager.connect.max-wait.ms</name>
      <value>40000</value>
   </property>
   <property>
      <name>yarn.resourcemanager.connect.retry-interval.ms</name>
      <value>30000</value>
   </property>
<!-- Applications' Configuration-->
   <property>
     <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
      <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
      <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
      <name>yarn.application.classpath</name>
      <value>$HADOOP_CLIENT_CONF_DIR,$HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/*,$HADOOP_COMMON_HOME/lib/*,$HADOOP_HDFS_HOME/*,$HADOOP_HDFS_HOME/lib/*,$HADOOP_YARN_HOME/*,$HADOOP_YARN_HOME/lib/*</value>
   </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
   <property>
      <name>yarn.resourcemanager.principal</name>
      <value></value>
   </property>
-->
</configuration>
```

**mapred-site.xml**

Beachten Sie, dass die Eigenschaft mapreduce.application.classpath hinzugefügt wurde. In CDH 5. x finden Sie die Konfigurationswerte in der gleichen Benennungs Konvention in ambari.

```xml
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
<configuration xmlns:xi="http://www.w3.org/2001/XInclude">
   <property>
     <name>mapred.min.split.size</name>
       <value>1073741824</value>
   </property>
   <property>
     <name>mapreduce.app-submission.cross-platform</name>
     <value>true</value>
   </property>
<property>
     <name>mapreduce.application.classpath</name>
     <value>$HADOOP_MAPRED_HOME/*,$HADOOP_MAPRED_HOME/lib/*,$MR2_CLASSPATH</value>
   </property>


<!--kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
   <property>
     <name>mapreduce.jobhistory.principal</name>
     <value></value>
   </property>
   <property>
     <name>mapreduce.jobhistory.address</name>
     <value></value>
   </property>
-->
</configuration>
```

## <a name="example-xml-files-for-hdp-3x-cluster-default-values"></a>Beispiel-XML-Dateien für die Standardwerte des HDP 3. X-Clusters

**yarn-site.xml**

```xml
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
  <property>
     <name>yarn.resourcemanager.connect.max-wait.ms</name>
     <value>40000</value>
  </property>
  <property>
     <name>yarn.resourcemanager.connect.retry-interval.ms</name>
     <value>30000</value>
  </property>
<!-- Applications' Configuration-->
  <property>
    <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
     <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
     <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
     <name>yarn.application.classpath</name>
     <value>$HADOOP_CONF_DIR,/usr/hdp/3.1.0.0-78/hadoop/*,/usr/hdp/3.1.0.0-78/hadoop/lib/*,/usr/hdp/current/hadoop-hdfs-client/*,/usr/hdp/current/hadoop-hdfs-client/lib/*,/usr/hdp/current/hadoop-yarn-client/*,/usr/hdp/current/hadoop-yarn-client/lib/*,/usr/hdp/3.1.0.0-78/hadoop-mapreduce/*,/usr/hdp/3.1.0.0-78/hadoop-yarn/*,/usr/hdp/3.1.0.0-78/hadoop-yarn/lib/*,/usr/hdp/3.1.0.0-78/hadoop-mapreduce/lib/*,/usr/hdp/share/hadoop/common/*,/usr/hdp/share/hadoop/common/lib/*,/usr/hdp/share/hadoop/tools/lib/*</value>
  </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
  <property>
     <name>yarn.resourcemanager.principal</name>
     <value></value>
  </property>
-->
</configuration>
```

## <a name="configure-an-external-table"></a>Konfigurieren einer externen Tabelle

Um die Daten in Ihrer Hadoop-Datenquelle abzufragen, müssen Sie eine externe Tabelle definieren, die in Transact-SQL-Abfragen verwendet werden soll. Die folgenden Schritte beschreiben, wie Sie die externe Tabelle konfigurieren.

1. Erstellen Sie einen Hauptschlüssel in der Datenbank. Es ist erforderlich, um den geheimen Schlüssel für die Anmelde Informationen zu verschlüsseln.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

2. Erstellen Sie datenbankweite Anmeldeinformationen für Hadoop-Cluster, die mit Kerberos gesichert sind.

   ```sql
   -- IDENTITY: the Kerberos user name.  
   -- SECRET: the Kerberos password  
   CREATE DATABASE SCOPED CREDENTIAL HadoopUser1
   WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
   ```

3. Erstellen Sie eine externe Datenquelle mit der [externen Datenquelle erstellen](../t-sql/statements/create-external-data-source-transact-sql.md).

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

4. Erstellen Sie mit [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md) ein externes Dateiformat.

   ```sql
   -- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

5. Erstellen Sie mit [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md) eine externe Tabelle, die auf in Hadoop gespeicherte Daten verweist. In diesem Beispiel handelt es sich bei den externen Daten um Kfz-Sensordaten.

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

6. Erstellen Sie Statistiken für eine externe Tabelle.

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

Die folgende Ad-hoc-Abfrage wird relationalen mit Hadoop-Daten verbunden. Es wählt Kunden aus, die schneller als 35 mph sind, und verbindet strukturierte Kundendaten, die in APS gespeichert sind, mit Fahrzeug Sensordaten, die in Hadoop gespeichert sind  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
OPTION (FORCE EXTERNALPUSHDOWN);   -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
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

Die folgende Abfrage exportiert Daten von APS nach Hadoop. Sie kann verwendet werden, um relationale Daten in Hadoop zu archivieren und Sie trotzdem abzufragen.

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

## <a name="view-polybase-objects-in-ssdt"></a>Anzeigen von polybase-Objekten in SSDT  

In SQL Server Data Tools werden externe Tabellen in einem separaten Ordner **externe Tabellen**angezeigt. Externe Datenquellen und externe Dateiformate befinden sich in Unterordnern unter **Externe Ressourcen**.  
  
![Polybase-Objekte in SSDT](media/polybase/external-tables-datasource.png)  

## <a name="next-steps"></a>Nächste Schritte

Informationen zu Hadoop-Sicherheitseinstellungen finden Sie unter [Konfigurieren der Hadoop-Sicherheit](polybase-configure-hadoop-security.md).<br>
Weitere Informationen zu PolyBase finden Sie unter [Was ist PolyBase?](../relational-databases/polybase/polybase-guide.md). 
 
