---
title: Versionshinweise
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt die neuesten Updates und bekannte Probleme bei der SQL Server-2019 big Data-Clustern (Vorschau).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4c178c5868789bec2dc80a4b68558f12afbc90d2
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58073226"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>Anmerkungen zu dieser Version für big Data-Cluster in SQL Server

Dieser Artikel führt die Updates und bekannte Probleme für die neuesten Versionen von SQL Server-big Data-Cluster.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp23"></a> CTP 2.3 (SQL 2019)

February 2019 &nbsp; &nbsp; / &nbsp; &nbsp; SQL Server 2019 &nbsp; &nbsp; / &nbsp; &nbsp; CTP2.3

### <a name="new-features"></a>Neue Funktionen

| Neues feature | Details |
| :---------- | :------ |
| [Übermitteln von Spark-Aufträgen in SQL Server-Clustern in Big Data in IntelliJ](spark-submit-job-intellij-tool-plugin.md). | &nbsp; |
| [Allgemeine CLI für die Bereitstellung und -Cluster-anwendungsverwaltung](big-data-cluster-create-apps.md). | &nbsp; |
| [VS Code-Erweiterung zum Bereitstellen von Anwendungen für SQL Server-big Data-Cluster](app-deployment-extension.md). | &nbsp; |
| [Änderungen an der **Mssqlctl** tool zur Verwendung des Befehls](#mssqlctlctp23). | &nbsp; |
| [Verwenden Sie Sparklyr in SQL Server 2019 Big Data-Cluster](sparklyr-from-RStudio.md). | &nbsp; |
| Binden Sie externe HDFS-kompatiblen Speicher in big Data-Cluster mit **HDFS tiering**. | Finden Sie unter [HDFS tiering](hdfs-tiering.md). |
| Neue einheitliche Verbindungsschnittstelle für SQL Server-Instanz master und das HDFS/Spark-Gateway. | Finden Sie unter [master SQL Server-Instanz und das HDFS/Spark-Gateway](connect-to-big-data-cluster.md). |
| Löschen eines Clusters mit **Mssqlctl Cluster löschen** jetzt löscht nur die Objekte im Namespace, die Teil der big Data-Cluster waren. | Der Namespace wird nicht gelöscht werden. In früheren Versionen mit diesem Befehl jedoch den gesamten Namespace löschen. |
| _Sicherheit_ Endpunktnamen wurden geändert und zusammengefasst. | _Vorherige Endpunkte:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-security-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-security-nodeport**<br/><br/>_Neuer Endpunkt:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-security** |
| _Proxy_ Endpunktnamen wurden geändert und zusammengefasst. | _Vorherige Endpunkte:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-proxy-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-proxy-nodeport**<br/><br/>_Neuer Endpunkt:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-service-proxy** |
| _Controller_ Endpunktnamen wurden geändert und zusammengefasst. | _Vorherige Endpunkte:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-mssql-controller-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-mssql-controller-nodeport**<br/><br/>_Neuer Endpunkt:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-controller** |
| &nbsp; | &nbsp; |

### <a name="known-issues-deployment"></a>Bekannte Probleme: Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt.

   > [!IMPORTANT]
   > Müssen Sie Ihre Daten sichern und löschen Sie Ihre vorhandenen big Data-Cluster (mit der früheren Version von **Mssqlctl**) vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-guidance.md#upgrade).

- Die **ACCEPT_EULA** -Umgebungsvariable muss "yes" oder "Ja", um den Endbenutzer-Lizenzvertrag zu akzeptieren. Vorgängerversionen zulässig, "y" und "Y", aber diese sind nicht mehr akzeptiert und führt dazu, dass die Bereitstellung nicht ausgeführt werden.

- Die **CLUSTER_PLATFORM** Umgebungsvariablen besitzt keinen Standardwert, wie in früheren Versionen.

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

### <a name="known-issues-kubeadm-deployments"></a>Bekannte Probleme: Kubeadm-Bereitstellungen

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

### <a id="mssqlctlctp23"></a> Bekannte Probleme: Mssqlctl

- Die **Mssqlctl** Tool geändert werden, von einem Verb-Nomen-Befehl, der Sortierung auf eine Bestellung Substantiv-Verb. Z. B. `mssqlctl create cluster` ist jetzt `mssqlctl cluster create`.

- Die `--name` -Parameter ist jetzt erforderlich, beim Erstellen eines Clusters mit `mssqlctl cluster create`.

   ```bash
   mssqlctl cluster create --name <cluster_name>
   ```

- Wichtige Informationen zum Upgrade auf die neueste Version von big Data-Cluster und **Mssqlctl**, finden Sie unter [ein Upgrade auf ein neues Release](deployment-guidance.md#upgrade).

### <a name="known-issues-external-tables"></a>Bekannte Probleme: Externe Tabellen

- Es ist möglich, eine externen Pool Datentabelle für eine Tabelle zu erstellen, die Spaltentypen nicht unterstützt wird. Wenn Sie auf die externe Tabelle Abfragen, erhalten Sie eine Meldung ähnlich der folgenden:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Wenn Sie eine externe Speicher-Pool-Tabelle Abfragen, können Sie eine Fehlermeldung, wenn gleichzeitig die zugrunde liegende Datei in HDFS kopiert wird.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Bei der Erstellung einer externen Tabelle, Oracle, die Zeichen-Datentypen zu verwenden, interpretiert der Studio für Azure Data Virtualization-Assistent diese Spalten als VARCHAR in der Definition der externen Tabelle an. Dies bewirkt einen Fehler in der DDL für externe Tabellen. Ändern Sie entweder das Oracle-Schema, um verwenden Sie den Typ NVARCHAR2 oder EXTERNAL TABLE-Anweisungen manuell erstellen, und geben NVARCHAR, statt mit dem Assistenten.

### <a name="known-issues-application-deployment"></a>Bekannte Probleme: Anwendungsbereitstellung

- Bei eine Anwendung von R, Python oder MLeap von RESTful-API aufrufen, tritt ein Timeout für der Aufruf innerhalb von 5 Minuten.

### <a name="known-issues-spark-and-notebooks"></a>Bekannte Probleme: Spark und notebooks

- In der Kubernetes-Umgebung können als PODs Neustarts POD-IP-Adressen ändern. In dem Szenario, in dem für die Master-Pod neu gestartet wird, kann die Spark-Sitzung mit fehlschlagen `NoRoteToHostException`. Dies wird verursacht durch JVM-Caches, die mit der neuen IP-Adresse aktualisiert nicht behandelt.

- Wenn Sie Jupyter, die bereits installiert haben, und ein separaten Python für Windows, Spark-Notebooks schlägt möglicherweise fehl. Um dieses Problem zu umgehen, aktualisieren Sie Jupyter, auf die neueste Version.

- In einem Notizbuch, wenn Sie auf die **Text hinzufügen** Befehl, die Textzelle im Bearbeitungsmodus befindet, anstatt im Vorschaumodus hinzugefügt wird. Klicken Sie auf das vorschausymbol klicken zum umschalten, um den Bearbeitungsmodus, und Bearbeiten der Zelle.

### <a name="known-issues-hdfs"></a>Bekannte Probleme: HDFS

- Wenn Sie mit der rechten Maustaste auf eine Datei in HDFS diesen in der Vorschau, können Sie die folgende Fehlermeldung angezeigt:

   `Error previewing file: File exceeds max size of 30MB`

   Zurzeit besteht keine Möglichkeit, Dateien, die größer als 30 MB in Azure Data Studio Vorschau anzeigen.

- Änderungen an der Konfiguration in HDFS, bei denen Änderungen an "Hdfs-Site.xml" werden nicht unterstützt.

### <a name="known-issues-security"></a>Bekannte Probleme: Sicherheit

- Die SA_PASSWORD ist Teil der Umgebung "und" ermittelt (z. B. in einer Dumpdatei "Cord"). Sie müssen die SA_PASSWORD für die master-Instanz nach der Bereitstellung zurücksetzen. Dies ist nicht auf, einen Fehler, aber eine Sicherheitsschritt. Weitere Informationen zum Ändern der SA_PASSWORD in einem Linux-Container finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS-Protokolle können das SA-Kennwort für big Data-Cluster-Bereitstellungen enthalten.

## <a id="ctp22"></a> CTP 2.2 (Dezember 2018)

Die folgenden Abschnitte beschreiben die neuen Features und bekannten Probleme für big Data-Cluster in SQL Server 2019 CTP 2.2.

### <a name="whats-in-the-ctp-22-release"></a>Was ist in der Version CTP 2.2?

- Cluster-Verwaltungsportal Zugriff mit `/portal` (**https://\<Ip-Adresse\>: 30777/Portal**).
- Master-Dienst-Poolname geändert `service-master-pool-lb` und `service-master-pool-nodeport` zu `endpoint-master-pool`.
- Neue Version des **Mssqlctl** und Images aktualisiert.
- Verschiedene Fehlerbehebungen und Verbesserungen.

### <a name="known-issues"></a>Bekannte Probleme

Die folgenden Abschnitte enthalten bekannte Probleme für SQL Server-big Data-Cluster in der CTP-Version 2.2.

#### <a name="deployment"></a>Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt. Sie müssen die sichern und löschen Sie alle vorhandenen big Data-Cluster vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-guidance.md#upgrade).

- Nach dem Bereitstellen in AKS können Sie die folgenden zwei Warning-Ereignisse aus der Bereitstellung möglicherweise. Diese beiden Ereignisse finden Sie bekannte Probleme, aber sie verhindern nicht, dass Sie erfolgreiche Bereitstellung von big Data-Cluster in AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Wenn es sich bei eine Clusterbereitstellung mit big Data ein Fehler auftritt, wird der zugeordnete Namespace nicht entfernt werden. Dies kann in einem verwaiste-Namespace im Cluster führen. Eine problemumgehung besteht darin, den Namespace manuell zu löschen, bevor die Bereitstellung eines Clusters mit dem gleichen Namen.

#### <a name="cluster-administration-portal"></a>Cluster-Verwaltungsportal

Das Verwaltungsportal für den Cluster wird den Endpunkt für die master-SQL Server-Instanz nicht angezeigt. Um die IP-Adresse und den Port für die master-Instanz ermitteln möchten, verwenden Sie die folgenden **"kubectl"** Befehl:

```
kubectl get svc endpoint-master-pool -n <your-cluster-name>
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

### <a name="whats-in-the-ctp-21-release"></a>Was ist in der Version CTP 2.1?

- [Bereitstellen von Python und R-apps](big-data-cluster-create-apps.md) in einer big Data-Cluster.
- Neue Version des **Mssqlctl** und Images aktualisiert. 
- Verschiedene Fehlerbehebungen und Verbesserungen.

### <a name="known-issues"></a>Bekannte Probleme

Die folgenden Abschnitte enthalten bekannte Probleme für SQL Server-big Data-Cluster in der CTP-Version 2.1.

#### <a name="deployment"></a>Bereitstellung

- Upgrade von eines big Data-Clusters für Daten aus einer früheren Version wird nicht unterstützt. Sie müssen die sichern und löschen Sie alle vorhandenen big Data-Cluster vor der Bereitstellung der neuesten Version. Weitere Informationen finden Sie unter [ein Upgrade auf ein neues Release](deployment-guidance.md#upgrade).

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

### <a name="whats-in-the-ctp-20-release"></a>Was ist in der Version CTP 2.0?

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