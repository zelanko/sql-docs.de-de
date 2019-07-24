---
title: Versionshinweise
titleSuffix: SQL Server big data clusters
description: In diesem Artikel werden die neuesten Updates und bekannten Probleme bei SQL Server 2019 Big Data Clustern (Vorschau) beschrieben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c0dd96d4a3227fda76921764429b4566e3e5dd28
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419302"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>Anmerkungen zu dieser Version für Big Data Cluster auf SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel werden die Updates und Probleme für die neuesten Versionen von SQL Server Big Data Clustern aufgeführt.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp32"></a>CTP 3,2 (Juli)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 3,2 beschrieben.

|Neue Funktion oder Update | Details |
|:---|:---|
|Öffentliche Vorschau |Vor CTP 3,2 war SQL Server Big Data-Cluster für registrierte Early Adopters verfügbar. Diese Version ermöglicht es allen Benutzern, die Funktionen von SQL Server Big Data-Clustern zu erleben. <br/><br/> Weitere Informationen finden [Sie unter Get Started with SQL Server Big Data Clusters](deploy-get-started.md).|
|`azdata` |CTP 3,2 führt `azdata` ein in Python geschriebenes Befehlszeilen-Hilfsprogramm ein, mit dem Cluster Administratoren den Big Data Cluster über Rest-APIs Bootstrap und verwalten können. `azdata`ersetzt `mssqlctl`. Siehe [installieren `azdata` ](deploy-install-azdata.md). |
|PolyBase |Externe Tabellen Spaltennamen werden jetzt zum Abfragen von SQL Server-, Oracle-, Teradata-, MongoDB-und ODBC-Datenquellen verwendet. |
|HDFS-Tiering aktualisieren |Einführung in die Aktualisierungs Funktionalität für HDFS-Tiering, sodass eine vorhandene einreihenfolge für die aktuelle Momentaufnahme der Remote Daten aktualisiert werden kann. Siehe [HDFS-Tiering](hdfs-tiering.md) |
|Notebook-basierte Problembehandlung |Mit CTP 3,2 werden jupyter-Notebooks eingeführt, um die [Bereitstellung](deploy-notebooks.md) und [Ermittlung, Diagnose und Problem](manage-notebooks.md) Behandlung für Komponenten in einem SQL Server Big Data-Cluster zu unterstützen. |
| &nbsp; | &nbsp; |

## <a id="ctp31"></a>CTP 3,1 (Juni)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 3,1 beschrieben.

|Neue Funktion oder Update | Details |
|:---|:---|
|Öffentliche Vorschau |Vor CTP 3,2 war SQL Server Big Data-Cluster für registrierte Early Adopters verfügbar. Diese Version ermöglicht es allen Benutzern, die Funktionen von SQL Server Big Data-Clustern zu erleben. <br/><br/> Weitere Informationen finden [Sie unter Get Started with SQL Server Big Data Clusters](deploy-get-started.md).|
|Notebook basierte Problembehandlung.|Mit CTP 3,2 werden jupyter-Notebooks eingeführt, um die [Bereitstellung](deploy-notebooks.md), [Ermittlung, Diagnose und Problem](manage-notebooks.md) Behandlung von Komponenten in einem SQL Server Big Data-Cluster zu unterstützen. |
|`azdata` |CTP 3,2 führt `azdata` ein in Python geschriebenes Befehlszeilen-Hilfsprogramm ein, mit dem Cluster Administratoren den Big Data Cluster über Rest-APIs Bootstrap und verwalten können. `azdata`ersetzt `mssqlctl`. Siehe [installieren `azdata` ](deploy-install-azdata.md). |
|HDFS-Tiering aktualisieren |Einführung in die Aktualisierungs Funktionalität für HDFS-Tiering, sodass eine vorhandene einreihenfolge für die aktuelle Momentaufnahme der Remote Daten aktualisiert werden kann. Siehe [HDFS-Tiering](hdfs-tiering.md) |
| &nbsp; | &nbsp; |

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Änderungen am Befehl `mssqlctl` | Die `mssqlctl cluster`-Befehle wurden in `mssqlctl bdc` umbenannt. Weitere Informationen finden Sie in der [Referenz zu `mssqlctl`](reference-azdata.md). |
| Neue `mssqlctl` Status Befehle und Entfernen des Cluster Verwaltungs Portals. | Das Cluster Verwaltungs Portal wird in dieser Version entfernt. Neue Status Befehle wurden hinzugefügt `mssqlctl` , die vorhandene Überwachungs Befehle ergänzen. |
| Spark-Computepools | Erstellen Sie zusätzliche Knoten, um die Spark-Rechenleistung zu erhöhen, ohne den Speicher zentral hochskalieren zu müssen. Zudem können Sie Speicherpoolknoten starten, die nicht für Spark verwendet werden. Spark wird vom Speicher entkoppelt. Weitere Informationen finden Sie unter [Configure storage without spark (Konfigurieren des Speichers ohne Spark)](deployment-custom-configuration.md#sparkstorage). |
| MSSQL-Spark-Connector | Ab jetzt werden Lese- und Schreibvorgänge in externen Datenpooltabellen unterstützt. In vorherigen Releases wurden Lese- und Schreibvorgänge nur für Tabellen der MASTER-Instanz unterstützt. Weitere Informationen finden Sie unter [How to read and write to SQL Server from Spark using the MSSQL Spark Connector (Lesen und Schreiben in SQL Server über Spark mithilfe des MSSQL-Spark-Connectors)](spark-mssql-connector.md). |
| Machine Learning mit MLeap | [Trainieren Sie ein MLeap-Machine-Learning-Modell in Spark, und bewerten Sie es mit der Java-Spracherweiterung in SQL Server.](spark-create-machine-learning-model.md) |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in dieser Version beschrieben.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise der folgende Fehler angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, die Änderungen an "HDFS-Site. XML einschließen, werden nicht unterstützt.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big Data-Daten Clusters von einer vorherigen Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie die neueste Version bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big Data Cluster (unter Verwendung der früheren Version von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf eine neue Version](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warn Ereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch nicht verhindern, dass Sie die Big Data Cluster in AKS erfolgreich bereitstellen.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big Data Cluster Bereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Eine Problem Umgehung besteht darin, den Namespace manuell zu löschen, bevor Sie einen Cluster mit dem gleichen Namen bereitstellen.

#### <a name="external-tables"></a>Externe Tabellen

- Die Big Data-Cluster Bereitstellung erstellt nicht mehr die externen Datenquellen **sqldatapool** und **sqlstoragepool** . Sie können diese Datenquellen manuell erstellen, um die Datenvirtualisierung für den Daten Pool und den Speicherpool zu unterstützen.

   > [!NOTE]
   > Der URI zum Erstellen dieser externen Datenquellen unterscheidet sich zwischen CTPs. Sehen Sie sich die folgenden Transact-SQL-Befehle an, um zu erfahren, wie Sie diese erstellen. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Es ist möglich, eine externe Daten Pool Tabelle für eine Tabelle zu erstellen, die nicht unterstützte Spaltentypen aufweist. Wenn Sie die externe Tabelle Abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle für einen Speicherpool Abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Zeichen Datentypen verwendet, interpretiert der Azure Data Studio virtualisierungsassistent diese Spalten in der Definition der externen Tabelle als varchar. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie externe Tabellen Anweisungen manuell, und geben Sie nvarchar anstelle des Assistenten an.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie eine R-, Python-oder mleap-Anwendung von der Rest-API aufrufen, wird der Aufruf in 5 Minuten als Timeout bezeichnet.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. In dem Szenario, in dem das Master-Pod neu gestartet wird, schlägt die Spark `NoRoteToHostException`-Sitzung möglicherweise mit fehl. Dies wird durch JVM-Caches verursacht, die nicht mit neuen IP-Adressen aktualisiert werden.

- Wenn Sie jupyter bereits installiert haben und ein separates python unter Windows, können Spark-Notebooks fehlschlagen. Um dieses Problem zu umgehen, führen Sie ein Upgrade von jupyter auf die neueste Version durch.

- Wenn Sie in einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle im Vorschaumodus anstatt im Bearbeitungsmodus hinzugefügt. Sie können auf das Vorschau Symbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="security"></a>Sicherheit

- Der SA_PASSWORD ist Teil der Umgebung und ermittelbar (z. b. in einer Dump-Dumpdatei). Sie müssen die SA_PASSWORD auf der Master Instanz nach der Bereitstellung zurücksetzen. Dabei handelt es sich nicht um einen Fehler, sondern um einen Sicherheits Schritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

- AKS-Protokolle können ein SA-Kennwort für Big Data Cluster Bereitstellungen enthalten.

#### <a name="kibana-logs-dashboards"></a>Kibana protokolliert Dashboards

- Zwischen ARIS CTP 3,0 und 3,1 wurde die kibana-Version von 6.3.1 auf 7.0.1 aktualisiert.  Dadurch ist der Edge-Browser mit kibana nicht kompatibel. Benutzern wird beim Laden der aktuellen Version der kibana-Dashboards in Edge eine leere Seite angezeigt. Weitere [Informationen finden Sie]( https://www.elastic.co/support/matrix#matrix_browse) unter Unterstützte Browser für Kibana.RS 


## <a id="ctp30"></a>CTP 3,0 (Mai)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 3,0 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| **mssqlctl**-Updates | Mehrere [Updates für den Befehl **mssqlctl** und seine Parameter](reference-azdata.md). Dies umfasst ein Update für den Befehl **mssqlctl login**, der nun den Controllerbenutzernamen und -endpunkt zum Ziel hat. |
| Speichererweiterungen | Unterstützung für verschiedene Speicherkonfigurationen für Protokolle und Daten. Darüber hinaus wurde die Anzahl der Ansprüche von persistentem Volume für einen Big Data-Cluster gesenkt. |
| Mehrere Computepoolinstanzen | Unterstützung für mehrere Computepoolinstanzen. |
| Neues Poolverhalten und neue Poolfunktionen | Der Computepool wird jetzt standardmäßig für Speicherpool- und Datenpoolvorgänge ausschließlich in einer **ROUND_ROBIN**-Verteilung verwendet. Der Datenpool kann nun einen neuen Verteilungstyp **REPLICATED** verwenden, was bedeutet, dass dieselben Daten in allen Datenpoolinstanzen vorhanden sind. |
| Verbesserungen externer Tabellen | Externe Tabellen des HADOOP-Datenquellentyps unterstützen nun das Lesen von Zeilen mit einer Größe von bis zu 1 MB. Externe Tabellen (ODBC, Speicherpool, Datenpool) unterstützen jetzt Zeilen mit der Breite einer SQL Server-Tabelle. |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in dieser Version beschrieben.

#### <a name="hdfs"></a>HDFS

- Azure Data Studio gibt einen Fehler zurück, wenn Sie versuchen, einen neuen Ordner in HDFS zu erstellen. Um diese Funktionalität zu aktivieren, installieren Sie den Insider-Build Azure Data Studio:
  
   - [Windows-benutzerinstaller: **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-user/insider)
   - [Windows-System Installationsprogramm: **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64/insider)
   - [Windows Zip- **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-archive/insider)
   - [macOS-Zip- **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/darwin/insider)
   - [Linux-tar. GZ- **Insider-Build**](https://azuredatastudio-update.azurewebsites.net/latest/linux-x64/insider)

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise der folgende Fehler angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, die Änderungen an "HDFS-Site. XML einschließen, werden nicht unterstützt.

#### <a name="deployment"></a>Bereitstellung

- Die vorherigen Bereitstellungs Prozeduren für GPU-fähige Big Data-Cluster werden in CTP 3,0 nicht unterstützt. Ein alternatives Bereitstellungs Verfahren wird untersucht. Der Artikel "Bereitstellen eines Big Data Clusters mit GPU-Unterstützung und Ausführen von tensorflow" wurde vorläufig aufgehoben, um Verwechslungen zu vermeiden.

- Das Upgrade eines Big Data-Daten Clusters von einer vorherigen Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie die neueste Version bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big Data Cluster (unter Verwendung der früheren Version von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf eine neue Version](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warn Ereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch nicht verhindern, dass Sie die Big Data Cluster in AKS erfolgreich bereitstellen.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big Data Cluster Bereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Eine Problem Umgehung besteht darin, den Namespace manuell zu löschen, bevor Sie einen Cluster mit dem gleichen Namen bereitstellen.

#### <a name="external-tables"></a>Externe Tabellen

- Die Big Data-Cluster Bereitstellung erstellt nicht mehr die externen Datenquellen **sqldatapool** und **sqlstoragepool** . Sie können diese Datenquellen manuell erstellen, um die Datenvirtualisierung für den Daten Pool und den Speicherpool zu unterstützen.

   > [!NOTE]
   > Der URI zum Erstellen dieser externen Datenquellen unterscheidet sich zwischen CTPs. Sehen Sie sich die folgenden Transact-SQL-Befehle an, um zu erfahren, wie Sie diese erstellen. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Es ist möglich, eine externe Daten Pool Tabelle für eine Tabelle zu erstellen, die nicht unterstützte Spaltentypen aufweist. Wenn Sie die externe Tabelle Abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle für einen Speicherpool Abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Zeichen Datentypen verwendet, interpretiert der Azure Data Studio virtualisierungsassistent diese Spalten in der Definition der externen Tabelle als varchar. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie externe Tabellen Anweisungen manuell, und geben Sie nvarchar anstelle des Assistenten an.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie eine R-, Python-oder mleap-Anwendung von der Rest-API aufrufen, wird der Aufruf in 5 Minuten als Timeout bezeichnet.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. In dem Szenario, in dem das Master-Pod neu gestartet wird, schlägt die Spark `NoRoteToHostException`-Sitzung möglicherweise mit fehl. Dies wird durch JVM-Caches verursacht, die nicht mit neuen IP-Adressen aktualisiert werden.

- Wenn Sie jupyter bereits installiert haben und ein separates python unter Windows, können Spark-Notebooks fehlschlagen. Um dieses Problem zu umgehen, führen Sie ein Upgrade von jupyter auf die neueste Version durch.

- Wenn Sie in einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle im Vorschaumodus anstatt im Bearbeitungsmodus hinzugefügt. Sie können auf das Vorschau Symbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="security"></a>Sicherheit

- Der SA_PASSWORD ist Teil der Umgebung und ermittelbar (z. b. in einer Dump-Dumpdatei). Sie müssen die SA_PASSWORD auf der Master Instanz nach der Bereitstellung zurücksetzen. Dabei handelt es sich nicht um einen Fehler, sondern um einen Sicherheits Schritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

- AKS-Protokolle können ein SA-Kennwort für Big Data Cluster Bereitstellungen enthalten.

## <a id="ctp25"></a>CTP 2,5 (April)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 2,5 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Bereitstellungsprofile | Verwenden Sie für die Bereitstellung von Big Data-Clustern standardmäßige und benutzerdefinierte [Konfigurationsdateien für die JSON-Bereitstellung](deployment-guidance.md#configfile) anstelle von Umgebungsvariablen. |
| Bereitstellungen mit Aufforderung | `azdata cluster create` ruft jetzt zu allen erforderlichen Einstellungen für Standardbereitstellungen auf. |
| Änderungen bei Dienstendpunkten und Podnamen | Die Namen der folgenden externen Endpunkte haben sich geändert:<br/>&nbsp;&nbsp;&nbsp;- **endpoint-master-pool** => **master-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **Endpunkt Controller** => **Controller-SVC-extern**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-service-proxy** => **mgmtproxy-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **Endpoint-Security** => -**Gateway-SVC-extern**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-app-service-proxy** => **appproxy-svc-external**|
| Weitere **azdata** | Verwenden Sie **azdata** , um [externe Endpunkte aufzulisten](deployment-guidance.md#endpoints) , und überprüfen Sie die Version `--version` von **azdata** mit dem-Parameter. |
| Offlineinstallation | Leitfaden für Offline-Big Data-Cluster Bereitstellungen. |
| Verbesserungen bei HDFS-Tiering | S3-Tiering, einstellungscaching und OAuth-Unterstützung für ADLS Gen2. |
| Neuer `mssql` Spark-SQL Server-Connector | |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in dieser Version beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big Data-Daten Clusters von einer vorherigen Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie die neueste Version bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big Data Cluster (unter Verwendung der früheren Version von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf eine neue Version](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warn Ereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch nicht verhindern, dass Sie die Big Data Cluster in AKS erfolgreich bereitstellen.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big Data Cluster Bereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Eine Problem Umgehung besteht darin, den Namespace manuell zu löschen, bevor Sie einen Cluster mit dem gleichen Namen bereitstellen.

#### <a name="external-tables"></a>Externe Tabellen

- Die Big Data-Cluster Bereitstellung erstellt nicht mehr die externen Datenquellen **sqldatapool** und **sqlstoragepool** . Sie können diese Datenquellen manuell erstellen, um die Datenvirtualisierung für den Daten Pool und den Speicherpool zu unterstützen.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://nmnode-0-svc:50070');
   ```

- Es ist möglich, eine externe Daten Pool Tabelle für eine Tabelle zu erstellen, die nicht unterstützte Spaltentypen aufweist. Wenn Sie die externe Tabelle Abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle für einen Speicherpool Abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Zeichen Datentypen verwendet, interpretiert der Azure Data Studio virtualisierungsassistent diese Spalten in der Definition der externen Tabelle als varchar. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie externe Tabellen Anweisungen manuell, und geben Sie nvarchar anstelle des Assistenten an.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie eine R-, Python-oder mleap-Anwendung von der Rest-API aufrufen, wird der Aufruf in 5 Minuten als Timeout bezeichnet.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. In dem Szenario, in dem das Master-Pod neu gestartet wird, schlägt die Spark `NoRoteToHostException`-Sitzung möglicherweise mit fehl. Dies wird durch JVM-Caches verursacht, die nicht mit neuen IP-Adressen aktualisiert werden.

- Wenn Sie jupyter bereits installiert haben und ein separates python unter Windows, können Spark-Notebooks fehlschlagen. Um dieses Problem zu umgehen, führen Sie ein Upgrade von jupyter auf die neueste Version durch.

- Wenn Sie in einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle im Vorschaumodus anstatt im Bearbeitungsmodus hinzugefügt. Sie können auf das Vorschau Symbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise der folgende Fehler angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, die Änderungen an "HDFS-Site. XML einschließen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Der SA_PASSWORD ist Teil der Umgebung und ermittelbar (z. b. in einer Dump-Dumpdatei). Sie müssen die SA_PASSWORD auf der Master Instanz nach der Bereitstellung zurücksetzen. Dabei handelt es sich nicht um einen Fehler, sondern um einen Sicherheits Schritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

- AKS-Protokolle können ein SA-Kennwort für Big Data Cluster Bereitstellungen enthalten.

## <a id="ctp24"></a>CTP 2,4 (März)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 2,4 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
|:---|:---|
| Anleitung für die GPU-Unterstützung zum Ausführen von Deep Learning mit TensorFlow in Spark | Weitere Informationen finden Sie unter [Deploy a big data cluster with GPU support and run TensorFlow (Bereitstellen eines Big Data-Clusters mit GPU-Unterstützung und Ausführen von TensorFlow)](spark-gpu-tensorflow.md). |
| Die Datenquellen **SqlDataPool** und **SqlStoragePool** werden nicht mehr standardmäßig erstellt. | Erstellen Sie diese nach Bedarf manuell. Weitere Informationen finden Sie im Abschnitt [Bekannte Probleme](#externaltablesctp24). |
| Unterstützung von `INSERT INTO SELECT` für den Datenpool | Ein Beispiel finden Sie unter [Tutorial: Ingest data into a SQL Server data pool with Transact-SQL (Tutorial: Erfassen von Daten in einem SQL Server-Datenpool mit Transact-SQL)](tutorial-data-pool-ingest-sql.md). |
| Optionen `FORCE SCALEOUTEXECUTION` und `DISABLE SCALEOUTEXECUTION` | Erzwingt oder deaktiviert die Verwendung des computepools für Abfragen für externe Tabellen. Beispiel: `SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)`Hyper-V-Hosts oder Hyper-V-Hostcluster in einem separaten Namespace als verwaltete Hyper-V-Hosts hinzuzufügen. |
| Aktualisierte Bereitstellungsempfehlungen für AKS | Für die Auswertung von Big Data-Clustern in AKS wird die Verwendung eines einzelnen Knotens der Größe **Standard_L8s** empfohlen. |
| Upgrade der Spark-Runtime auf Spark 2.4 | |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in dieser Version beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big Data-Daten Clusters von einer vorherigen Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie die neueste Version bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big Data Cluster (unter Verwendung der früheren Version von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf eine neue Version](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warn Ereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch nicht verhindern, dass Sie die Big Data Cluster in AKS erfolgreich bereitstellen.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big Data Cluster Bereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Eine Problem Umgehung besteht darin, den Namespace manuell zu löschen, bevor Sie einen Cluster mit dem gleichen Namen bereitstellen.

#### <a name="kubeadm-deployments"></a>kubeadm-bereit Stellungen

Wenn Sie kubeadm verwenden, um Kubernetes auf mehreren Computern bereitzustellen, werden im Cluster Verwaltungs Portal die Endpunkte, die zum Herstellen einer Verbindung mit dem Big Data Cluster benötigt werden, nicht ordnungsgemäß angezeigt. Wenn dieses Problem auftritt, verwenden Sie die folgende Problem Umgehung, um die IP-Adressen des Dienst Endpunkts zu ermitteln:

- Wenn Sie innerhalb des Clusters eine Verbindung herstellen, Fragen Sie Kubernetes nach der Dienst-IP-Adresse für den Endpunkt ab, mit dem Sie eine Verbindung herstellen möchten. Der folgende **kubectl** -Befehl zeigt z. b. die IP-Adresse der SQL Server Master Instanz an:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Wenn Sie von außerhalb des Clusters eine Verbindung herstellen, führen Sie die folgenden Schritte aus, um eine Verbindung herzustellen:

   1. Erhalten Sie die IP-Adresse des Knotens, auf dem die `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`SQL Server Master Instanz ausgeführt wird:.

   1. Stellen Sie mithilfe dieser IP-Adresse eine Verbindung mit SQL Server Master Instanz her.

   1. Fragen Sie die **cluster_endpoint_table** in der Master-Datenbank nach anderen externen Endpunkten ab.

      Wenn dies mit einem Verbindungs Timeout fehlschlägt, ist es möglich, dass der jeweilige Knoten firewallbasiert ist. In diesem Fall müssen Sie sich an Ihren Kubernetes-Cluster Administrator wenden und nach der Knoten-IP Fragen, die extern verfügbar gemacht wird. Dies kann ein beliebiger Knoten sein. Anschließend können Sie diese IP-Adresse und den entsprechenden Port zum Herstellen einer Verbindung mit verschiedenen Diensten verwenden, die im Cluster ausgeführt werden. Beispielsweise kann der Administrator diese IP-Adresse ermitteln, indem er Folgendes ausführen:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>Fehler beim Löschen des Clusters

Wenn Sie versuchen, einen Cluster mit **azdata**zu löschen, tritt der folgende Fehler auf:

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

Ein neuer python Kubernetes Client (Version 9.0.0) hat die Delete Namespaces-API geändert, die derzeit **azdata**unterbricht. Dies geschieht nur, wenn Sie einen neueren Kubernetes-Python-Client installiert haben. Sie können dieses Problem umgehen, indem Sie den Cluster mithilfe von **kubectl** (`kubectl delete ns <ClusterName>`) direkt löschen, oder Sie können die ältere Version `sudo pip install kubernetes==8.0.1`mithilfe von installieren.

#### <a id="externaltablesctp24"></a>Externe Tabellen

- Die Big Data-Cluster Bereitstellung erstellt nicht mehr die externen Datenquellen **sqldatapool** und **sqlstoragepool** . Sie können diese Datenquellen manuell erstellen, um die Datenvirtualisierung für den Daten Pool und den Speicherpool zu unterstützen.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   ```

- Es ist möglich, eine externe Daten Pool Tabelle für eine Tabelle zu erstellen, die nicht unterstützte Spaltentypen aufweist. Wenn Sie die externe Tabelle Abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle für einen Speicherpool Abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Zeichen Datentypen verwendet, interpretiert der Azure Data Studio virtualisierungsassistent diese Spalten in der Definition der externen Tabelle als varchar. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie externe Tabellen Anweisungen manuell, und geben Sie nvarchar anstelle des Assistenten an.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie eine R-, Python-oder mleap-Anwendung von der Rest-API aufrufen, wird der Aufruf in 5 Minuten als Timeout bezeichnet.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. In dem Szenario, in dem das Master-Pod neu gestartet wird, schlägt die Spark `NoRoteToHostException`-Sitzung möglicherweise mit fehl. Dies wird durch JVM-Caches verursacht, die nicht mit neuen IP-Adressen aktualisiert werden.

- Wenn Sie jupyter bereits installiert haben und ein separates python unter Windows, können Spark-Notebooks fehlschlagen. Um dieses Problem zu umgehen, führen Sie ein Upgrade von jupyter auf die neueste Version durch.

- Wenn Sie in einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle im Vorschaumodus anstatt im Bearbeitungsmodus hinzugefügt. Sie können auf das Vorschau Symbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise der folgende Fehler angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, die Änderungen an "HDFS-Site. XML einschließen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Der SA_PASSWORD ist Teil der Umgebung und ermittelbar (z. b. in einer Dump-Dumpdatei). Sie müssen die SA_PASSWORD auf der Master Instanz nach der Bereitstellung zurücksetzen. Dabei handelt es sich nicht um einen Fehler, sondern um einen Sicherheits Schritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

- AKS-Protokolle können ein SA-Kennwort für Big Data Cluster Bereitstellungen enthalten.

## <a id="ctp23"></a>CTP 2,3 (Februar)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 2,3 beschrieben.

### <a name="whats-new"></a>Neues

| Neue Funktion oder Update | Details |
| :---------- | :------ |
| Übermitteln von Spark-Aufträgen an Big Data-Cluster in IntelliJ | [Submit Spark jobs on SQL Server big data clusters in IntelliJ (Übermitteln von Spark-Aufträgen an Big Data-Cluster von SQL Server in IntelliJ)](spark-submit-job-intellij-tool-plugin.md) |
| Allgemeine CLI für die Anwendungsbereitstellung und Clusterverwaltung | [How to deploy an app on SQL Server 2019 big data cluster (preview) (Vorgehensweise: Bereitstellen einer App in Big Data-Clustern von SQL Server 2019 (Vorschau))](big-data-cluster-create-apps.md) |
| VS Code-Erweiterung zum Bereitstellen von Anwendungen in einem Big Data-Cluster | [How to use VS Code to deploy applications to SQL Server big data clusters (Vorgehensweise: Verwenden von VS Code zum Bereitstellen von Anwendungen in Big Data-Clustern von SQL Server)](app-deployment-extension.md) |
| Änderungen an der Befehls Verwendung des **azdata** -Tools. | Weitere Informationen finden Sie unter [bekannte Probleme für azdata](#azdatactp23). |
| Verwenden von sparklyr in Big Data Cluster | [Use Sparklyr in SQL Server 2019 big data cluster (Verwenden von Sparklyr in Big Data-Clustern von SQL Server 2019)](sparklyr-from-RStudio.md) |
| Einbinden von externen HDFS-kompatiblen Speichern (Hadoop Distributed File System) in Big Data-Clustern mit dem **HDFS-Tiering** | Weitere Informationen finden Sie unter [HDFS-Tiering](hdfs-tiering.md). |
| Neue einheitliche Verbindungsoberfläche für die SQL Server-Masterinstanz und das HDFS-/Spark-Gateway | Weitere Informationen finden Sie unter [SQL Server master instance and the HDFS/Spark Gateway (Die SQL Server-Masterinstanz und das HDFS-/Spark-Gateway)](connect-to-big-data-cluster.md). |
| Beim Löschen eines Clusters mit **azdata Cluster DELETE** werden jetzt nur die Objekte im Namespace gelöscht, die Teil des Big Data Clusters waren. | Der Namespace wird nicht gelöscht. In früheren Releases wurde mit diesem Befehl jedoch nicht der gesamte Namespace gelöscht. |
| Namen von _Sicherheitsendpunkten_ wurden geändert und zusammengefasst | **service-security-lb** und **service-security-nodeport** wurden im Endpunkt **endpoint-security** zusammengefasst. |
| Namen von _Proxyendpunkten_ wurden geändert und zusammengefasst | **service-proxy-lb** und **service-proxy-nodeport** wurden im Endpunkt **endpoint-service-proxy** zusammengefasst. |
| Namen von _Controllerendpunkten_ wurden geändert und zusammengefasst | **service-mssql-controller-lb** und **service-mssql-controller-nodeport** wurden im Endpunkt **endpoint-controller** zusammengefasst. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in dieser Version beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big Data-Daten Clusters von einer vorherigen Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Bevor Sie die neueste Version bereitstellen, müssen Sie die Daten sichern und dann den vorhandenen Big Data Cluster (unter Verwendung der früheren Version von **azdata**) löschen. Weitere Informationen finden Sie unter [Upgrade auf eine neue Version](deployment-upgrade.md).

- Die **ACCEPT_EULA** -Umgebungsvariable muss "yes" oder "yes" lauten, um die Lizenzbedingungen zu akzeptieren. Frühere Releases erlaubten "y" und "y", diese werden jedoch nicht mehr akzeptiert und führen zu einem Fehler bei der Bereitstellung.

- Die Umgebungsvariablen **CLUSTER_PLATFORM** haben keinen Standardwert wie in vorherigen Versionen.

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warn Ereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch nicht verhindern, dass Sie die Big Data Cluster in AKS erfolgreich bereitstellen.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big Data Cluster Bereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Eine Problem Umgehung besteht darin, den Namespace manuell zu löschen, bevor Sie einen Cluster mit dem gleichen Namen bereitstellen.

#### <a name="kubeadm-deployments"></a>kubeadm-bereit Stellungen

Wenn Sie kubeadm verwenden, um Kubernetes auf mehreren Computern bereitzustellen, werden im Cluster Verwaltungs Portal die Endpunkte, die zum Herstellen einer Verbindung mit dem Big Data Cluster benötigt werden, nicht ordnungsgemäß angezeigt. Wenn dieses Problem auftritt, verwenden Sie die folgende Problem Umgehung, um die IP-Adressen des Dienst Endpunkts zu ermitteln:

- Wenn Sie innerhalb des Clusters eine Verbindung herstellen, Fragen Sie Kubernetes nach der Dienst-IP-Adresse für den Endpunkt ab, mit dem Sie eine Verbindung herstellen möchten. Der folgende **kubectl** -Befehl zeigt z. b. die IP-Adresse der SQL Server Master Instanz an:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Wenn Sie von außerhalb des Clusters eine Verbindung herstellen, führen Sie die folgenden Schritte aus, um eine Verbindung herzustellen:

   1. Erhalten Sie die IP-Adresse des Knotens, auf dem die `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`SQL Server Master Instanz ausgeführt wird:.

   1. Stellen Sie mithilfe dieser IP-Adresse eine Verbindung mit SQL Server Master Instanz her.

   1. Fragen Sie die **cluster_endpoint_table** in der Master-Datenbank nach anderen externen Endpunkten ab.

      Wenn dies mit einem Verbindungs Timeout fehlschlägt, ist es möglich, dass der jeweilige Knoten firewallbasiert ist. In diesem Fall müssen Sie sich an Ihren Kubernetes-Cluster Administrator wenden und nach der Knoten-IP Fragen, die extern verfügbar gemacht wird. Dies kann ein beliebiger Knoten sein. Anschließend können Sie diese IP-Adresse und den entsprechenden Port zum Herstellen einer Verbindung mit verschiedenen Diensten verwenden, die im Cluster ausgeführt werden. Beispielsweise kann der Administrator diese IP-Adresse ermitteln, indem er Folgendes ausführen:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="azdatactp23"></a>azdata

- Das Tool **azdata** hat sich von einer Verb-Substantiv-Befehls Sortierung in eine Substantiv-Verb-Reihenfolge geändert. Beispielsweise `azdata create cluster` ist jetzt `azdata cluster create`.

- Der `--name` -Parameter ist jetzt erforderlich, wenn ein Cluster `azdata cluster create`mit erstellt wird.

   ```bash
   azdata cluster create --name <cluster_name>
   ```

- Wichtige Informationen zum Aktualisieren auf die neueste Version von Big Data Clustern und **azdata**finden Sie unter [Upgrade auf eine neue](deployment-upgrade.md)Version.

#### <a name="external-tables"></a>Externe Tabellen

- Es ist möglich, eine externe Daten Pool Tabelle für eine Tabelle zu erstellen, die nicht unterstützte Spaltentypen aufweist. Wenn Sie die externe Tabelle Abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle für einen Speicherpool Abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Wenn Sie eine externe Tabelle für Oracle erstellen, die Zeichen Datentypen verwendet, interpretiert der Azure Data Studio virtualisierungsassistent diese Spalten in der Definition der externen Tabelle als varchar. Dies führt zu einem Fehler in der DDL der externen Tabelle. Ändern Sie entweder das Oracle-Schema so, dass der NVARCHAR2-Typ verwendet wird, oder erstellen Sie externe Tabellen Anweisungen manuell, und geben Sie nvarchar anstelle des Assistenten an.

#### <a name="application-deployment"></a>Anwendungsbereitstellung

- Wenn Sie eine R-, Python-oder mleap-Anwendung von der Rest-API aufrufen, wird der Aufruf in 5 Minuten als Timeout bezeichnet.

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. In dem Szenario, in dem das Master-Pod neu gestartet wird, schlägt die Spark `NoRoteToHostException`-Sitzung möglicherweise mit fehl. Dies wird durch JVM-Caches verursacht, die nicht mit neuen IP-Adressen aktualisiert werden.

- Wenn Sie jupyter bereits installiert haben und ein separates python unter Windows, können Spark-Notebooks fehlschlagen. Um dieses Problem zu umgehen, führen Sie ein Upgrade von jupyter auf die neueste Version durch.

- Wenn Sie in einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle im Vorschaumodus anstatt im Bearbeitungsmodus hinzugefügt. Sie können auf das Vorschau Symbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise der folgende Fehler angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, die Änderungen an "HDFS-Site. XML einschließen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Der SA_PASSWORD ist Teil der Umgebung und ermittelbar (z. b. in einer Dump-Dumpdatei). Sie müssen die SA_PASSWORD auf der Master Instanz nach der Bereitstellung zurücksetzen. Dabei handelt es sich nicht um einen Fehler, sondern um einen Sicherheits Schritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

- AKS-Protokolle können ein SA-Kennwort für Big Data Cluster Bereitstellungen enthalten.

## <a id="ctp22"></a>CTP 2,2 (Dezember 2018)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 2,2 beschrieben.

### <a name="new-features"></a>Neue Funktionen

- Auf das Cluster Verwaltungs Portal `/portal` wird mit ( **\<https://IP\>-Address: 30777/Portal**) zugegriffen.
- Der Name des Master Pool Dienstanbieter `endpoint-master-pool`wurde von `service-master-pool-lb` und `service-master-pool-nodeport` in geändert.
- Neue Version von **azdata** und aktualisierte Images.
- Verschiedene Fehlerbehebungen und Verbesserungen.

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden die bekannten Probleme und Einschränkungen in dieser Version beschrieben.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big Data-Daten Clusters von einer vorherigen Version wird nicht unterstützt. Sie müssen alle vorhandenen Big Data Cluster sichern und löschen, bevor Sie die neueste Version bereitstellen. Weitere Informationen finden Sie unter [Upgrade auf eine neue Version](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warn Ereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch nicht verhindern, dass Sie die Big Data Cluster in AKS erfolgreich bereitstellen.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big Data Cluster Bereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Eine Problem Umgehung besteht darin, den Namespace manuell zu löschen, bevor Sie einen Cluster mit dem gleichen Namen bereitstellen.

#### <a name="cluster-administration-portal"></a>Cluster-Verwaltungsportal

Im Cluster Verwaltungs Portal wird der Endpunkt für die SQL Server Master Instanz nicht angezeigt. Verwenden Sie den folgenden **kubectl** -Befehl, um die IP-Adresse und den Port für die Master Instanz zu ermitteln:

```
kubectl get svc endpoint-master-pool -n <your-big-data-cluster-name>
```

#### <a name="external-tables"></a>Externe Tabellen

- Es ist möglich, eine externe Daten Pool Tabelle für eine Tabelle zu erstellen, die nicht unterstützte Spaltentypen aufweist. Wenn Sie die externe Tabelle Abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle für einen Speicherpool Abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. In dem Szenario, in dem das Master-Pod neu gestartet wird, schlägt die Spark `NoRoteToHostException`-Sitzung möglicherweise mit fehl. Dies wird durch JVM-Caches verursacht, die nicht mit neuen IP-Adressen aktualisiert werden.

- Wenn Sie jupyter bereits installiert haben und ein separates python unter Windows, können Spark-Notebooks fehlschlagen. Um dieses Problem zu umgehen, führen Sie ein Upgrade von jupyter auf die neueste Version durch.

- Wenn Sie in einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle im Vorschaumodus anstatt im Bearbeitungsmodus hinzugefügt. Sie können auf das Vorschau Symbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise der folgende Fehler angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, die Änderungen an "HDFS-Site. XML einschließen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Der SA_PASSWORD ist Teil der Umgebung und ermittelbar (z. b. in einer Dump-Dumpdatei). Sie müssen die SA_PASSWORD auf der Master Instanz nach der Bereitstellung zurücksetzen. Dabei handelt es sich nicht um einen Fehler, sondern um einen Sicherheits Schritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

- AKS-Protokolle können ein SA-Kennwort für Big Data Cluster Bereitstellungen enthalten.

## <a id="ctp21"></a>CTP 2,1 (November 2018)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 2,1 beschrieben.

### <a name="new-features"></a>Neue Funktionen

- Stellen Sie [python-und R-apps](big-data-cluster-create-apps.md) in einem Big Data Cluster bereit.
- Neue Version von **azdata** und aktualisierte Images. 
- Verschiedene Fehlerbehebungen und Verbesserungen.

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten finden Sie Informationen zu bekannten Problemen bei SQL Server Big Data Clustern in CTP 2,1.

#### <a name="deployment"></a>Bereitstellung

- Das Upgrade eines Big Data-Daten Clusters von einer vorherigen Version wird nicht unterstützt. Sie müssen alle vorhandenen Big Data Cluster sichern und löschen, bevor Sie die neueste Version bereitstellen. Weitere Informationen finden Sie unter [Upgrade auf eine neue Version](deployment-upgrade.md).

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warn Ereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch nicht verhindern, dass Sie die Big Data Cluster in AKS erfolgreich bereitstellen.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big Data Cluster Bereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Eine Problem Umgehung besteht darin, den Namespace manuell zu löschen, bevor Sie einen Cluster mit dem gleichen Namen bereitstellen.

#### <a name="admin-portal"></a>Verwaltungs Portal

- Wenn Sie [eine APP mit dem Befehl "msqlctl-CTP" erstellen](big-data-cluster-create-apps.md) und Sie auf einem SQL Server Big Data Cluster bereitstellen, zeigt das Cluster Verwaltungs Portal die Pods an, auf denen die Anwendung im Controller Abschnitt des Administrator Teils als "unbekannt" bereitgestellt wurde.

#### <a name="external-tables"></a>Externe Tabellen

- Es ist möglich, eine externe Daten Pool Tabelle für eine Tabelle zu erstellen, die nicht unterstützte Spaltentypen aufweist. Wenn Sie die externe Tabelle Abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle für einen Speicherpool Abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. In dem Szenario, in dem das Master-Pod neu gestartet wird, schlägt die Spark `NoRoteToHostException`-Sitzung möglicherweise mit fehl. Dies wird durch JVM-Caches verursacht, die nicht mit neuen IP-Adressen aktualisiert werden.

- Wenn Sie jupyter bereits installiert haben und ein separates python unter Windows, können Spark-Notebooks fehlschlagen. Um dieses Problem zu umgehen, führen Sie ein Upgrade von jupyter auf die neueste Version durch.

- Wenn Sie in einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle im Vorschaumodus anstatt im Bearbeitungsmodus hinzugefügt. Sie können auf das Vorschau Symbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise der folgende Fehler angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, die Änderungen an "HDFS-Site. XML einschließen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Der SA_PASSWORD ist Teil der Umgebung und ermittelbar (z. b. in einer Dump-Dumpdatei). Sie müssen die SA_PASSWORD auf der Master Instanz nach der Bereitstellung zurücksetzen. Dabei handelt es sich nicht um einen Fehler, sondern um einen Sicherheits Schritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

- AKS-Protokolle können ein SA-Kennwort für Big Data Cluster Bereitstellungen enthalten.

## <a id="ctp20"></a>CTP 2,0 (Oktober 2018)

In den folgenden Abschnitten werden die neuen Features und bekannten Probleme für Big Data Cluster in SQL Server 2019 CTP 2,0 beschrieben.

### <a name="new-features"></a>Neue Funktionen

- Einfache Bereitstellung mit dem Tool "azdata Management"
- Native Notebook-Darstellung in Azure Data Studio
- Abfragen von HDFS-Dateien über die Speicher Instanz von SQL Server
- Data Virtualization via Master to SQL Server, Oracle, MongoDB und HDFS
- Datenvirtualisierungsassistent für SQL Server und Oracle in Azure Data Studio
- ML-Dienste auf der Master-
- Cluster Verwaltungs Portal, das Sie für die Überwachung und Problembehandlung verwenden können
- Spark-Auftrags Übermittlung in Azure Data Studio 
- Spark-Benutzeroberfläche im Cluster Verwaltungs Portal
- Volumebereitstellung in Speicher Klassen
- Abfragen von Datenpools vom Master
- Anzeigen von Plänen für verteilte Abfragen in SSMS
- PIP-Paket für azdata-Verwaltungs Tool
- Integrierte Bereitstellungs-Engine über den Controller Dienst

### <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten finden Sie Informationen zu bekannten Problemen bei SQL Server Big Data Clustern in CTP 2,0.

#### <a name="deployment"></a>Bereitstellung

- Wenn Sie Azure Kubernetes Service (AKS) verwenden, ist die empfohlene Version von Kubernetes 1,10. *, die keine Unterstützung der Datenträger Größe bietet. Stellen Sie sicher, dass Sie die Größe des Speichers zum Zeitpunkt der Bereitstellung entsprechend anpassen. Weitere Informationen zum Anpassen der Speichergröße finden Sie im Artikel zur [Daten Persistenz](concept-data-persistence.md) . Für Kubernetes, die auf VMS bereitgestellt werden, ist die empfohlene Version 1,11.

- Nach der Bereitstellung in AKS werden möglicherweise die folgenden beiden Warn Ereignisse aus der Bereitstellung angezeigt. Beide Ereignisse sind bekannte Probleme, die jedoch nicht verhindern, dass Sie die Big Data Cluster in AKS erfolgreich bereitstellen.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn eine Big Data Cluster Bereitstellung fehlschlägt, wird der zugeordnete Namespace nicht entfernt. Dies kann zu einem verwaisten Namespace im Cluster führen. Eine Problem Umgehung besteht darin, den Namespace manuell zu löschen, bevor Sie einen Cluster mit dem gleichen Namen bereitstellen.

#### <a name="external-tables"></a>Externe Tabellen

- Es ist möglich, eine externe Daten Pool Tabelle für eine Tabelle zu erstellen, die nicht unterstützte Spaltentypen aufweist. Wenn Sie die externe Tabelle Abfragen, erhalten Sie eine Meldung wie die folgende:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Tabelle für einen Speicherpool Abfragen, erhalten Sie möglicherweise eine Fehlermeldung, wenn die zugrunde liegende Datei gleichzeitig in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark und Notebooks

- Pod-IP-Adressen können sich in der Kubernetes-Umgebung ändern, wenn Pods neu gestartet werden. In dem Szenario, in dem das Master-Pod neu gestartet wird, schlägt die Spark `NoRoteToHostException`-Sitzung möglicherweise mit fehl. Dies wird durch JVM-Caches verursacht, die nicht mit neuen IP-Adressen aktualisiert werden.

- Wenn Sie jupyter bereits installiert haben und ein separates python unter Windows, können Spark-Notebooks fehlschlagen. Um dieses Problem zu umgehen, führen Sie ein Upgrade von jupyter auf die neueste Version durch.

- Wenn Sie in einem Notebook auf den Befehl **Text hinzufügen** klicken, wird die Textzelle im Vorschaumodus anstatt im Bearbeitungsmodus hinzugefügt. Sie können auf das Vorschau Symbol klicken, um in den Bearbeitungsmodus zu wechseln und die Zelle zu bearbeiten.

#### <a name="hdfs"></a>HDFS

- Wenn Sie in HDFS mit der rechten Maustaste auf eine Datei klicken, um eine Vorschau anzuzeigen, wird möglicherweise der folgende Fehler angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Derzeit gibt es keine Möglichkeit, Dateien mit mehr als 30 MB in Azure Data Studio in einer Vorschau anzuzeigen.

- Konfigurationsänderungen an HDFS, die Änderungen an "HDFS-Site. XML einschließen, werden nicht unterstützt.

#### <a name="security"></a>Sicherheit

- Der SA_PASSWORD ist Teil der Umgebung und ermittelbar (z. b. in einer Dump-Dumpdatei). Sie müssen die SA_PASSWORD auf der Master Instanz nach der Bereitstellung zurücksetzen. Dabei handelt es sich nicht um einen Fehler, sondern um einen Sicherheits Schritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

- AKS-Protokolle können ein SA-Kennwort für Big Data Cluster Bereitstellungen enthalten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server Big Data Clustern finden Sie unter [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md).
