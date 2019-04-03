---
title: Konfigurieren Sie die HDFS-tiering
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie HDFS, die Informationen zum Einbinden von eines externen Systems von Azure Data Lake Store-Datei in HDFS auf eine SQL Server-2019 big Data-Cluster (Vorschau) tiering konfiguriert.
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2542c7c05b222517ae9f4a4c05152f21a5ba293b
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58859642"
---
# <a name="configure-hdfs-tiering-on-sql-server-big-data-clusters"></a>Konfigurieren von HDFS cloudtiering auf SQL Server-big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

HDFS-Tiering bietet die Möglichkeit zum Bereitstellen von externen, HDFS-kompatiblen Dateisystem in HDFS. In diesem Artikel wird erläutert, wie HDFS, die Staffelung für SQL Server-2019 big Data-Clustern (Vorschau) zu konfigurieren. Zu diesem Zeitpunkt unterstützt CTP 2.4 nur die Verbindung mit Azure Data Lake-Speicher Gen2, die den Schwerpunkt dieses Artikels ist.

## <a name="hdfs-tiering-overview"></a>HDFS-tiering-Übersicht

Mit tiering, können Anwendungen problemlos Daten in einer Vielzahl von externen zugreifen, als ob die Daten in HDFS gespeichert. Einbindung ist ein Metadatenvorgang, in dem die Metadaten, die den Namespace auf dem System externe Datei wird beschrieben, über in HDFS kopiert. Zu diesen Metadaten gehören Informationen zu den externen Verzeichnisse und Dateien sowie deren Berechtigungen und ACLs. Die entsprechenden Daten ist nur kopiert bei Bedarf, wenn die Daten selbst erfolgt. Die externe Dateisystem-Daten können jetzt von der SQL Server-big Data-Cluster zugegriffen werden. Sie können Spark-Aufträge und SQL-Abfragen für diese Daten auf die gleiche Weise ausführen, die Sie für alle lokalen Daten in HDFS im Cluster ausgeführt werden würde.

> [!NOTE]
> HDFS zu Cloudtiering ist ein Feature von Microsoft entwickelt wurde, und eine frühere Version als Teil der Apache Hadoop 3.1 Verteilungspunkte freigegeben wurde. Weitere Informationen finden Sie unter [ https://issues.apache.org/jira/browse/HDFS-9806 ](https://issues.apache.org/jira/browse/HDFS-9806) Details.

Die folgenden Abschnitte enthalten ein Beispiel für HDFS, die horizontale Skalierung mit einer Azure Data Lake-Speicher Gen2-Datenquelle konfigurieren.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Bereitgestellte big Data-cluster](deployment-guidance.md)
- [Big Data-tools](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a id="load"></a> Laden von Daten in Azure Data Lake-Speicher

Der folgende Abschnitt beschreibt, wie Azure Data Lake-Speicher Gen2 zum Testen der HDFS-tiering eingerichtet wird. Wenn Sie bereits in Azure Data Lake-Speicher gespeicherte Daten haben, können Sie diesen Abschnitt, um Ihre eigenen Daten verwenden überspringen.

1. [Erstellen eines Speicherkontos mit Data Lake-Speicher Gen2 Funktionen](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Erstellen eines blobcontainers](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) in diesem Speicherkonto für Ihre externen Daten.

1. Hochgeladen Sie CSV- oder Parquet-Datei in den Container. Dies ist die externe HDFS-Daten, die in HDFS in die big Data-Cluster bereitgestellt werden.

## <a id="mount"></a> Bereitstellen der HDFS-Remotespeicher

Die folgenden Schritte stellen remote HDFS-Speicher in Azure Data Lake in den lokalen HDFS-Speicher, der Ihre big Data-Cluster bereit.

1. Öffnen Sie eine Eingabeaufforderung auf einem Clientcomputer, der Ihre big Data-Cluster zugreifen können.

1. Erstellen Sie eine lokale Datei mit dem Namen **files.creds** , enthält die Anmeldeinformationen Ihres Azure Data Lake-Speicher Gen2-Kontos mithilfe des folgenden Formats:

   ```text
   fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

   > [!TIP]
   > Weitere Informationen dazu, wie den Zugriffsschlüssel finden (`<storage-account-access-key>`) finden Sie in Ihrem Storage-Konto [anzeigen und kopieren Sie den Zugriffsschlüssel](https://docs.microsoft.com/azure/storage/common/storage-account-manage?#view-and-copy-access-keys).

1. Verwendung **"kubectl"** finden Sie die IP-Adresse für die **Endpunkt-Dienst-Proxy** -Dienst in Ihre big Data-Cluster. Suchen Sie nach der **externe IP-**.

   ```bash
   kubectl get svc endpoint-service-proxy -n <your-cluster-name>
   ```

1. Melden Sie sich mit **Mssqlctl** mithilfe den Proxy-Dienstendpunkt mit Ihrem Benutzernamen und Kennwort:

   ```bash
   mssqlctl login -e https://<IP-of-endpoint-service-proxy>:30777/ -u <username> -p <password>
   ```

1. Bereitstellen der remote-HDFS-Speicher in Azure mithilfe **Mssqlctl Speicher bereitstellen erstellen**. Ersetzen Sie die Platzhalter-Werte, bevor Sie den folgenden Befehl ausführen:

   ```bash
   mssqlctl storage mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name> --credential-file <path-to-adls-credentials>/file.creds
   ```

   > [!NOTE]
   > Create-Befehl für die Bereitstellung erfolgt asynchron. Zu diesem Zeitpunkt keine Nachricht vorliegt, der angibt, ob die Bereitstellung erfolgreich war. Finden Sie unter den [Status](#status) Abschnitt aus, um den Status Ihrer Bereitstellungen zu überprüfen.

Wenn erfolgreich bereitgestellt wurde, sollten Sie möglicherweise die HDFS-Daten Abfragen und führt Spark-Aufträge für diese. Er wird in das HDFS für Ihre big Data-Cluster in der vom angegebenen Position angezeigt `--local-path`.

## <a id="status"></a> Abrufen des Status von Bereitstellungen

Um den Status aller Bereitstellungen in Ihrer big Data-Cluster aufzulisten, verwenden Sie den folgenden Befehl aus:

```bash
mssqlctl storage mount status
```

Um den Status einer Bereitstellung in einem bestimmten Pfad in HDFS aufzulisten, verwenden Sie den folgenden Befehl aus:

```bash
mssqlctl storage mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Löschen Sie die Bereitstellung

Verwenden Sie zum Löschen der Bereitstellung der **Mssqlctl Speicher bereitstellen löschen** Befehl aus, und geben Sie den Bereitstellungspfad in HDFS:

```bash
mssqlctl storage mount delete --mount-path <mount-path-in-hdfs>
```

## <a id="issues"></a> Bekannte Probleme und Einschränkungen

Die folgende Liste enthält bekannte Probleme und aktuelle Einschränkungen der Verwendung von HDFS-Staffelung in SQL Server-big Data-Cluster:

- Wenn die Größe des externen Verzeichnis bereitgestellt wird, größer als die Kapazität des Clusters ist, schlägt fehl einbinden.

- Wenn die Bereitstellung im hängengeblieben ist eine `CREATING` Status seit langem, er hat in den meisten Fällen nicht. Brechen Sie in diesem Fall den Befehl ab, und löschen Sie die Bereitstellung aus, falls erforderlich. Stellen Sie sicher, dass die Parameter und Anmeldeinformationen vor der Wiederholung richtig sind.

- Bereitstellungen können nicht auf vorhandene Verzeichnisse erstellt werden.

- Bereitstellungen können nicht innerhalb von vorhandenen Bereitstellungen erstellt werden.

- Wenn alle Vorgänger des Bereitstellungspunkts-nicht vorhanden sind, werden sie mit den Berechtigungen erstellt werden standardmäßig auf R-Xr-Xr-X (555).

- Erstellen der Bereitstellung kann eine Weile dauern je nach Anzahl und Größe der Dateien, die bereitgestellt wird. Während dieses Vorgangs nicht die Dateien in die Bereitstellung für Benutzer sichtbar sind. Während die Bereitstellung erstellt wird, werden alle Dateien hinzugefügt werden, in einen temporären Pfad, deren Standard `/_temporary/_mounts/<mount-location>`.

- Der Ladebefehl für die Erstellung erfolgt asynchron. Nachdem der Befehl ausgeführt wurde, kann der Bereitstellungsstatus überprüft werden, um den Status der Bereitstellung zu verstehen.

- Wenn Sie die Bereitstellung zu erstellen, wird das Argument für verwendet **– Local-Path** ist im Wesentlichen ein eindeutiger Bezeichner der Bereitstellung. Die gleiche Zeichenfolge (einschließlich der "/" am Ende, falls vorhanden) muss in allen nachfolgenden Befehlen verwendet werden.

- Die Bereitstellungen sind schreibgeschützt. Sie können keine Verzeichnisse oder Dateien in einen Bereitstellungspunkt erstellen.

- Wir empfehlen nicht, Einbinden von Verzeichnissen und Dateien, die geändert werden können. Nachdem die Bereitstellung erstellt wurde, werden Änderungen oder Updates am Remotestandort, nicht in die Bereitstellung in HDFS übernommen. Wenn Änderungen am Remotestandort auftreten, können Sie auswählen, löschen und neu erstellen der Bereitstellung entsprechend den aktualisierten Zustand.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-2019 big Data-Cluster, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
