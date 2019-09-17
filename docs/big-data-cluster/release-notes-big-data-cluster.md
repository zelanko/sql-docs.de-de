---
title: Versionshinweise
titleSuffix: SQL Server big data clusters
description: In diesem Artikel werden die neuesten Updates und bekannten Probleme [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] für (Vorschau) beschrieben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bcbc3537a6ba26dc907bf348c565939ff869ea43
ms.sourcegitcommit: da8bb7abd256b2bebee7852dc0164171eeff11be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988097"
---
# <a name="release-notes-for-sql-server-big-data-clusters"></a>Anmerkungen zu dieser Version von SQL Server Big Data-Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel werden Updates und bekannte Probleme für die neuesten Versionen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]aufgeführt.

## <a id="rc"></a>Release Candidate (August)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 Release Candidate beschrieben.

### <a name="whats-new"></a>Neues

|Neue Funktion oder Update | Details |
|:---|:---|
|SQL Server Always on Verfügbarkeits Gruppe |Beim Bereitstellen eines SQL Server Big Data-Clusters können Sie die Bereitstellung so konfigurieren, dass eine Verfügbarkeits Gruppe erstellt wird, die Folgendes bereitstellt:<br/><br/>-Hohe Verfügbarkeit <br/><br/>-Read-Scale Out <br/><br/>-Horizontales Skalieren von Daten in den Daten Pool<br/><br>Siehe bereitstellen [mit hoher Verfügbarkeit](../big-data-cluster/deployment-high-availability.md). |
|`azdata` |Vereinfachte Installation für das Tool mit dem [Installations-Manager](./deploy-install-azdata-linux-package.md)<br/><br/>[`azdata notebook`s](./reference-azdata-notebook.md)<br/><br/>[`azdata bdc status`s](./reference-azdata-bdc-status.md) |
|Azure Data Studio|[Laden Sie den Release Candidate-Build von Azure Data Studio herunter](deploy-big-data-tools.md#download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc).<br/><br/>Problem Behandlungs Notebooks wurden im jupyter-Handbuch SQL Server 2019 Guide hinzugefügt.<br/><br/>Benutzeroberflächen Anmeldung hinzugefügt.<br/><br/>Controller Dashboard zum Anzeigen von Dienst Endpunkten, Anzeigen des Integritäts Status des Clusters und Zugreifen auf Problembehandlungs-Notebooks hinzugefügt.<br/><br/>Verbesserte Ausgabe-/Bearbeitungsleistung von Notebook Zellen.|
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme

* SQL Server 2019 Big Data-Cluster Release Candidate Buildnummer `15.0.1900.47`aktualisieren ist.

* Das Bereitstellungs Profil "kubeadm-Prod" wird in SQL Server 2019-Big Data-Clustern, Release Candidate mit der obigen Buildnummer, nicht unterstützt. Verwenden Sie stattdessen das Profil "kubeadm-dev-Test" für kubeadm-bereit Stellungen.

## <a id="ctp32"></a> CTP 3.2 (Juli)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 3.2 beschrieben.

### <a name="whats-new"></a>Neues

|Neue Funktion oder Update | Details |
|:---|:---|
|Public Preview |Vor CTP 3.2 war SQL Server-Big-Data-Cluster für registrierte Early Adopter verfügbar. Dieses Release ermöglicht allen Benutzern, die Funktionen von SQL Server-Big-Data-Clustern zu nutzen. <br/><br/> Weitere Informationen finden [Sie [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]unter Einstieg in ](deploy-get-started.md).|
|`azdata` |CTP 3.2 führt `azdata` ein – ein in Python geschriebenes Befehlszeilenprogramm, das Clusteradministratoren ermöglicht, den Big-Data-Cluster über REST-APIs zu starten und zu verwalten. `azdata` ersetzt `mssqlctl`. Siehe [Installieren von `azdata`](deploy-install-azdata.md). |
|PolyBase |Externe Tabellenspaltennamen werden jetzt zum Abfragen von SQL Server-, Oracle-, Teradata-, MongoDB- und ODBC-Datenquellen verwendet. In früheren CTP-Releases wurden die Spalten in der externen Datenquelle nur auf Basis der Ordinalposition gebunden, und die in der Definition der EXTERNEN TABELLE angegebenen Namen wurden nicht verwendet. |
|HDFS-Tieringaktualisierung |Einführung der Aktualisierungsfunktionalität für HDFS-Tiering, sodass eine vorhandene Einbindung für die neueste Momentaufnahme der Remotedaten aktualisiert werden kann. Weitere Informationen finden Sie unter [HDFS-Tiering](hdfs-tiering.md). |
|Notebook-basierte Problembehandlung |CTP 3.2 stellt Jupyter-Notebooks vor, die die [Bereitstellung](deploy-notebooks.md) und [Ermittlung, Diagnose und Problembehandlung](manage-notebooks.md) für Komponenten in einem SQL Server-Big-Data-Cluster unterstützen. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in diesem Release beschrieben.

#### <a name="polybase"></a>PolyBase

- Die Weitergabe der TOP-Klausel, wenn die Anzahl > 1000 ist, wird in diesem Release nicht unterstützt. In solchen Fällen werden alle Zeilen aus der Remotedatenquelle gelesen. (In Release Candidate korrigiert)

- Die Weitergabe von verbundenen Joins an externe Datenquellen wird in diesem Release nicht unterstützt. Mit der Weitergabe von zwei Datenpooltabellen vom Verteilungstyp ROUND_ROBIN gelangen die Daten zur Ausführung der JOIN-Operation in die SQL Master- oder Computepoolinstanz.

#### <a name="compute-pool"></a>Computepool

- Die Big-Data-Clusterbereitstellung unterstützt nur Computepools mit einer Instanz. (In Release Candidate korrigiert)

#### <a name="storage-pool"></a>Speicherpool

- Beim Abfragen von PARQUET-Dateien im Speicherpool werden bestimmte Datentypen nicht unterstützt.

- Übergeordnete MAP- und LIST-Spalten sowie übergeordnete Spalten ohne einen angefügten Typ können nicht abgefragt werden. Dabei wird eine Fehlermeldung zurückgegeben.

- WIEDERHOLTE Knoten können nicht abgefragt werden und geben möglicherweise falsche Ergebnisse zurück.

## <a id="ctp31"></a> CTP 3.1 (Juni)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 3.1 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Änderungen am Befehl `mssqlctl` | Die `mssqlctl cluster`-Befehle wurden in `mssqlctl bdc` umbenannt. Weitere Informationen finden Sie in der [Referenz zu `mssqlctl`](reference-azdata.md). |
| Neue `mssqlctl`-Statusbefehle und Wegfall des Cluster-Verwaltungsportals | Das Cluster-Verwaltungsportal ist ab diesem Release nicht mehr enthalten. `mssqlctl` enthält neue Statusbefehle, die die vorhandenen Überwachungsbefehle ergänzen. |
| Spark-Computepools | Erstellen Sie zusätzliche Knoten, um die Spark-Rechenleistung zu erhöhen, ohne den Speicher zentral hochskalieren zu müssen. Zudem können Sie Speicherpoolknoten starten, die nicht für Spark verwendet werden. Spark wird vom Speicher entkoppelt. Weitere Informationen finden Sie unter [Configure storage without spark (Konfigurieren des Speichers ohne Spark)](deployment-custom-configuration.md#sparkstorage). |
| MSSQL-Spark-Connector | Ab jetzt werden Lese- und Schreibvorgänge in externen Datenpooltabellen unterstützt. In vorherigen Releases wurden Lese- und Schreibvorgänge nur für Tabellen der MASTER-Instanz unterstützt. Weitere Informationen finden Sie unter [How to read and write to SQL Server from Spark using the MSSQL Spark Connector (Lesen und Schreiben in SQL Server über Spark mithilfe des MSSQL-Spark-Connectors)](spark-mssql-connector.md). |
| Machine Learning mit MLeap | [Trainieren Sie ein MLeap-Machine-Learning-Modell in Spark, und bewerten Sie es mit der Java-Spracherweiterung in SQL Server.](spark-create-machine-learning-model.md) |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in diesem Release beschrieben.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, mit denen Änderungen an „hdfs-site.xml“ einhergehen, werden nicht unterstützt.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big-Data-Datenclusters von einem vorherigen Release wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie das neueste Release bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big-Data-Cluster (mithilfe des vorherigen Releases von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warnereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch eine erfolgreiche Bereitstellung des Big-Data-Clusters in AKS nicht verhindern.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big-Data-Clusterbereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Dieses Problem kann umgangen werden, indem der Namespace vor der Bereitstellung eines Clusters mit dem gleichen Namen manuell gelöscht wird.

#### <a name="external-tables"></a>Externe Tabellen

- Bei der Big-Data-Clusterbereitstellung werden die externen Datenquellen **SqlDataPool** und **SqlStoragePool** nicht mehr erstellt. Sie können diese Datenquellen manuell erstellen, um die Datenvirtualisierung für den Datenpool und den Speicherpool zu unterstützen.

   > [!NOTE]
   > Der URI zum Erstellen dieser externen Datenquellen ist je nach CTP unterschiedlich. Wie Sie diese Datenquellen erstellen, sehen Sie anhand der folgenden Transact-SQL-Befehle. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Für eine Tabelle, die nicht unterstützte Spaltentypen aufweist, kann eine externe Datenpooltabelle erstellt werden. Wenn Sie die externe Tabelle abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle eines Speicherpools abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Daten vom Typ CHAR enthält, werden diese Spalten in der Definition der externen Tabelle vom Azure Data Studio-Virtualisierungsassistenten als VARCHAR interpretiert. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie manuell EXTERNAL TABLE-Anweisungen, und geben Sie NVARCHAR an, statt den Assistenten zu verwenden.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie über die RESTful-API eine R-, Python- oder MLeap-Anwendung aufrufen, tritt beim Aufruf nach 5 Minuten eine Zeitüberschreitung auf.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. Wenn der Masterpod neu gestartet wird, schlägt die Spark-Sitzung möglicherweise mit `NoRoteToHostException` fehl. Ursache hierfür sind JVM-Caches, die nicht mit den neuen IP-Adressen aktualisiert werden.

- Wenn Sie Jupyter bereits installiert haben und getrennt davon Python unter Windows verwenden, tritt bei Spark-Notebooks möglicherweise ein Fehler auf. Dieses Problem können Sie umgehen, indem Sie für Jupyter ein Upgrade auf die neueste Version ausführen.

- Wenn Sie bei einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle nicht im Bearbeitungsmodus, sondern im Vorschaumodus hinzugefügt. Sie können auf das Vorschausymbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD-Variable ist Teil der Umgebung und kann erkannt werden (z. B. in einer CORD-Sicherungsdatei). Nach der Bereitstellung müssen Sie die SA_PASSWORD-Variable in der Masterinstanz zurücksetzen. Das ist kein Fehler, sondern eine Sicherheitsmaßnahme. Weitere Informationen zum Ändern der SA_PASSWORD-Variablen in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle enthalten möglicherweise ein Systemadministratorkennwort für Big-Data-Clusterbereitstellungen.

#### <a name="kibana-logs-dashboards"></a>Kibana-Protokolldashboards

- Zwischen Aris CTP 3.0 und 3.1 wurde für die Kibana-Version ein Upgrade von 6.3.1 auf 7.0.1 ausgeführt.  Dies hat den Microsoft Edge-Browser mit kibana nicht kompatibel gemacht. Benutzern wird beim Laden der aktuellen Version der kibana-Dashboards in Microsoft Edge eine leere Seite angezeigt. Klicken Sie [hier]( https://www.elastic.co/support/matrix#matrix_browse), um unterstützte Browser für Kibana.rs anzuzeigen. 


## <a id="ctp30"></a> CTP 3.0 (Mai)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 3.0 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| **mssqlctl**-Updates | Mehrere [Updates für den Befehl **mssqlctl** und seine Parameter](reference-azdata.md). Dies umfasst ein Update für den Befehl **mssqlctl login**, der nun den Controllerbenutzernamen und -endpunkt zum Ziel hat. |
| Speichererweiterungen | Unterstützung für verschiedene Speicherkonfigurationen für Protokolle und Daten. Darüber hinaus wurde die Anzahl der Ansprüche von persistentem Volume für einen Big Data-Cluster gesenkt. |
| Mehrere Computepoolinstanzen | Unterstützung für mehrere Computepoolinstanzen. |
| Neues Poolverhalten und neue Poolfunktionen | Der Computepool wird jetzt standardmäßig für Speicherpool- und Datenpoolvorgänge ausschließlich in einer **ROUND_ROBIN**-Verteilung verwendet. Der Datenpool kann nun einen neuen Verteilungstyp **REPLICATED** verwenden, was bedeutet, dass dieselben Daten in allen Datenpoolinstanzen vorhanden sind. |
| Verbesserungen externer Tabellen | Externe Tabellen des HADOOP-Datenquellentyps unterstützen nun das Lesen von Zeilen mit einer Größe von bis zu 1 MB. Externe Tabellen (ODBC, Speicherpool, Datenpool) unterstützen jetzt Zeilen mit der Breite einer SQL Server-Tabelle. |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in diesem Release beschrieben.

#### <a name="hdfs"></a>HDFS

- Azure Data Studio gibt einen Fehler zurück, wenn Sie in HDFS einen neuen Ordner erstellen. Wenn Sie diese Funktion aktivieren möchten, installieren Sie das Insider-Build von Azure Data Studio:
  
   - [Windows-Benutzer-Installationsprogramm – **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-user/insider)
   - [Windows-System-Installationsprogramm – **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64/insider)
   - [Windows-ZIP – **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-archive/insider)
   - [macOS-ZIP – **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/darwin/insider)
   - [Linux TAR.GZ - **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/linux-x64/insider)

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, mit denen Änderungen an „hdfs-site.xml“ einhergehen, werden nicht unterstützt.

#### <a name="deployment"></a>Bereitstellung

- Die vorherigen Bereitstellungsvorgänge für GPU-fähige Big-Data-Cluster werden in CTP 3.0 nicht unterstützt. Nach einem alternativen Bereitstellungsvorgang wird derzeit gesucht. Zur Vermeidung von Verwechslungen wurde die Veröffentlichung des Artikels „Deploy a big data cluster with GPU support and run TensorFlow“ (Bereitstellen eines Big-Data-Clusters mit GPU-Unterstützung und Ausführen von TensorFlow) vorläufig aufgehoben.

- Das Upgrade eines Big-Data-Datenclusters von einem vorherigen Release wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie das neueste Release bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big-Data-Cluster (mithilfe des vorherigen Releases von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warnereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch eine erfolgreiche Bereitstellung des Big-Data-Clusters in AKS nicht verhindern.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big-Data-Clusterbereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Dieses Problem kann umgangen werden, indem der Namespace vor der Bereitstellung eines Clusters mit dem gleichen Namen manuell gelöscht wird.

#### <a name="external-tables"></a>Externe Tabellen

- Bei der Big-Data-Clusterbereitstellung werden die externen Datenquellen **SqlDataPool** und **SqlStoragePool** nicht mehr erstellt. Sie können diese Datenquellen manuell erstellen, um die Datenvirtualisierung für den Datenpool und den Speicherpool zu unterstützen.

   > [!NOTE]
   > Der URI zum Erstellen dieser externen Datenquellen ist je nach CTP unterschiedlich. Wie Sie diese Datenquellen erstellen, sehen Sie anhand der folgenden Transact-SQL-Befehle. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Für eine Tabelle, die nicht unterstützte Spaltentypen aufweist, kann eine externe Datenpooltabelle erstellt werden. Wenn Sie die externe Tabelle abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle eines Speicherpools abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Daten vom Typ CHAR enthält, werden diese Spalten in der Definition der externen Tabelle vom Azure Data Studio-Virtualisierungsassistenten als VARCHAR interpretiert. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie manuell EXTERNAL TABLE-Anweisungen, und geben Sie NVARCHAR an, statt den Assistenten zu verwenden.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie über die RESTful-API eine R-, Python- oder MLeap-Anwendung aufrufen, tritt beim Aufruf nach 5 Minuten eine Zeitüberschreitung auf.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. Wenn der Masterpod neu gestartet wird, schlägt die Spark-Sitzung möglicherweise mit `NoRoteToHostException` fehl. Ursache hierfür sind JVM-Caches, die nicht mit den neuen IP-Adressen aktualisiert werden.

- Wenn Sie Jupyter bereits installiert haben und getrennt davon Python unter Windows verwenden, tritt bei Spark-Notebooks möglicherweise ein Fehler auf. Dieses Problem können Sie umgehen, indem Sie für Jupyter ein Upgrade auf die neueste Version ausführen.

- Wenn Sie bei einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle nicht im Bearbeitungsmodus, sondern im Vorschaumodus hinzugefügt. Sie können auf das Vorschausymbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD-Variable ist Teil der Umgebung und kann erkannt werden (z. B. in einer CORD-Sicherungsdatei). Nach der Bereitstellung müssen Sie die SA_PASSWORD-Variable in der Masterinstanz zurücksetzen. Das ist kein Fehler, sondern eine Sicherheitsmaßnahme. Weitere Informationen zum Ändern der SA_PASSWORD-Variablen in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle enthalten möglicherweise ein Systemadministratorkennwort für Big-Data-Clusterbereitstellungen.

## <a id="ctp25"></a> CTP 2.5 (April)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 2.5 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Bereitstellungsprofile | Verwenden Sie für die Bereitstellung von Big Data-Clustern standardmäßige und benutzerdefinierte [Konfigurationsdateien für die JSON-Bereitstellung](deployment-guidance.md#configfile) anstelle von Umgebungsvariablen. |
| Bereitstellungen mit Aufforderung | `azdata cluster create` ruft jetzt zu allen erforderlichen Einstellungen für Standardbereitstellungen auf. |
| Änderungen bei Dienstendpunkten und Podnamen | Die Namen der folgenden externen Endpunkte haben sich geändert:<br/>&nbsp;&nbsp;&nbsp;- **endpoint-master-pool** => **master-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-controller** => **controller-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-service-proxy** => **mgmtproxy-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-security** => **gateway-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-app-service-proxy** => **appproxy-svc-external**|
| **azdata**-Verbesserungen | Verwenden Sie **azdata** zum [Auflisten externer Endpunkte](deployment-guidance.md#endpoints) und zum Überprüfen der Version von **azdata** mithilfe des Parameters `--version`. |
| Offlineinstallation | Anleitung für Offlinebereitstellungen von Big-Data-Clustern |
| Verbesserungen bei HDFS-Tiering | S3-Tiering, Mountcaching und OAuth-Unterstützung für ADLS Gen2. |
| Neuer `mssql`-Connector zu SQL Server aus Spark | |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in diesem Release beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big-Data-Datenclusters von einem vorherigen Release wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie das neueste Release bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big-Data-Cluster (mithilfe des vorherigen Releases von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warnereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch eine erfolgreiche Bereitstellung des Big-Data-Clusters in AKS nicht verhindern.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big-Data-Clusterbereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Dieses Problem kann umgangen werden, indem der Namespace vor der Bereitstellung eines Clusters mit dem gleichen Namen manuell gelöscht wird.

#### <a name="external-tables"></a>Externe Tabellen

- Bei der Big-Data-Clusterbereitstellung werden die externen Datenquellen **SqlDataPool** und **SqlStoragePool** nicht mehr erstellt. Sie können diese Datenquellen manuell erstellen, um die Datenvirtualisierung für den Datenpool und den Speicherpool zu unterstützen.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://nmnode-0-svc:50070');
   ```

- Für eine Tabelle, die nicht unterstützte Spaltentypen aufweist, kann eine externe Datenpooltabelle erstellt werden. Wenn Sie die externe Tabelle abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle eines Speicherpools abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Daten vom Typ CHAR enthält, werden diese Spalten in der Definition der externen Tabelle vom Azure Data Studio-Virtualisierungsassistenten als VARCHAR interpretiert. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie manuell EXTERNAL TABLE-Anweisungen, und geben Sie NVARCHAR an, statt den Assistenten zu verwenden.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie über die RESTful-API eine R-, Python- oder MLeap-Anwendung aufrufen, tritt beim Aufruf nach 5 Minuten eine Zeitüberschreitung auf.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. Wenn der Masterpod neu gestartet wird, schlägt die Spark-Sitzung möglicherweise mit `NoRoteToHostException` fehl. Ursache hierfür sind JVM-Caches, die nicht mit den neuen IP-Adressen aktualisiert werden.

- Wenn Sie Jupyter bereits installiert haben und getrennt davon Python unter Windows verwenden, tritt bei Spark-Notebooks möglicherweise ein Fehler auf. Dieses Problem können Sie umgehen, indem Sie für Jupyter ein Upgrade auf die neueste Version ausführen.

- Wenn Sie bei einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle nicht im Bearbeitungsmodus, sondern im Vorschaumodus hinzugefügt. Sie können auf das Vorschausymbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, mit denen Änderungen an „hdfs-site.xml“ einhergehen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD-Variable ist Teil der Umgebung und kann erkannt werden (z. B. in einer CORD-Sicherungsdatei). Nach der Bereitstellung müssen Sie die SA_PASSWORD-Variable in der Masterinstanz zurücksetzen. Das ist kein Fehler, sondern eine Sicherheitsmaßnahme. Weitere Informationen zum Ändern der SA_PASSWORD-Variablen in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle enthalten möglicherweise ein Systemadministratorkennwort für Big-Data-Clusterbereitstellungen.

## <a id="ctp24"></a> CTP 2.4 (März)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 2.4 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Anleitung für die GPU-Unterstützung zum Ausführen von Deep Learning mit TensorFlow in Spark | Weitere Informationen finden Sie unter [Deploy a big data cluster with GPU support and run TensorFlow (Bereitstellen eines Big Data-Clusters mit GPU-Unterstützung und Ausführen von TensorFlow)](spark-gpu-tensorflow.md). |
| Die Datenquellen **SqlDataPool** und **SqlStoragePool** werden nicht mehr standardmäßig erstellt. | Erstellen Sie diese nach Bedarf manuell. Weitere Informationen finden Sie im Abschnitt [Bekannte Probleme](#externaltablesctp24). |
| Unterstützung von `INSERT INTO SELECT` für den Datenpool | Ein Beispiel finden Sie unter [Tutorial: Ingest data into a SQL Server data pool with Transact-SQL (Tutorial: Erfassen von Daten in einem SQL Server-Datenpool mit Transact-SQL)](tutorial-data-pool-ingest-sql.md). |
| Optionen `FORCE SCALEOUTEXECUTION` und `DISABLE SCALEOUTEXECUTION` | Erzwingt oder deaktiviert die Verwendung des Computepools für Abfragen für externe Tabellen. Beispiel: `SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)`Hyper-V-Hosts oder Hyper-V-Hostcluster in einem separaten Namespace als verwaltete Hyper-V-Hosts hinzuzufügen. |
| Aktualisierte Bereitstellungsempfehlungen für AKS | Für die Auswertung von Big Data-Clustern in AKS wird die Verwendung eines einzelnen Knotens der Größe **Standard_L8s** empfohlen. |
| Upgrade der Spark-Runtime auf Spark 2.4 | |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in diesem Release beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big-Data-Datenclusters von einem vorherigen Release wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie das neueste Release bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big-Data-Cluster (mithilfe des vorherigen Releases von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warnereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch eine erfolgreiche Bereitstellung des Big-Data-Clusters in AKS nicht verhindern.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big-Data-Clusterbereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Dieses Problem kann umgangen werden, indem der Namespace vor der Bereitstellung eines Clusters mit dem gleichen Namen manuell gelöscht wird.

#### <a name="kubeadm-deployments"></a>Kubeadm-Bereitstellungen

Wenn Sie Kubeadm zum Bereitstellen von Kubernetes auf mehreren Computern verwenden, werden im Cluster-Verwaltungsportal die Endpunkte, die zum Herstellen einer Verbindung mit dem Big-Data-Cluster benötigt werden, nicht ordnungsgemäß angezeigt. Wenn dieses Problem auftritt, verwenden Sie die folgende Problemumgehung, um die IP-Adressen des Dienstendpunkts zu ermitteln:

- Wenn Sie innerhalb des Clusters eine Verbindung herstellen, fragen Sie von Kubernetes die IP-Adresse des Dienstendpunkts ab, mit dem Sie eine Verbindung herstellen möchten. Mit dem folgenden **kubectl**-Befehl wird beispielsweise die IP-Adresse der SQL Server-Masterinstanz angezeigt:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Wenn Sie von außerhalb des Clusters eine Verbindung herstellen, führen Sie zum Herstellen der Verbindung die folgenden Schritte aus:

   1. Rufen Sie die IP-Adresse des Knotens ab, auf dem die SQL Server-Masterinstanz ausgeführt wird: `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Stellen Sie mithilfe dieser IP-Adresse eine Verbindung mit der SQL Server-Masterinstanz her.

   1. Fragen Sie **cluster_endpoint_table** in der Masterdatenbank nach weiteren externen Endpunkten ab.

      Wenn diese Abfrage mit einem Verbindungstimeout fehlschlägt, wird der entsprechende Knoten möglicherweise durch eine Firewall geschützt. In diesem Fall müssen Sie sich an den Administrator des Kubernetes-Clusters wenden und nach der extern verfügbar gemachten IP-Adresse des Knotens fragen. Dies kann ein beliebiger Knoten sein. Anschließend können Sie diese IP-Adresse und den entsprechenden Port zum Herstellen einer Verbindung mit verschiedenen Diensten verwenden, die im Cluster ausgeführt werden. Der Administrator kann diese IP-Adresse beispielsweise ermitteln, indem er Folgendes ausführt:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>Fehler beim Löschen eines Clusters

Wenn Sie versuchen, einen Cluster mit **azdata** zu löschen, tritt der folgende Fehler auf:

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

Ein neuer Python Kubernetes-Client (Version 9.0.0) hat die API zum Löschen von Namespaces geändert, die derzeit **azdata** unterbricht. Dies geschieht nur, wenn Sie einen neueren Kubernetes Python-Client installiert haben. Sie können dieses Problem umgehen, indem Sie den Cluster mithilfe von **kubectl** (`kubectl delete ns <ClusterName>`) direkt löschen oder die ältere Version mithilfe von `sudo pip install kubernetes==8.0.1` installieren.

#### <a id="externaltablesctp24"></a> Externe Tabellen

- Bei der Big-Data-Clusterbereitstellung werden die externen Datenquellen **SqlDataPool** und **SqlStoragePool** nicht mehr erstellt. Sie können diese Datenquellen manuell erstellen, um die Datenvirtualisierung für den Datenpool und den Speicherpool zu unterstützen.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   ```

- Für eine Tabelle, die nicht unterstützte Spaltentypen aufweist, kann eine externe Datenpooltabelle erstellt werden. Wenn Sie die externe Tabelle abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle eines Speicherpools abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Daten vom Typ CHAR enthält, werden diese Spalten in der Definition der externen Tabelle vom Azure Data Studio-Virtualisierungsassistenten als VARCHAR interpretiert. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie manuell EXTERNAL TABLE-Anweisungen, und geben Sie NVARCHAR an, statt den Assistenten zu verwenden.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie über die RESTful-API eine R-, Python- oder MLeap-Anwendung aufrufen, tritt beim Aufruf nach 5 Minuten eine Zeitüberschreitung auf.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. Wenn der Masterpod neu gestartet wird, schlägt die Spark-Sitzung möglicherweise mit `NoRoteToHostException` fehl. Ursache hierfür sind JVM-Caches, die nicht mit den neuen IP-Adressen aktualisiert werden.

- Wenn Sie Jupyter bereits installiert haben und getrennt davon Python unter Windows verwenden, tritt bei Spark-Notebooks möglicherweise ein Fehler auf. Dieses Problem können Sie umgehen, indem Sie für Jupyter ein Upgrade auf die neueste Version ausführen.

- Wenn Sie bei einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle nicht im Bearbeitungsmodus, sondern im Vorschaumodus hinzugefügt. Sie können auf das Vorschausymbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, mit denen Änderungen an „hdfs-site.xml“ einhergehen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD-Variable ist Teil der Umgebung und kann erkannt werden (z. B. in einer CORD-Sicherungsdatei). Nach der Bereitstellung müssen Sie die SA_PASSWORD-Variable in der Masterinstanz zurücksetzen. Das ist kein Fehler, sondern eine Sicherheitsmaßnahme. Weitere Informationen zum Ändern der SA_PASSWORD-Variablen in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle enthalten möglicherweise ein Systemadministratorkennwort für Big-Data-Clusterbereitstellungen.

## <a id="ctp23"></a> CTP 2.3 (Februar)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 2.3 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
| :---------- | :------ |
| Übermitteln von Spark-Aufträgen an Big Data-Cluster in IntelliJ | [Übermitteln von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Spark-Aufträgen in IntelliJ](spark-submit-job-intellij-tool-plugin.md) |
| Allgemeine CLI für die Anwendungsbereitstellung und Clusterverwaltung | [Bereitstellen einer APP auf[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-create-apps.md) |
| VS Code-Erweiterung zum Bereitstellen von Anwendungen in einem Big Data-Cluster | [Verwenden von vs Code zum Bereitstellen von Anwendungen[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](app-deployment-extension.md) |
| Änderungen an der Befehlssyntax des Tools **azdata** | Weitere Informationen finden Sie unter [Bekannte Probleme bei „azdata“](#azdatactp23). |
| Verwenden von Sparklyr in Big-Data-Clustern | [Use Sparklyr in SQL Server 2019 big data cluster (Verwenden von Sparklyr in Big Data-Clustern von SQL Server 2019)](sparklyr-from-RStudio.md) |
| Einbinden von externen HDFS-kompatiblen Speichern (Hadoop Distributed File System) in Big Data-Clustern mit dem **HDFS-Tiering** | Weitere Informationen finden Sie unter [HDFS-Tiering](hdfs-tiering.md). |
| Neue einheitliche Verbindungsoberfläche für die SQL Server-Masterinstanz und das HDFS-/Spark-Gateway | Weitere Informationen finden Sie unter [SQL Server master instance and the HDFS/Spark Gateway (Die SQL Server-Masterinstanz und das HDFS-/Spark-Gateway)](connect-to-big-data-cluster.md). |
| Beim Löschen eines Clusters mit **azdata cluster delete** werden jetzt nur noch die Objekte im Namespace gelöscht, die Teil des Big-Data-Clusters waren. | Der Namespace wird nicht gelöscht. In früheren Releases wurde mit diesem Befehl jedoch nicht der gesamte Namespace gelöscht. |
| Namen von _Sicherheitsendpunkten_ wurden geändert und zusammengefasst | **service-security-lb** und **service-security-nodeport** wurden im Endpunkt **endpoint-security** zusammengefasst. |
| Namen von _Proxyendpunkten_ wurden geändert und zusammengefasst | **service-proxy-lb** und **service-proxy-nodeport** wurden im Endpunkt **endpoint-service-proxy** zusammengefasst. |
| Namen von _Controllerendpunkten_ wurden geändert und zusammengefasst | **service-mssql-controller-lb** und **service-mssql-controller-nodeport** wurden im Endpunkt **endpoint-controller** zusammengefasst. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in diesem Release beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big-Data-Datenclusters von einem vorherigen Release wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie das neueste Release bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big-Data-Cluster (mithilfe des vorherigen Releases von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

- Die **ACCEPT_EULA**-Umgebungsvariable muss „ja“ oder „Ja“ lauten, um die Lizenzbedingungen zu akzeptieren. In früheren Releases war „j“ und „J“ zulässig. Dies wird jedoch nicht mehr akzeptiert und führt zu einem Fehler bei der Bereitstellung.

- Für die **CLUSTER_PLATFORM**-Umgebungsvariablen gibt es keinen Standardwert mehr wie bei früheren Releases.

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warnereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch eine erfolgreiche Bereitstellung des Big-Data-Clusters in AKS nicht verhindern.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big-Data-Clusterbereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Dieses Problem kann umgangen werden, indem der Namespace vor der Bereitstellung eines Clusters mit dem gleichen Namen manuell gelöscht wird.

#### <a name="kubeadm-deployments"></a>Kubeadm-Bereitstellungen

Wenn Sie Kubeadm zum Bereitstellen von Kubernetes auf mehreren Computern verwenden, werden im Cluster-Verwaltungsportal die Endpunkte, die zum Herstellen einer Verbindung mit dem Big-Data-Cluster benötigt werden, nicht ordnungsgemäß angezeigt. Wenn dieses Problem auftritt, verwenden Sie die folgende Problemumgehung, um die IP-Adressen des Dienstendpunkts zu ermitteln:

- Wenn Sie innerhalb des Clusters eine Verbindung herstellen, fragen Sie von Kubernetes die IP-Adresse des Dienstendpunkts ab, mit dem Sie eine Verbindung herstellen möchten. Mit dem folgenden **kubectl**-Befehl wird beispielsweise die IP-Adresse der SQL Server-Masterinstanz angezeigt:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Wenn Sie von außerhalb des Clusters eine Verbindung herstellen, führen Sie zum Herstellen der Verbindung die folgenden Schritte aus:

   1. Rufen Sie die IP-Adresse des Knotens ab, auf dem die SQL Server-Masterinstanz ausgeführt wird: `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Stellen Sie mithilfe dieser IP-Adresse eine Verbindung mit der SQL Server-Masterinstanz her.

   1. Fragen Sie **cluster_endpoint_table** in der Masterdatenbank nach weiteren externen Endpunkten ab.

      Wenn diese Abfrage mit einem Verbindungstimeout fehlschlägt, wird der entsprechende Knoten möglicherweise durch eine Firewall geschützt. In diesem Fall müssen Sie sich an den Administrator des Kubernetes-Clusters wenden und nach der extern verfügbar gemachten IP-Adresse des Knotens fragen. Dies kann ein beliebiger Knoten sein. Anschließend können Sie diese IP-Adresse und den entsprechenden Port zum Herstellen einer Verbindung mit verschiedenen Diensten verwenden, die im Cluster ausgeführt werden. Der Administrator kann diese IP-Adresse beispielsweise ermitteln, indem er Folgendes ausführt:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="azdatactp23"></a> azdata

- Beim Tool **azdata** hat ein Wechsel von einer Verb-Nomen-Befehlsstruktur hin zu einer Nomen-Verb-Struktur stattgefunden. `azdata create cluster` lautet jetzt beispielsweise `azdata cluster create`.

- Zum Erstellen eines Clusters mit `azdata cluster create` ist jetzt der Parameter `--name` erforderlich.

   ```bash
   azdata cluster create --name <cluster_name>
   ```

- Wichtige Informationen zum Ausführen eines Upgrades auf die neueste Version von Big-Data-Clustern und **azdata** finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

#### <a name="external-tables"></a>Externe Tabellen

- Für eine Tabelle, die nicht unterstützte Spaltentypen aufweist, kann eine externe Datenpooltabelle erstellt werden. Wenn Sie die externe Tabelle abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle eines Speicherpools abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Daten vom Typ CHAR enthält, werden diese Spalten in der Definition der externen Tabelle vom Azure Data Studio-Virtualisierungsassistenten als VARCHAR interpretiert. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie manuell EXTERNAL TABLE-Anweisungen, und geben Sie NVARCHAR an, statt den Assistenten zu verwenden.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie über die RESTful-API eine R-, Python- oder MLeap-Anwendung aufrufen, tritt beim Aufruf nach 5 Minuten eine Zeitüberschreitung auf.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. Wenn der Masterpod neu gestartet wird, schlägt die Spark-Sitzung möglicherweise mit `NoRoteToHostException` fehl. Ursache hierfür sind JVM-Caches, die nicht mit den neuen IP-Adressen aktualisiert werden.

- Wenn Sie Jupyter bereits installiert haben und getrennt davon Python unter Windows verwenden, tritt bei Spark-Notebooks möglicherweise ein Fehler auf. Dieses Problem können Sie umgehen, indem Sie für Jupyter ein Upgrade auf die neueste Version ausführen.

- Wenn Sie bei einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle nicht im Bearbeitungsmodus, sondern im Vorschaumodus hinzugefügt. Sie können auf das Vorschausymbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, mit denen Änderungen an „hdfs-site.xml“ einhergehen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD-Variable ist Teil der Umgebung und kann erkannt werden (z. B. in einer CORD-Sicherungsdatei). Nach der Bereitstellung müssen Sie die SA_PASSWORD-Variable in der Masterinstanz zurücksetzen. Das ist kein Fehler, sondern eine Sicherheitsmaßnahme. Weitere Informationen zum Ändern der SA_PASSWORD-Variablen in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle enthalten möglicherweise ein Systemadministratorkennwort für Big-Data-Clusterbereitstellungen.

## <a id="ctp22"></a> CTP 2.2 (Dezember 2018)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 2.2 beschrieben.

### <a name="new-features"></a>Neue Funktionen

- Auf das Cluster-Verwaltungsportal wird mit `/portal` zugegriffen (**https://\<ip-address\>:30777/portal**).
- Der Name des Masterpooldiensts wurde von `service-master-pool-lb` und `service-master-pool-nodeport` in `endpoint-master-pool` geändert.
- Neue Version von **azdata** und aktualisierte Images.
- Verschiedene Fehlerbehebungen und Verbesserungen.

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in diesem Release beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big-Data-Datenclusters von einem vorherigen Release wird nicht unterstützt. Sie müssen alle vorhandenen Big-Data-Cluster sichern und löschen, bevor Sie das neueste Release bereitstellen. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warnereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch eine erfolgreiche Bereitstellung des Big-Data-Clusters in AKS nicht verhindern.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big-Data-Clusterbereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Dieses Problem kann umgangen werden, indem der Namespace vor der Bereitstellung eines Clusters mit dem gleichen Namen manuell gelöscht wird.

#### <a name="cluster-administration-portal"></a>Cluster-Verwaltungsportal

Im Cluster-Verwaltungsportal wird der Endpunkt für die SQL Server-Masterinstanz nicht angezeigt. Verwenden Sie den folgenden **kubectl**-Befehl, um die IP-Adresse und den Port für die Masterinstanz zu ermitteln:

```
kubectl get svc endpoint-master-pool -n <your-big-data-cluster-name>
```

#### <a name="external-tables"></a>Externe Tabellen

- Für eine Tabelle, die nicht unterstützte Spaltentypen aufweist, kann eine externe Datenpooltabelle erstellt werden. Wenn Sie die externe Tabelle abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle eines Speicherpools abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. Wenn der Masterpod neu gestartet wird, schlägt die Spark-Sitzung möglicherweise mit `NoRoteToHostException` fehl. Ursache hierfür sind JVM-Caches, die nicht mit den neuen IP-Adressen aktualisiert werden.

- Wenn Sie Jupyter bereits installiert haben und getrennt davon Python unter Windows verwenden, tritt bei Spark-Notebooks möglicherweise ein Fehler auf. Dieses Problem können Sie umgehen, indem Sie für Jupyter ein Upgrade auf die neueste Version ausführen.

- Wenn Sie bei einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle nicht im Bearbeitungsmodus, sondern im Vorschaumodus hinzugefügt. Sie können auf das Vorschausymbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, mit denen Änderungen an „hdfs-site.xml“ einhergehen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD-Variable ist Teil der Umgebung und kann erkannt werden (z. B. in einer CORD-Sicherungsdatei). Nach der Bereitstellung müssen Sie die SA_PASSWORD-Variable in der Masterinstanz zurücksetzen. Das ist kein Fehler, sondern eine Sicherheitsmaßnahme. Weitere Informationen zum Ändern der SA_PASSWORD-Variablen in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle enthalten möglicherweise ein Systemadministratorkennwort für Big-Data-Clusterbereitstellungen.

## <a id="ctp21"></a> CTP 2.1 (November 2018)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 2.1 beschrieben.

### <a name="new-features"></a>Neue Funktionen

- [Bereitstellung von Python- und R-Apps](big-data-cluster-create-apps.md) in einem Big-Data-Cluster.
- Neue Version von **azdata** und aktualisierte Images. 
- Verschiedene Fehlerbehebungen und Verbesserungen.

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten finden Sie Informationen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] zu bekannten Problemen für in CTP 2,1.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big-Data-Datenclusters von einem vorherigen Release wird nicht unterstützt. Sie müssen alle vorhandenen Big-Data-Cluster sichern und löschen, bevor Sie das neueste Release bereitstellen. Weitere Informationen finden Sie unter [Upgrade auf ein neues Release](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warnereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch eine erfolgreiche Bereitstellung des Big-Data-Clusters in AKS nicht verhindern.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big-Data-Clusterbereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Dieses Problem kann umgangen werden, indem der Namespace vor der Bereitstellung eines Clusters mit dem gleichen Namen manuell gelöscht wird.

#### <a name="admin-portal"></a>Verwaltungsportal

- Wenn Sie [eine App mithilfe des Befehls „msqlctl-ctp“ erstellen](big-data-cluster-create-apps.md) und in einem SQL Server-Big-Data-Cluster bereitstellen, werden im Cluster-Verwaltungsportal die Pods angezeigt, in denen die Anwendung im Abschnitt „Controller“ des Verwaltungsteils als „unbekannt“ bereitgestellt wurden.

#### <a name="external-tables"></a>Externe Tabellen

- Für eine Tabelle, die nicht unterstützte Spaltentypen aufweist, kann eine externe Datenpooltabelle erstellt werden. Wenn Sie die externe Tabelle abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle eines Speicherpools abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. Wenn der Masterpod neu gestartet wird, schlägt die Spark-Sitzung möglicherweise mit `NoRoteToHostException` fehl. Ursache hierfür sind JVM-Caches, die nicht mit den neuen IP-Adressen aktualisiert werden.

- Wenn Sie Jupyter bereits installiert haben und getrennt davon Python unter Windows verwenden, tritt bei Spark-Notebooks möglicherweise ein Fehler auf. Dieses Problem können Sie umgehen, indem Sie für Jupyter ein Upgrade auf die neueste Version ausführen.

- Wenn Sie bei einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle nicht im Bearbeitungsmodus, sondern im Vorschaumodus hinzugefügt. Sie können auf das Vorschausymbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, mit denen Änderungen an „hdfs-site.xml“ einhergehen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD-Variable ist Teil der Umgebung und kann erkannt werden (z. B. in einer CORD-Sicherungsdatei). Nach der Bereitstellung müssen Sie die SA_PASSWORD-Variable in der Masterinstanz zurücksetzen. Das ist kein Fehler, sondern eine Sicherheitsmaßnahme. Weitere Informationen zum Ändern der SA_PASSWORD-Variablen in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle enthalten möglicherweise ein Systemadministratorkennwort für Big-Data-Clusterbereitstellungen.

## <a id="ctp20"></a> CTP 2.0 (Oktober 2018)

In den folgenden Abschnitten werden die neuen Funktionen und bekannten Probleme von Big-Data-Clustern in SQL Server 2019 CTP 2.0 beschrieben.

### <a name="new-features"></a>Neue Funktionen

- Einfache Bereitstellung dank dem Verwaltungstool azdata
- Native Notebookumgebung in Azure Data Studio
- Abfragen von HDFS-Dateien über die Speicherinstanz von SQL Server
- Datenvirtualisierung über den Master für SQL Server, Oracle, MongoDB und HDFS
- Datenvirtualisierungs-Assistent für SQL Server und Oracle in Azure Data Studio
- ML-Dienste auf dem Master
- Cluster-Verwaltungsportal, das für die Überwachung und Problembehandlung verwendet werden kann
- Übermittlung von Spark-Aufträgen in Azure Data Studio 
- Spark-Benutzeroberfläche im Cluster-Verwaltungsportal
- Volumebereitstellung in Speicherklassen
- Abfragen von Datenpools vom Master
- Anzeigen von Plänen für verteilte Abfragen in SSMS
- PIP-Paket für das Verwaltungstool azdata
- Integrierte Bereitstellungs-Engine über den Controllerdienst

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten finden Sie Informationen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] zu bekannten Problemen für in CTP 2,0.

#### <a name="deployment"></a>Bereitstellung

- Für die Verwendung von Azure Kubernetes Service (AKS) wird die Kubernetes-Version 1.10.* empfohlen, die eine Größenänderung von Datenträgern nicht unterstützt. Stellen Sie sicher, dass Sie die Größe des Speichers zum Zeitpunkt der Bereitstellung entsprechend anpassen. Weitere Informationen zum Anpassen der Speichergröße finden Sie im Artikel zur [Datenpersistenz](concept-data-persistence.md). Für die Bereitstellung auf VMs wird die Kubernetes-Version 1.11 empfohlen.

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warnereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch eine erfolgreiche Bereitstellung des Big-Data-Clusters in AKS nicht verhindern.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big-Data-Clusterbereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Dieses Problem kann umgangen werden, indem der Namespace vor der Bereitstellung eines Clusters mit dem gleichen Namen manuell gelöscht wird.

#### <a name="external-tables"></a>Externe Tabellen

- Für eine Tabelle, die nicht unterstützte Spaltentypen aufweist, kann eine externe Datenpooltabelle erstellt werden. Wenn Sie die externe Tabelle abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle eines Speicherpools abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. Wenn der Masterpod neu gestartet wird, schlägt die Spark-Sitzung möglicherweise mit `NoRoteToHostException` fehl. Ursache hierfür sind JVM-Caches, die nicht mit den neuen IP-Adressen aktualisiert werden.

- Wenn Sie Jupyter bereits installiert haben und getrennt davon Python unter Windows verwenden, tritt bei Spark-Notebooks möglicherweise ein Fehler auf. Dieses Problem können Sie umgehen, indem Sie für Jupyter ein Upgrade auf die neueste Version ausführen.

- Wenn Sie bei einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle nicht im Bearbeitungsmodus, sondern im Vorschaumodus hinzugefügt. Sie können auf das Vorschausymbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, mit denen Änderungen an „hdfs-site.xml“ einhergehen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Die SA_PASSWORD-Variable ist Teil der Umgebung und kann erkannt werden (z. B. in einer CORD-Sicherungsdatei). Nach der Bereitstellung müssen Sie die SA_PASSWORD-Variable in der Masterinstanz zurücksetzen. Das ist kein Fehler, sondern eine Sicherheitsmaßnahme. Weitere Informationen zum Ändern der SA_PASSWORD-Variablen in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle enthalten möglicherweise ein Systemadministratorkennwort für Big-Data-Clusterbereitstellungen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]finden Sie unter [was [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]ist?](big-data-cluster-overview.md).
