---
title: Konfigurieren von HDFS-Tiering
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird beschrieben, wie Sie HDFS-Tiering zum Einbinden eines externen Azure Data Lake Storage Dateisystems in HDFS auf einem [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]konfigurieren.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c7b24af0b0c6a22cbab1a9c280a0ba868ca2cd21
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652324"
---
# <a name="configure-hdfs-tiering-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Konfigurieren von HDFS-Tiering für[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

HDFS-Tiering bietet die Möglichkeit, ein externes, HDFS-kompatibles Dateisystem in HDFS einzubinden. In diesem Artikel wird erläutert, wie das HDFS- [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] Tiering für (Vorschau) konfiguriert wird. Zurzeit unterstützen wir das Herstellen einer Verbindung mit Azure Data Lake Storage Gen2 und Amazon S3. 

## <a name="hdfs-tiering-overview"></a>Übersicht zum HDFS-Tiering

Beim Tiering können Anwendungen nahtlos auf Daten in einer Vielzahl externer Speicher zugreifen, als ob sich die Daten im lokalen HDFS befinden. Die Einbindung ist ein Metadatenvorgang, bei dem die Metadaten, die den Namespace im externen Dateisystem beschreiben, in Ihr lokales HDFS kopiert werden. Diese Metadaten enthalten Informationen zu den externen Verzeichnissen und Dateien zusammen mit ihren Berechtigungen und ACLs. Die entsprechenden Daten werden nur bei Bedarf kopiert, wenn auf die Daten selbst z.B. über eine Abfrage zugegriffen wird. Der Zugriff auf die externen Dateisystemdaten ist jetzt über den SQL Server-Big Data-Cluster möglich. Sie können Spark-Aufträge und SQL-Abfragen für diese Daten auf die gleiche Weise ausführen, wie Sie sie für allen lokalen Daten ausführen, die in HDFS im Cluster gespeichert sind.

### <a name="caching"></a>Caching
Heutzutage wird standardmäßig 1% des gesamten HDFS-Speichers für das Zwischenspeichern der eingebundenen Daten reserviert. Das Zwischenspeichern ist eine Einbindungen übergreifende globale Einstellung.

> [!NOTE]
> HDFS-Tiering ist ein von Microsoft entwickeltes Feature, und eine frühere Version davon wurde als Teil der Apache Hadoop 3.1-Distribution veröffentlicht. Weitere Informationen finden Sie unter [https://issues.apache.org/jira/browse/HDFS-9806](https://issues.apache.org/jira/browse/HDFS-9806).

Die folgenden Abschnitte zeigen ein Beispiel für die Konfiguration von HDFS-Tiering mit einer Azure Data Lake Storage Gen2-Datenquelle.

## <a name="refresh"></a>Aktualisieren

Das HDFS-Tiering unterstützt die Aktualisierung. Aktualisieren Sie eine vorhandene Einbindung für die aktuelle Momentaufnahme der Remotedaten.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Bereitgestellte Big Data-Cluster](deployment-guidance.md)
- [Big Data-Tools](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a name="mounting-instructions"></a>Einbindungsanweisungen

Wir unterstützen das Herstellen einer Verbindung mit Azure Data Lake Storage Gen2 und Amazon S3. Anweisungen zum Einbinden dieser Speichertypen finden Sie in den folgenden Artikeln:

- [Vorgehensweise: Einbinden von ADLS Gen2 für HDFS-Tiering in einen Big Data-Cluster](hdfs-tiering-mount-adlsgen2.md)
- [Vorgehensweise: Einbinden von S3 für HDFS-Tiering in einen Big Data-Cluster](hdfs-tiering-mount-s3.md)

## <a id="issues"></a> Einschränkungen und bekannte Probleme

Die folgende Liste enthält bekannte Probleme und die aktuellen Einschränkungen bei der Verwendung von HDFS [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]-Tiering in:

- Wenn die Einbindung für einen längeren Zeitraum in einem `CREATING`-Zustand bleibt, ist wahrscheinlich ein Fehler aufgetreten. Brechen Sie in diesem Fall den Befehl ab, und löschen Sie die Einbindung, falls erforderlich. Vergewissern Sie sich vor einem erneuten Versuch, dass die Parameter und Anmeldeinformationen richtig sind.

- Einbindungen können nicht in vorhandenen Verzeichnissen erstellt werden.

- Einbindungen können nicht in vorhandenen Einbindungen erstellt werden.

- Wenn keiner der Vorgänger des Bereitstellungspunkts vorhanden ist, wird er mit den standardmäßigen Berechtigungen r-xr-xr-x (555) erstellt.

- Die Erstellung der Einbindung kann je nach Anzahl und Größe der einzubindenden Dateien einige Zeit in Anspruch nehmen. Während dieses Vorgangs sind die Dateien unter der Einbindung für die Benutzer nicht sichtbar. Während die Einbindung erstellt wird, werden alle Dateien einem temporären Pfad hinzugefügt, der standardmäßig `/_temporary/_mounts/<mount-location>` lautet.

- Der Befehl zum Erstellen der Einbindung ist asynchron. Nachdem der Befehl ausgeführt wurde, kann der Einbindungsstatus geprüft werden, um den Status der Einbindung zu verstehen.

- Beim Erstellen der Einbindung ist das für **--mount-path** verwendete Argument im Grunde ein eindeutiger Bezeichner für die Einbindung. Die gleiche Zeichenfolge (einschließlich „/“ am Ende, falls vorhanden) muss in nachfolgenden Befehlen verwendet werden.

- Die Einbindungen sind schreibgeschützt. Es ist nicht möglich, Verzeichnisse oder Dateien unter einer Einbindung zu erstellen.

- Es wird nicht empfohlen, Verzeichnisse und Dateien einzubinden, die sich ändern können. Nach dem Erstellen der Einbindung werden Änderungen oder Aktualisierungen des Remotespeicherorts nicht mehr in der Einbindung im HDFS berücksichtigt. Wenn am Remotespeicherort Änderungen vorgenommen werden, können Sie wählen, die Einbindung zu löschen und neu zu erstellen, um den aktualisierten Zustand widerzuspiegeln.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]finden Sie unter [was [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]ist?](big-data-cluster-overview.md).
