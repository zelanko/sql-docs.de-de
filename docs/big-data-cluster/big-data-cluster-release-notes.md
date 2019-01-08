---
title: Versionshinweise
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt die neuesten Updates und bekannte Probleme bei der SQL Server-2019 big Data-Clustern (Vorschau).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: 8c9c57e641c76f78bf66565cc8e1ce8f67323b7e
ms.sourcegitcommit: 3f19c843b38d3835d07921612f0143620eb9a0e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53709813"
---
# <a name="release-notes-for-sql-server-2019-big-data-clusters"></a>Anmerkungen zu dieser Version für SQL Server-2019 big Data-Cluster

Dieser Artikel enthält die neuesten Updates und bekannten Probleme für die neueste Version von SQL Server-big Data-Cluster. Die folgende Tabelle enthält Links, die Sie im Abschnitt für die Versionen in diesem Artikel behandelt.

| Release | date |
|---|---|
| [CTP-VERSION 2.2](#ctp22) | Dezember 2018 |
| [CTP-VERSION 2.1](#ctp21) | November 2018 |
| [CTP 2.0](#ctp20) | Oktober 2018 |

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

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
