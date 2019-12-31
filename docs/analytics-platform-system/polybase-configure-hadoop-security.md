---
title: Konfigurieren der polybase-Hadoop-Sicherheit
description: Erläutert, wie polybase parallel Data Warehouse zum Herstellen einer Verbindung mit dem externen Hadoop konfiguriert wird.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/26/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: f275c77556e8abe8932e241075b9e24e2ae5db77
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400656"
---
# <a name="polybase-configuration-and-security-for-hadoop"></a>PolyBase-Konfiguration und -Sicherheit für Hadoop

Dieser Artikel enthält eine Referenz für verschiedene Konfigurationseinstellungen, die sich auf die APS-polybase-Konnektivität mit Hadoop auswirken. Eine exemplarische Vorgehensweise für polybase finden Sie unter [Was ist polybase](configure-polybase-connectivity-to-external-data.md)?.

> [!NOTE]
> In APS sind Änderungen an XML-Dateien auf allen Computeknoten und dem Steuerungs Knoten erforderlich.
> 
> Achten Sie besonders auf die Änderung von XML-Dateien in APS. Fehlende Tags oder unerwünschte Zeichen können die XML-Datei für ungültig erklären, wodurch die Verfügbarkeit des Features verhindert wird.
> Hadoop-Konfigurationsdateien befinden sich im folgenden Pfad:  
> ```  
> C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf 
> ``` 
> Alle Änderungen an den XML-Dateien erfordern, dass ein Neustart des Dienstanbieter wirksam ist.

## <a id="rpcprotection"></a>Hadoop. RPC. Protection-Einstellung

Eine gängige Methode zum Sichern der Kommunikation in einem Hadoop-Cluster ist das Ändern der Konfiguration „hadoop.rpc.protection“ zu „Datenschutz“ oder „Integrität“. Standardmäßig geht PolyBase davon aus, dass die Konfiguration auf „Authentifizieren“ festgelegt ist. Um diese Standardeinstellung außer Kraft zu setzen, müssen Sie folgende Eigenschaft zur Datei „core-site.xml“ hinzufügen. Das Ändern dieser Konfiguration ermöglicht eine sichere Datenübertragung zwischen Hadoop-Knoten und eine SSL-Verbindung zu SQL Server.

```xml
<!-- RPC Encryption information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG -->
   <property>
     <name>hadoop.rpc.protection</name>
     <value></value>
   </property> 
```

## <a id="kerberossettings"></a>Kerberos-Konfiguration  

Beachten Sie, dass es zur Authentifizierung von PolyBase bei einem gesicherten Kerberos-Cluster erforderlich ist, die Einstellung „hadoop.rpc.protection“ auf „Authentifizieren“ festzulegen. Dadurch bleibt die Datenkommunikation zwischen den Hadoop-Knoten unverschlüsselt. Aktualisieren Sie Datei „core-site.xml“ auf dem PolyBase-Server, um die Einstellung „Datenschutz“ oder „Integrität“ für „hadoop.rpc.protection“ zu verwenden. Weitere Informationen finden Sie im vorherigen Abschnitt ([Herstellen einer Verbindung mit einem Hadoop-Cluster mit der Einstellung „hadoop.rpc.protection“](#rpcprotection)).

Zum Herstellen einer Verbindung mit einem Kerberos-gesicherten Hadoop-Cluster mit mit KDC sind die folgenden Änderungen auf allen APS-Computeknoten und-Steuerungs Knoten erforderlich:

1. Suchen Sie die Hadoop-Konfigurations Verzeichnisse im Installationspfad von APS. In der Regel lautet der Pfad:  

   ```  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf  
   ```  

2. Suchen Sie den hadoopseitigen Konfigurationswert der in dieser Tabelle aufgelisteten Konfigurationsschlüssel. (Suchen Sie die Dateien auf dem Hadoop-Computer im Hadoop-Konfigurationsverzeichnis.)  
   
3. Kopieren Sie die Konfigurationswerte in die Eigenschaft „Value“ in den entsprechenden Dateien auf dem SQL Server-Computer.  
   
   |**#**|**Konfigurationsdatei**|**Konfigurationsschlüssel**|**Hinspiel**|  
   |------------|----------------|---------------------|----------|   
   |1|core-site.xml|polybase.kerberos.kdchost|Geben Sie den KDC-Hostnamen an. Zum Beispiel: kerberos.ihr-bereich.de.|  
   |2|core-site.xml|polybase.kerberos.realm|Geben Sie den Kerberos-Bereich an. Zum Beispiel: IHR-BEREICH.DE|  
   |3|core-site.xml|hadoop.security.authentication|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: KERBEROS<br></br>**Sicherheitshinweis:** Kerberos muss in Großbuchstaben geschrieben werden. Bei Kleinschreibung ist die Funktionalität nicht gewährleistet.|   
   |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: hdfs/_HOST@YOUR-REALM.COM|  
   |5|mapred-site.xml|mapreduce.jobhistory.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: mapred/_HOST@YOUR-REALM.COM|  
   |6|mapred-site.xml|mapreduce.jobhistory.address|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Zum Beispiel: 10.193.26.174:10020|  
   |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: yarn/_HOST@YOUR-REALM.COM|  

**core-site.xml**
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

**hdfs-site.xml**
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

## <a id="encryptionzone"></a>Einrichten der Hadoop-Verschlüsselungs Zone
Wenn Sie die Hadoop-Verschlüsselungs Zone verwenden, ändern Sie Core-Site. XML und "HDFS-Site. XML wie folgt. Geben Sie die IP-Adresse an, unter der der KMS-Dienst mit der entsprechenden Portnummer ausgeführt wird. Der Standardport für KMS in CDH ist 16000.

**core-site.xml**
```xml
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value> 
</property>
```

**hdfs-site.xml**
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