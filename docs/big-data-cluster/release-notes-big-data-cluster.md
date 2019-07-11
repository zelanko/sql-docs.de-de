---
title: Versionshinweise
titleSuffix: SQL Server big data clusters
description: Dieser Artikel beschreibt die neuesten Updates und bekannte Probleme bei der SQL Server-2019 big Data-Clustern (Vorschau).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2937734ad4543d9dc59e777ceaddfc597da148d2
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794090"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>Anmerkungen zu dieser Version für big Data-Cluster in SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel führt die Updates und bekannte Probleme für die neuesten Versionen von SQL Server-big Data-Cluster.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp31"></a> CTP 3.1 (Juni)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in SQL Server 2019 CTP 3.1.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Änderungen am Befehl `mssqlctl` | Die `mssqlctl cluster`-Befehle wurden in `mssqlctl bdc` umbenannt. Weitere Informationen finden Sie in der [Referenz zu `mssqlctl`](reference-mssqlctl.md). |
| Neue `mssqlctl` statusbefehlen und Entfernen von das Cluster-Verwaltungsportal. | Das Verwaltungsportal für den Cluster wird in dieser Version entfernt. Neue Befehle hinzugefügt wurden `mssqlctl` , dass Ergänzung für vorhandene Überwachungsbefehle. |
| Spark-Computepools | Erstellen Sie zusätzliche Knoten, um die Spark-Rechenleistung zu erhöhen, ohne den Speicher zentral hochskalieren zu müssen. Zudem können Sie Speicherpoolknoten starten, die nicht für Spark verwendet werden. Spark wird vom Speicher entkoppelt. Weitere Informationen finden Sie unter [Configure storage without spark (Konfigurieren des Speichers ohne Spark)](deployment-custom-configuration.md#sparkstorage). |
| MSSQL-Spark-Connector | Ab jetzt werden Lese- und Schreibvorgänge in externen Datenpooltabellen unterstützt. In vorherigen Releases wurden Lese- und Schreibvorgänge nur für Tabellen der MASTER-Instanz unterstützt. Weitere Informationen finden Sie unter [How to read and write to SQL Server from Spark using the MSSQL Spark Connector (Lesen und Schreiben in SQL Server über Spark mithilfe des MSSQL-Spark-Connectors)](spark-mssql-connector.md). |
| Machine Learning mit MLeap | [Trainieren Sie ein MLeap-Machine-Learning-Modell in Spark, und bewerten Sie es mit der Java-Spracherweiterung in SQL Server.](spark-create-machine-learning-model.md) |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen im Zusammenhang mit dieser Version beschrieben.

#### <a name="hdfs"></a>HDFS

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

#### <a name="deployment"></a>Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Müssen Sie Ihre Daten sichern und löschen Sie Ihre vorhandenen big Data-Cluster (mit der früheren Version von **Mssqlctl**) vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="external-tables"></a>Externe Tabellen

- Bereitstellung von Big Data-Cluster werden nicht mehr erstellt die **SqlDataPool** und **SqlStoragePool** Daten aus externen Quellen. Sie können diese Datenquellen manuell, um Daten bei den Daten-Pools und den Speicherpool Virtualisierungsunterstützung erstellen.

   > [!NOTE]
   > Der URI für diese externen Datenquellen zu erstellen, unterscheidet sich zwischen CTPs. Informieren Sie sich die zu deren Erstellung finden Sie unter folgenden Transact-SQL-Befehle 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Bei der Erstellung einer externen Tabelle, Oracle, die Zeichen-Datentypen zu verwenden, interpretiert der Studio für Azure Data Virtualization-Assistent diese Spalten als VARCHAR in der Definition der externen Tabelle an. Dies bewirkt einen Fehler in der DDL für externe Tabellen. Ändern Sie entweder das Oracle-Schema, um verwenden Sie den Typ NVARCHAR2 oder EXTERNAL TABLE-Anweisungen manuell erstellen, und geben NVARCHAR, statt mit dem Assistenten.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Bei eine Anwendung von R, Python oder MLeap von RESTful-API aufrufen, tritt ein Timeout für der Aufruf innerhalb von 5 Minuten.

#### <a name="spark-and-notebooks"></a>Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

#### <a name="kibana-logs-dashboards"></a>Kibana-Dashboards Protokolle

- Zwischen Aris CTP 3.0 und 3.1 wurde die Kibana-Version von 6.3.1 auf 7.0.1 aktualisiert.  Dies hat den Edge-Browser nicht kompatibel mit Kibana vorgenommen. Benutzern werden eine leere Seite angezeigt, beim Laden der aktuellen Version von der Kibana-Dashboards in Microsoft Edge. Finden Sie unter [hier]( https://www.elastic.co/support/matrix#matrix_browse) für die unterstützten Browser Kibana.rs 


## <a id="ctp30"></a> CTP-Version 3.0 (Mai)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in SQL Server 2019 CTP-Version 3.0.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| **mssqlctl**-Updates | Mehrere [Updates für den Befehl **mssqlctl** und seine Parameter](../big-data-cluster/reference-mssqlctl.md). Dies umfasst ein Update für den Befehl **mssqlctl login**, der nun den Controllerbenutzernamen und -endpunkt zum Ziel hat. |
| Speichererweiterungen | Unterstützung für verschiedene Speicherkonfigurationen für Protokolle und Daten. Darüber hinaus wurde die Anzahl der Ansprüche von persistentem Volume für einen Big Data-Cluster gesenkt. |
| Mehrere Computepoolinstanzen | Unterstützung für mehrere Computepoolinstanzen. |
| Neues Poolverhalten und neue Poolfunktionen | Der Computepool wird jetzt standardmäßig für Speicherpool- und Datenpoolvorgänge ausschließlich in einer **ROUND_ROBIN**-Verteilung verwendet. Der Datenpool können Sie jetzt ein neues **REPLIZIERTE** Verteilungstyp, was bedeutet, dass die gleichen Daten für alle Instanzen der Daten-Pool vorhanden ist. |
| Verbesserungen externer Tabellen | Externe Tabellen des HADOOP-Datenquellentyps unterstützen nun das Lesen von Zeilen mit einer Größe von bis zu 1 MB. Externe Tabellen (ODBC, Speicherpool, Datenpool) unterstützen jetzt Zeilen mit der Breite einer SQL Server-Tabelle. |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen im Zusammenhang mit dieser Version beschrieben.

#### <a name="hdfs"></a>HDFS

- Azure Data Studio gibt einen Fehler zurück, wenn Sie versuchen, einen neuen Ordner in HDFS zu erstellen. Um diese Funktionalität zu aktivieren, installieren Sie den Insider-Build von Azure Data Studio:
  
   - [Installationsprogramm für Windows-Benutzer - **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-user/insider)
   - [Installer für Windows-System - **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64/insider)
   - [Windows-ZIP - **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-archive/insider)
   - [MacOS-ZIP - **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/darwin/insider)
   - [Linux TAR. GZ - **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/linux-x64/insider)

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

#### <a name="deployment"></a>Bereitstellung

- Die vorherigen Bereitstellungsverfahren für GPU-fähige big Data-Cluster werden in CTP 3.0 nicht unterstützt. Eine alternative Bereitstellungsverfahren wird untersucht. Jetzt wurde im Artikel "Bereitstellen einer big Data-cluster mit GPU-Unterstützung und TensorFlow ausführen" vorübergehend aufgehoben wurde, um Verwirrung zu vermeiden.

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Müssen Sie Ihre Daten sichern und löschen Sie Ihre vorhandenen big Data-Cluster (mit der früheren Version von **Mssqlctl**) vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="external-tables"></a>Externe Tabellen

- Bereitstellung von Big Data-Cluster werden nicht mehr erstellt die **SqlDataPool** und **SqlStoragePool** Daten aus externen Quellen. Sie können diese Datenquellen manuell, um Daten bei den Daten-Pools und den Speicherpool Virtualisierungsunterstützung erstellen.

   > [!NOTE]
   > Der URI für diese externen Datenquellen zu erstellen, unterscheidet sich zwischen CTPs. Informieren Sie sich die zu deren Erstellung finden Sie unter folgenden Transact-SQL-Befehle 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Bei der Erstellung einer externen Tabelle, Oracle, die Zeichen-Datentypen zu verwenden, interpretiert der Studio für Azure Data Virtualization-Assistent diese Spalten als VARCHAR in der Definition der externen Tabelle an. Dies bewirkt einen Fehler in der DDL für externe Tabellen. Ändern Sie entweder das Oracle-Schema, um verwenden Sie den Typ NVARCHAR2 oder EXTERNAL TABLE-Anweisungen manuell erstellen, und geben NVARCHAR, statt mit dem Assistenten.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Bei eine Anwendung von R, Python oder MLeap von RESTful-API aufrufen, tritt ein Timeout für der Aufruf innerhalb von 5 Minuten.

#### <a name="spark-and-notebooks"></a>Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

## <a id="ctp25"></a> CTP-Version 2.5 (April)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in SQL Server 2019 CTP-Version 2.5.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Bereitstellungsprofile | Verwenden Sie für die Bereitstellung von Big Data-Clustern standardmäßige und benutzerdefinierte [Konfigurationsdateien für die JSON-Bereitstellung](deployment-guidance.md#configfile) anstelle von Umgebungsvariablen. |
| Bereitstellungen mit Aufforderung | `mssqlctl cluster create` ruft jetzt zu allen erforderlichen Einstellungen für Standardbereitstellungen auf. |
| Änderungen bei Dienstendpunkten und Podnamen | Die folgenden externen Endpunkte haben Namen geändert:<br/>&nbsp;&nbsp;&nbsp;- **endpoint-master-pool** => **master-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-controller** => **controller-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-service-proxy** => **mgmtproxy-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-security** => **gateway-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-app-service-proxy** => **appproxy-svc-external**|
| Verbesserungen bei **mssqlctl** | Verwenden Sie **mssqlctl** zum [Auflisten externer Endpunkte](deployment-guidance.md#endpoints) und zum Überprüfen der Version von **mssqlctl** mithilfe des Parameters `--version`. |
| Offlineinstallation | Leitfaden für offline big Data-Cluster-Bereitstellungen. |
| Verbesserungen bei HDFS-Tiering | S3-tiering, Zwischenspeichern bereitstellen und OAuth unterstützt für den ADLS-Gen2. |
| Neue `mssql` Spark-SQL Server-Connector | |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen im Zusammenhang mit dieser Version beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Müssen Sie Ihre Daten sichern und löschen Sie Ihre vorhandenen big Data-Cluster (mit der früheren Version von **Mssqlctl**) vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="external-tables"></a>Externe Tabellen

- Bereitstellung von Big Data-Cluster werden nicht mehr erstellt die **SqlDataPool** und **SqlStoragePool** Daten aus externen Quellen. Sie können diese Datenquellen manuell, um Daten bei den Daten-Pools und den Speicherpool Virtualisierungsunterstützung erstellen.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://nmnode-0-svc:50070');
   ```

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Bei der Erstellung einer externen Tabelle, Oracle, die Zeichen-Datentypen zu verwenden, interpretiert der Studio für Azure Data Virtualization-Assistent diese Spalten als VARCHAR in der Definition der externen Tabelle an. Dies bewirkt einen Fehler in der DDL für externe Tabellen. Ändern Sie entweder das Oracle-Schema, um verwenden Sie den Typ NVARCHAR2 oder EXTERNAL TABLE-Anweisungen manuell erstellen, und geben NVARCHAR, statt mit dem Assistenten.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Bei eine Anwendung von R, Python oder MLeap von RESTful-API aufrufen, tritt ein Timeout für der Aufruf innerhalb von 5 Minuten.

#### <a name="spark-and-notebooks"></a>Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

#### <a name="hdfs"></a>HDFS

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

## <a id="ctp24"></a> CTP-Version 2.4 (März)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in SQL Server 2019 CTP 2.4.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Anleitung für die GPU-Unterstützung zum Ausführen von Deep Learning mit TensorFlow in Spark | Weitere Informationen finden Sie unter [Deploy a big data cluster with GPU support and run TensorFlow (Bereitstellen eines Big Data-Clusters mit GPU-Unterstützung und Ausführen von TensorFlow)](spark-gpu-tensorflow.md). |
| Die Datenquellen **SqlDataPool** und **SqlStoragePool** werden nicht mehr standardmäßig erstellt. | Erstellen Sie diese nach Bedarf manuell. Weitere Informationen finden Sie im Abschnitt [Bekannte Probleme](#externaltablesctp24). |
| Unterstützung von `INSERT INTO SELECT` für den Datenpool | Ein Beispiel finden Sie unter [Tutorial: Ingest data into a SQL Server data pool with Transact-SQL (Tutorial: Erfassen von Daten in einem SQL Server-Datenpool mit Transact-SQL)](tutorial-data-pool-ingest-sql.md). |
| Optionen `FORCE SCALEOUTEXECUTION` und `DISABLE SCALEOUTEXECUTION` | Erzwingt, dass aktiviert oder deaktiviert die Verwendung des Pools für Compute in externen Tabellen Abfragen. Beispiel: `SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)`Hyper-V-Hosts oder Hyper-V-Hostcluster in einem separaten Namespace als verwaltete Hyper-V-Hosts hinzuzufügen. |
| Aktualisierte Bereitstellungsempfehlungen für AKS | Für die Auswertung von Big Data-Clustern in AKS wird die Verwendung eines einzelnen Knotens der Größe **Standard_L8s** empfohlen. |
| Upgrade der Spark-Runtime auf Spark 2.4 | |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen im Zusammenhang mit dieser Version beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Müssen Sie Ihre Daten sichern und löschen Sie Ihre vorhandenen big Data-Cluster (mit der früheren Version von **Mssqlctl**) vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="kubeadm-deployments"></a>Kubeadm-Bereitstellungen

Wenn Sie Kubeadm zum Bereitstellen von Kubernetes auf mehreren Computern verwenden, wird das Cluster-Verwaltungsportal die Verbindung mit der big Data-Cluster erforderlichen Endpunkte nicht richtig angezeigt. Wenn Sie dieses Problem auftreten, verwenden Sie das folgende startbefehlsskript, um die IP-Adressen der Dienstendpunkte zu ermitteln:

- Wenn Sie von innerhalb des Clusters verbinden, Fragen Sie Kubernetes für die Dienst-IP für den Endpunkt, dem für die Verbindung verwendet werden sollen. Beispielsweise die folgenden **"kubectl"** Befehl zeigt die IP-Adresse der master SQL Server-Instanz:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Wenn Sie von außerhalb des Clusters herstellen, verwenden Sie die folgenden Schritte aus, eine Verbindung herstellen:

   1. Rufen Sie die IP-Adresse des Knotens master SQL Server-Instanz ausgeführt wird: `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Verbinden Sie mit SQL Server-Masterinstanz über diese IP-Adresse.

   1. Abfrage der **Cluster_endpoint_table** in master-Datenbank für andere externe Endpunkte.

      Wenn dies ein Timeout auftritt, ist es möglich, die der entsprechende Knoten durch eine Firewall geleitet wird. In diesem Fall müssen Sie wenden Sie sich an den Administrator der Kubernetes-Cluster und stellen Sie für die Knoten-IP, die extern verfügbar gemacht wird. Dies kann einen beliebigen Knoten sein. Sie können diese IP-Adresse und den entsprechenden Port klicken Sie dann verwenden, für die Verbindung auf verschiedene Dienste, die im Cluster ausgeführt. Beispielsweise kann der Administrator diese IP-Adresse mit finden:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>Löschen Cluster ein Fehler auftritt.

Wenn Sie versuchen, das Löschen eines Clusters mit **Mssqlctl**, schlägt Sie mit den folgenden Fehler:

```
2019-03-26 20:38:11.0614 UTC | INFO | Deleting cluster ...
Error processing command: "TypeError"
delete_namespaced_service() takes 3 positional arguments but 4 were given
Makefile:61: recipe for target 'delete-cluster' failed
make[2]: *** [delete-cluster] Error 1
Makefile:223: recipe for target 'deploy-clean' failed
make[1]: *** [deploy-clean] Error 2
Makefile:203: recipe for target 'deploy-clean' failed
make: *** [deploy-clean] Error 2
```

Ein neuer Python-Kubernetes-Client (Version 9.0.0) geändert, die Delete-Namespaces-API, der derzeit unterbricht **Mssqlctl**. Dies geschieht nur, wenn Sie einen neuere Kubernetes-Python-Client installiert haben. Sie können dieses Problem umgehen, indem Sie direkt löschen den Cluster mit **"kubectl"** (`kubectl delete ns <ClusterName>`), oder Sie können installieren, die ältere Version mit `sudo pip install kubernetes==8.0.1`.

#### <a id="externaltablesctp24"></a> Externe Tabellen

- Bereitstellung von Big Data-Cluster werden nicht mehr erstellt die **SqlDataPool** und **SqlStoragePool** Daten aus externen Quellen. Sie können diese Datenquellen manuell, um Daten bei den Daten-Pools und den Speicherpool Virtualisierungsunterstützung erstellen.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   ```

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Bei der Erstellung einer externen Tabelle, Oracle, die Zeichen-Datentypen zu verwenden, interpretiert der Studio für Azure Data Virtualization-Assistent diese Spalten als VARCHAR in der Definition der externen Tabelle an. Dies bewirkt einen Fehler in der DDL für externe Tabellen. Ändern Sie entweder das Oracle-Schema, um verwenden Sie den Typ NVARCHAR2 oder EXTERNAL TABLE-Anweisungen manuell erstellen, und geben NVARCHAR, statt mit dem Assistenten.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Bei eine Anwendung von R, Python oder MLeap von RESTful-API aufrufen, tritt ein Timeout für der Aufruf innerhalb von 5 Minuten.

#### <a name="spark-and-notebooks"></a>Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

#### <a name="hdfs"></a>HDFS

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

## <a id="ctp23"></a> CTP 2.3 (Februar)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in CTP 2.3 von SQL Server 2019.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
| :---------- | :------ |
| Übermitteln von Spark-Aufträgen an Big Data-Cluster in IntelliJ | [Submit Spark jobs on SQL Server big data clusters in IntelliJ (Übermitteln von Spark-Aufträgen an Big Data-Cluster von SQL Server in IntelliJ)](spark-submit-job-intellij-tool-plugin.md) |
| Allgemeine CLI für die Anwendungsbereitstellung und Clusterverwaltung | [How to deploy an app on SQL Server 2019 big data cluster (preview) (Vorgehensweise: Bereitstellen einer App in Big Data-Clustern von SQL Server 2019 (Vorschau))](big-data-cluster-create-apps.md) |
| VS Code-Erweiterung zum Bereitstellen von Anwendungen in einem Big Data-Cluster | [How to use VS Code to deploy applications to SQL Server big data clusters (Vorgehensweise: Verwenden von VS Code zum Bereitstellen von Anwendungen in Big Data-Clustern von SQL Server)](app-deployment-extension.md) |
| Änderungen an der Befehlssyntax des Tools **mssqlctl** | Weitere Informationen finden Sie unter [Bekannte Probleme bei „mssqlctl“](#mssqlctlctp23). |
| Verwenden Sie Sparklyr in big Data-cluster | [Use Sparklyr in SQL Server 2019 big data cluster (Verwenden von Sparklyr in Big Data-Clustern von SQL Server 2019)](sparklyr-from-RStudio.md) |
| Einbinden von externen HDFS-kompatiblen Speichern (Hadoop Distributed File System) in Big Data-Clustern mit dem **HDFS-Tiering** | Weitere Informationen finden Sie unter [HDFS-Tiering](hdfs-tiering.md). |
| Neue einheitliche Verbindungsoberfläche für die SQL Server-Masterinstanz und das HDFS-/Spark-Gateway | Weitere Informationen finden Sie unter [SQL Server master instance and the HDFS/Spark Gateway (Die SQL Server-Masterinstanz und das HDFS-/Spark-Gateway)](connect-to-big-data-cluster.md). |
| Beim Löschen eines Clusters mit **mssqlctl cluster delete** werden jetzt nur noch die Objekte im Namespace gelöscht, die Teil des Big Data-Clusters waren. | Der Namespace wird nicht gelöscht. In früheren Releases wurde mit diesem Befehl jedoch nicht der gesamte Namespace gelöscht. |
| Namen von _Sicherheitsendpunkten_ wurden geändert und zusammengefasst | **service-security-lb** und **service-security-nodeport** wurden im Endpunkt **endpoint-security** zusammengefasst. |
| Namen von _Proxyendpunkten_ wurden geändert und zusammengefasst | **service-proxy-lb** und **service-proxy-nodeport** wurden im Endpunkt **endpoint-service-proxy** zusammengefasst. |
| Namen von _Controllerendpunkten_ wurden geändert und zusammengefasst | **service-mssql-controller-lb** und **service-mssql-controller-nodeport** wurden im Endpunkt **endpoint-controller** zusammengefasst. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen im Zusammenhang mit dieser Version beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Müssen Sie Ihre Daten sichern und löschen Sie Ihre vorhandenen big Data-Cluster (mit der früheren Version von **Mssqlctl**) vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-upgrade.md).

- Die **ACCEPT_EULA** -Umgebungsvariable muss "yes" oder "Ja", um den Endbenutzer-Lizenzvertrag zu akzeptieren. Vorgängerversionen zulässig, "y" und "Y", aber diese sind nicht mehr akzeptiert und führt dazu, dass die Bereitstellung nicht ausgeführt werden.

- Die **CLUSTER_PLATFORM** Umgebungsvariablen besitzt keinen Standardwert, wie in früheren Versionen.

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="kubeadm-deployments"></a>Kubeadm-Bereitstellungen

Wenn Sie Kubeadm zum Bereitstellen von Kubernetes auf mehreren Computern verwenden, wird das Cluster-Verwaltungsportal die Verbindung mit der big Data-Cluster erforderlichen Endpunkte nicht richtig angezeigt. Wenn Sie dieses Problem auftreten, verwenden Sie das folgende startbefehlsskript, um die IP-Adressen der Dienstendpunkte zu ermitteln:

- Wenn Sie von innerhalb des Clusters verbinden, Fragen Sie Kubernetes für die Dienst-IP für den Endpunkt, dem für die Verbindung verwendet werden sollen. Beispielsweise die folgenden **"kubectl"** Befehl zeigt die IP-Adresse der master SQL Server-Instanz:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Wenn Sie von außerhalb des Clusters herstellen, verwenden Sie die folgenden Schritte aus, eine Verbindung herstellen:

   1. Rufen Sie die IP-Adresse des Knotens master SQL Server-Instanz ausgeführt wird: `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Verbinden Sie mit SQL Server-Masterinstanz über diese IP-Adresse.

   1. Abfrage der **Cluster_endpoint_table** in master-Datenbank für andere externe Endpunkte.

      Wenn dies ein Timeout auftritt, ist es möglich, die der entsprechende Knoten durch eine Firewall geleitet wird. In diesem Fall müssen Sie wenden Sie sich an den Administrator der Kubernetes-Cluster und stellen Sie für die Knoten-IP, die extern verfügbar gemacht wird. Dies kann einen beliebigen Knoten sein. Sie können diese IP-Adresse und den entsprechenden Port klicken Sie dann verwenden, für die Verbindung auf verschiedene Dienste, die im Cluster ausgeführt. Beispielsweise kann der Administrator diese IP-Adresse mit finden:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="mssqlctlctp23"></a> mssqlctl

- Die **Mssqlctl** Tool geändert werden, von einem Verb-Nomen-Befehl, der Sortierung auf eine Bestellung Substantiv-Verb. Z. B. `mssqlctl create cluster` ist jetzt `mssqlctl cluster create`.

- Die `--name` -Parameter ist jetzt erforderlich, beim Erstellen eines Clusters mit `mssqlctl cluster create`.

   ```bash
   mssqlctl cluster create --name <cluster_name>
   ```

- Wichtige Informationen zum Upgrade auf die neueste Version von big Data-Cluster und **Mssqlctl**, finden Sie unter [ein Upgrade auf ein neues Release](deployment-upgrade.md).

#### <a name="external-tables"></a>Externe Tabellen

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Bei der Erstellung einer externen Tabelle, Oracle, die Zeichen-Datentypen zu verwenden, interpretiert der Studio für Azure Data Virtualization-Assistent diese Spalten als VARCHAR in der Definition der externen Tabelle an. Dies bewirkt einen Fehler in der DDL für externe Tabellen. Ändern Sie entweder das Oracle-Schema, um verwenden Sie den Typ NVARCHAR2 oder EXTERNAL TABLE-Anweisungen manuell erstellen, und geben NVARCHAR, statt mit dem Assistenten.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Bei eine Anwendung von R, Python oder MLeap von RESTful-API aufrufen, tritt ein Timeout für der Aufruf innerhalb von 5 Minuten.

#### <a name="spark-and-notebooks"></a>Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

#### <a name="hdfs"></a>HDFS

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

## <a id="ctp22"></a> CTP 2.2 (Dezember 2018)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in SQL Server 2019 CTP 2.2.

### <a name="new-features"></a>Neue Funktionen

- Cluster-Verwaltungsportal Zugriff mit `/portal` (**https://\<Ip-Adresse\>: 30777/Portal**).
- Master-Dienst-Poolname geändert `service-master-pool-lb` und `service-master-pool-nodeport` zu `endpoint-master-pool`.
- Neue Version des **Mssqlctl** und Images aktualisiert.
- Verschiedene Fehlerbehebungen und Verbesserungen.

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen im Zusammenhang mit dieser Version beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt. Sie müssen die sichern und löschen Sie alle vorhandenen big Data-Cluster vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="cluster-administration-portal"></a>Cluster-Verwaltungsportal

Das Verwaltungsportal für den Cluster wird den Endpunkt für die master-SQL Server-Instanz nicht angezeigt. Um die IP-Adresse und den Port für die master-Instanz ermitteln möchten, verwenden Sie die folgenden **"kubectl"** Befehl:

```
kubectl get svc endpoint-master-pool -n <your-big-data-cluster-name>
```

#### <a name="external-tables"></a>Externe Tabellen

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

#### <a name="hdfs"></a>HDFS

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

## <a id="ctp21"></a> CTP-Version 2.1 (November 2018)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in SQL Server CTP 2.1 an 2019.

### <a name="new-features"></a>Neue Funktionen

- [Bereitstellen von Python und R-apps](big-data-cluster-create-apps.md) in einer big Data-Cluster.
- Neue Version des **Mssqlctl** und Images aktualisiert. 
- Verschiedene Fehlerbehebungen und Verbesserungen.

### <a name="known-issues"></a>Bekannte Probleme

Die folgenden Abschnitte enthalten bekannte Probleme für SQL Server-big Data-Cluster in der CTP-Version 2.1.

#### <a name="deployment"></a>Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt. Sie müssen die sichern und löschen Sie alle vorhandenen big Data-Cluster vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="admin-portal"></a>Admin-portal

- Wenn Sie [Erstellen einer app mithilfe von Msqlctl-CTP-Version-Befehl](big-data-cluster-create-apps.md) und Ihre Bereitstellung in einer SQL-Server, die big Data-Cluster, die Cluster-Admin-Portal zeigt die Pods, in dem die Anwendung als "Unbekannt" im Abschnitt "Controller" des Bereichs Admin bereitgestellt wurde.

#### <a name="external-tables"></a>Externe Tabellen

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

#### <a name="hdfs"></a>HDFS

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

## <a id="ctp20"></a> CTP-Version 2.0 (Oktober 2018)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in SQL Server 2019 CTP-Version 2.0.

### <a name="new-features"></a>Neue Funktionen

- Einfache bereitstellungserfahrung, die mithilfe des Verwaltungstools mssqlctl
- Native Notebook-Benutzeroberfläche in Azure Data Studio
- Abfragen von HDFS-Dateien über das Storage-Instanz von SQL Server
- Data Virtualization über Master zu SQL Server, Oracle, MongoDB und HDFS
- Data Virtualization-Assistenten für SQL Server und Oracle in Azure Data Studio
- ML-Dienste auf dem Masterknoten
- Portal zur Verwaltung von Cluster, die Sie verwenden können, für die Überwachung und Problembehandlung
- Übermitteln von Spark-Auftrags in Azure Data Studio 
- Spark-Benutzeroberfläche im Cluster-Verwaltungsportal
- Volume einbinden, Speicherklassen
- Abfragen über Datenpools aus dem masterbranch
- Plan für verteilte Abfragen in SSMS anzeigen
- PIP-Paket für Mssqlctl-Verwaltungstool
- Integrierte bereitstellungs-Engine, durch den Controller-Dienst

### <a name="known-issues"></a>Bekannte Probleme

Die folgenden Abschnitte enthalten bekannte Probleme für SQL Server-big Data-Cluster in der CTP-Version 2.0.

#### <a name="deployment"></a>Bereitstellung

- Wenn Sie Azure Kubernetes Service (AKS) verwenden, ist die empfohlene Version von Kubernetes 1.10. *, die unterstützt keine Größenänderung für den Datenträger. Stellen Sie sicher, Sie sind den Speicher entsprechend Größe zum Zeitpunkt der Bereitstellung. Weitere Informationen zum Anpassen von Speichergrößen finden Sie unter den [Datenpersistenz](concept-data-persistence.md) Artikel. Für Kubernetes, die auf virtuellen Computern bereitgestellt werden ist die empfohlene Version 1.11.

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="external-tables"></a>Externe Tabellen

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

#### <a name="hdfs"></a>HDFS

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-big Data-Clustern, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
