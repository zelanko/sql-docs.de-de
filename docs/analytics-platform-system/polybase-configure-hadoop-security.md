---
title: Konfigurieren von PolyBase-Hadoop-Sicherheit in Analytics Platform System | Microsoft-Dokumentation
description: Erläutert das Konfigurieren von PolyBase in Parallel Data Warehouse für die Verbindung mit externen Hadoop.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/26/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: df7e0492c73d213efb08c1bfb25a2c87e2550374
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51700288"
---
# <a name="polybase-configuration-and-security-for-hadoop"></a>PolyBase-Konfiguration und -Sicherheit für Hadoop

Dieser Artikel enthält eine Referenz für die verschiedenen Konfigurationseinstellungen, die APS-PolyBase-Konnektivität mit Hadoop in Azure zu beeinflussen. Eine exemplarische Vorgehensweise zu den neuerungen PolyBase finden Sie unter [neuerungen von PolyBase](configure-polybase-connectivity-to-external-data.md).

> [!NOTE]
> Für Zugriffspunkte sind Änderungen an der XML-Dateien auf alle Computerknoten und steuerknoten erforderlich.
> 
> Besondere Sorgfalt beim XML-Dateien im APS zu ändern. Alle fehlenden Tags oder unerwünschte Zeichen können die XML-Datei behindert die Usablilty des Features für ungültig erklärt.
> Hadoop-Konfigurationsdateien befinden sich unter folgendem Pfad:  
> ```  
> C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf 
> ``` 
> Alle Änderungen an den XML-Dateien erfordern einen Neustart des Diensts wirksam sein kann.

## <a id="rpcprotection"></a> Hadoop.RPC.Protection-Einstellung

Eine gängige Methode zum Sichern der Kommunikation in einem Hadoop-Cluster ist das Ändern der Konfiguration „hadoop.rpc.protection“ zu „Datenschutz“ oder „Integrität“. Standardmäßig geht PolyBase davon aus, dass die Konfiguration auf „Authentifizieren“ festgelegt ist. Um diese Standardeinstellung außer Kraft zu setzen, müssen Sie folgende Eigenschaft zur Datei „core-site.xml“ hinzufügen. Das Ändern dieser Konfiguration ermöglicht eine sichere Datenübertragung zwischen Hadoop-Knoten und eine SSL-Verbindung zu SQL Server.

```xml
<!-- RPC Encryption information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG -->
   <property>
     <name>hadoop.rpc.protection</name>
     <value></value>
   </property> 
```

## <a name="example-xml-files-for-cdh-5x-cluster"></a>XML-Beispieldateien für CDH 5.X-Cluster

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

Wenn Sie die beiden Konfigurationseinstellungen in Mapred-site.xml und Yarn-site.xml aufteilen möchten, würden die Dateien folgendermaßen lauten:

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

Beachten Sie, dass die Eigenschaft mapreduce.application.classpath hinzugefügt wurde. In CDH 5.x finden Sie die Konfigurationswerte unter derselben Namenskonvention in Ambari.

```xml
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
<configuration xmlns:xi="https://www.w3.org/2001/XInclude">
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

## <a name="kerberos-configuration"></a>Kerberos-Konfiguration  

Beachten Sie, dass es zur Authentifizierung von PolyBase bei einem gesicherten Kerberos-Cluster erforderlich ist, die Einstellung „hadoop.rpc.protection“ auf „Authentifizieren“ festzulegen. Dadurch bleibt die Datenkommunikation zwischen den Hadoop-Knoten unverschlüsselt. Aktualisieren Sie Datei „core-site.xml“ auf dem PolyBase-Server, um die Einstellung „Datenschutz“ oder „Integrität“ für „hadoop.rpc.protection“ zu verwenden. Weitere Informationen finden Sie im vorherigen Abschnitt ([Herstellen einer Verbindung mit einem Hadoop-Cluster mit der Einstellung „hadoop.rpc.protection“](#rpcprotection)).

Berechnen zur Verbindung mit eines durch Kerberos gesicherte Hadoop-Cluster mithilfe von MIT KDC, dass Sie die folgenden Änderungen erforderlich sind für alle Zugriffspunkte oder steuerknoten:

1. Suchen Sie die Hadoop-Konfiguration-Verzeichnisse im Installationspfad von Zugriffspunkten. In der Regel lautet der Pfad:  

   ```  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf  
   ```  

2. Suchen Sie den hadoopseitigen Konfigurationswert der in dieser Tabelle aufgelisteten Konfigurationsschlüssel. (Suchen Sie die Dateien auf dem Hadoop-Computer im Hadoop-Konfigurationsverzeichnis.)  
   
3. Kopieren Sie die Konfigurationswerte in die Eigenschaft „Value“ in den entsprechenden Dateien auf dem SQL Server-Computer.  
   
   |**#**|**Konfigurationsdatei**|**Konfigurationsschlüssel**|**Aktion**|  
   |------------|----------------|---------------------|----------|   
   |1|core-site.xml|polybase.kerberos.kdchost|Geben Sie den KDC-Hostnamen an. Zum Beispiel: kerberos.ihr-bereich.de.|  
   |2|core-site.xml|polybase.kerberos.realm|Geben Sie den Kerberos-Bereich an. Zum Beispiel: IHR-BEREICH.DE|  
   |3|core-site.xml|hadoop.security.authentication|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: KERBEROS<br></br>**Sicherheitshinweis:** KERBEROS muss in Großbuchstaben geschrieben werden. Bei Kleinschreibung ist die Funktionalität nicht gewährleistet.|   
   |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: hdfs/_HOST@YOUR-REALM.COM|  
   |5|mapred-site.xml|mapreduce.jobhistory.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: mapred/_HOST@YOUR-REALM.COM|  
   |6|mapred-site.xml|mapreduce.jobhistory.address|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Zum Beispiel: 10.193.26.174:10020|  
   |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: yarn/_HOST@YOUR-REALM.COM|  

**"Core-Site.xml"**
```xml
<property>
  <name>polybase.kerberos.realm</name>
  <value></value>
</property>
<property>
  <name>polybase.kerberos.kdchost</name>
  <value></value>
</property>
<property>
    <name>hadoop.security.authentication</name>
    <value>KERBEROS</value>
</property>
```

**"Hdfs-Site.xml"**
```xml
<property>
  <name>dfs.namenode.kerberos.principal</name>
  <value></value> 
</property>
```

**mapred-site.xml**
```xml
<property>
  <name>mapreduce.jobhistory.principal</name>
  <value></value>
</property>
<property>
  <name>mapreduce.jobhistory.address</name>
  <value></value>
</property>
```

**yarn-site.xml**
```xml
<property>
  <name>yarn.resourcemanager.principal</name>
  <value></value>
</property>
```

4. Erstellen Sie ein datenbankweites Anmeldeinformationsobjekt, um die Authentifizierungsinformationen für jeden Hadoop-Benutzer anzugeben. Weitere Informationen finden Sie unter [PolyBase T-SQL-Objekte](../relational-databases/polybase/polybase-t-sql-objects.md).

## <a id="encryptionzone"></a> Verschlüsselungszone Hadoop-setup
Bei Verwendung von Hadoop Verschlüsselungszone "Core-Site.xml" und "Hdfs-Site.xml" wie folgt zu ändern. Geben Sie die IP-Adresse, die dem KMS-Dienst, mit der entsprechenden Portnummer ausgeführt wird ein. Der Standardport für KMS für CDH ist 16000.

**"Core-Site.xml"**
```xml
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value> 
</property>
```

**"Hdfs-Site.xml"**
```xml
<property>
  <name>dfs.encryption.key.provider.uri</name>
  <value>kms://http@<ip address>:16000/kms</value>
</property>
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value>
  </property>
```