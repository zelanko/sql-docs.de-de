---
title: Konfigurieren Sie die HDFS-tiering
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie HDFS, die Informationen zum Einbinden von eines externen Systems von Azure Data Lake Store-Datei in HDFS auf eine SQL Server-2019 big Data-Cluster (Vorschau) tiering konfiguriert.
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a36bd28efd128a76246297995d712b417d7f230d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66782106"
---
# <a name="configure-hdfs-tiering-on-sql-server-big-data-clusters"></a>Konfigurieren von HDFS cloudtiering auf SQL Server-big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

HDFS-Tiering bietet die Möglichkeit zum Bereitstellen von externen, HDFS-kompatiblen Dateisystem in HDFS. In diesem Artikel wird erläutert, wie HDFS, die Staffelung für SQL Server-2019 big Data-Clustern (Vorschau) zu konfigurieren. Zu diesem Zeitpunkt wird die Verbindung mit Azure Data Lake-Speicher Gen2 und Amazon S3 unterstützt. 

## <a name="hdfs-tiering-overview"></a>HDFS-tiering-Übersicht

Mit tiering, können Anwendungen problemlos Daten in einer Vielzahl von externen zugreifen, als ob die Daten in das lokale HDFS gespeichert. Einbindung ist ein Metadatenvorgang, in die Metadaten, die den Namespace auf dem System externe Datei wird beschrieben, über in Ihrer lokalen HDFS kopiert. Zu diesen Metadaten gehören Informationen zu den externen Verzeichnisse und Dateien sowie deren Berechtigungen und ACLs. Die entsprechenden Daten ist nur kopiert bei Bedarf aus, wenn die Daten selbst über z. B. eine Abfrage zugegriffen werden. Die externe Dateisystem-Daten können jetzt von der SQL Server-big Data-Cluster zugegriffen werden. Sie können Spark-Aufträge und SQL-Abfragen für diese Daten auf die gleiche Weise ausführen, die Sie für alle lokalen Daten in HDFS im Cluster ausgeführt werden würde.

### <a name="caching"></a>Caching
Heute wird standardmäßig 1 % der Gesamtspeicher HDFS reserviert für die Zwischenspeicherung von bereitgestellten Daten. Das Zwischenspeichern ist eine globale Einstellung über Bereitstellungen hinweg.

> [!NOTE]
> HDFS zu Cloudtiering ist ein Feature von Microsoft entwickelt wurde, und eine frühere Version als Teil der Apache Hadoop 3.1 Verteilungspunkte freigegeben wurde. Weitere Informationen finden Sie unter [ https://issues.apache.org/jira/browse/HDFS-9806 ](https://issues.apache.org/jira/browse/HDFS-9806) Details.

Die folgenden Abschnitte enthalten ein Beispiel für HDFS, die horizontale Skalierung mit einer Azure Data Lake-Speicher Gen2-Datenquelle konfigurieren.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Bereitgestellte big Data-cluster](deployment-guidance.md)
- [Big Data-tools](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a name="mounting-instructions"></a>Bereitstellen von Anweisungen

Wir unterstützen das Herstellen einer Verbindung mit Azure Data Lake-Speicher Gen2 und Amazon S3. Anweisungen zum Bereitstellen von gegen diese Art von Speicher finden Sie in den folgenden Artikeln:

- [Wie Sie Mount ADLS Gen2 für HDFS-Staffelung in einem big Data-cluster](hdfs-tiering-mount-adlsgen2.md)
- [Wie Sie Mount S3 für HDFS-Staffelung in einem big Data-cluster](hdfs-tiering-mount-s3.md)

## <a id="issues"></a> Bekannte Probleme und Einschränkungen

Die folgende Liste enthält bekannte Probleme und aktuelle Einschränkungen der Verwendung von HDFS-Staffelung in SQL Server-big Data-Cluster:

- Wenn die Bereitstellung im hängengeblieben ist eine `CREATING` Status seit langem, er hat in den meisten Fällen nicht. Brechen Sie in diesem Fall den Befehl ab, und löschen Sie die Bereitstellung aus, falls erforderlich. Stellen Sie sicher, dass die Parameter und Anmeldeinformationen vor der Wiederholung richtig sind.

- Bereitstellungen können nicht auf vorhandene Verzeichnisse erstellt werden.

- Bereitstellungen können nicht innerhalb von vorhandenen Bereitstellungen erstellt werden.

- Wenn alle Vorgänger des Bereitstellungspunkts-nicht vorhanden sind, werden sie mit den Berechtigungen erstellt werden standardmäßig auf R-Xr-Xr-X (555).

- Erstellen der Bereitstellung kann eine Weile dauern je nach Anzahl und Größe der Dateien, die bereitgestellt wird. Während dieses Vorgangs nicht die Dateien in die Bereitstellung für Benutzer sichtbar sind. Während die Bereitstellung erstellt wird, werden alle Dateien hinzugefügt werden, in einen temporären Pfad, deren Standard `/_temporary/_mounts/<mount-location>`.

- Der Ladebefehl für die Erstellung erfolgt asynchron. Nachdem der Befehl ausgeführt wurde, kann der Bereitstellungsstatus überprüft werden, um den Status der Bereitstellung zu verstehen.

- Wenn Sie die Bereitstellung zu erstellen, wird das Argument für verwendet **--Bereitstellungspfad** ist im Wesentlichen ein eindeutiger Bezeichner der Bereitstellung. Die gleiche Zeichenfolge (einschließlich der "/" am Ende, falls vorhanden) muss in allen nachfolgenden Befehlen verwendet werden.

- Die Bereitstellungen sind schreibgeschützt. Sie können keine Verzeichnisse oder Dateien in einen Bereitstellungspunkt erstellen.

- Wir empfehlen nicht, Einbinden von Verzeichnissen und Dateien, die geändert werden können. Nachdem die Bereitstellung erstellt wurde, werden Änderungen oder Updates am Remotestandort, nicht in die Bereitstellung in HDFS übernommen. Wenn Änderungen am Remotestandort auftreten, können Sie auswählen, löschen und neu erstellen der Bereitstellung entsprechend den aktualisierten Zustand.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-2019 big Data-Cluster, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
