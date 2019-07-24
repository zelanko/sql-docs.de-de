---
title: Konfigurieren von HDFS-Tiering
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird beschrieben, wie Sie HDFS-Tiering konfigurieren, um ein externes Azure Data Lake Storage Dateisystem in HDFS in einem SQL Server 2019 Big Data-Cluster (Vorschau) einbinden zu können.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 17eedf9f0797a0adb5eda6ca8ee090fc762e1491
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419377"
---
# <a name="configure-hdfs-tiering-on-sql-server-big-data-clusters"></a>Konfigurieren von HDFS-Tiering auf SQL Server Big Data Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

HDFS-Tiering bietet die Möglichkeit, ein externes, HDFS-kompatibles Dateisystem in HDFS bereitzustellen. In diesem Artikel wird beschrieben, wie Sie HDFS-Tiering für SQL Server 2019 Big Data Cluster (Vorschauversion) konfigurieren. Zurzeit unterstützen wir das Herstellen einer Verbindung mit Azure Data Lake Storage Gen2 und Amazon S3. 

## <a name="hdfs-tiering-overview"></a>Übersicht über das HDFS-Tiering

Beim Tiering können Anwendungen nahtlos auf Daten in einer Vielzahl externer Speicher zugreifen, als ob sich die Daten im lokalen HDFS befinden. Die Einbindung ist ein Metadatenvorgang, bei dem die Metadaten, die den Namespace im externen Dateisystem beschreiben, in Ihr lokales HDFS kopiert werden. Diese Metadaten enthalten Informationen zu den externen Verzeichnissen und Dateien zusammen mit ihren Berechtigungen und ACLs. Die entsprechenden Daten werden nur bei Bedarf kopiert, wenn auf die Daten selbst über eine Abfrage zugegriffen wird. Der Zugriff auf die externen Dateisystem Daten ist jetzt über den SQL Server Big Data-Cluster möglich. Sie können Spark-Aufträge und SQL-Abfragen für diese Daten auf die gleiche Weise ausführen, wie Sie Sie auf allen lokalen Daten ausführen, die in HDFS im Cluster gespeichert sind.

### <a name="caching"></a>Caching
Heutzutage wird standardmäßig 1% des gesamten HDFS-Speichers für das Zwischenspeichern der bereitgestellten Daten reserviert. Caching ist eine globale Einstellung für alle bereit Stellungen.

> [!NOTE]
> HDFS-Tiering ist ein Feature, das von Microsoft entwickelt wurde, und eine frühere Version von Microsoft wurde als Teil der Apache Hadoop 3,1-Verteilung veröffentlicht. Weitere Informationen finden [https://issues.apache.org/jira/browse/HDFS-9806](https://issues.apache.org/jira/browse/HDFS-9806) Sie unter.

In den folgenden Abschnitten wird ein Beispiel für die Konfiguration von HDFS-Tiering mit einer Azure Data Lake Storage Gen2-Datenquelle bereitgestellt.

## <a name="refresh"></a>Aktualisieren

Das HDFS-Tiering unterstützt die Aktualisierung. Aktualisieren Sie eine vorhandene Anwendung für die aktuelle Momentaufnahme der Remote Daten.

## <a name="prerequisites"></a>Vorraussetzungen

- [Bereitgestellter Big Data Cluster](deployment-guidance.md)
- [Big Data-Tools](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a name="mounting-instructions"></a>Anweisungen zur Bereitstellung

Wir unterstützen das Herstellen einer Verbindung mit Azure Data Lake Storage Gen2 und Amazon S3. Anweisungen zum Einbinden dieser Speichertypen finden Sie in den folgenden Artikeln:

- [Einbinden von ADLS Gen2 für HDFS-Tiering in einem Big Data Cluster](hdfs-tiering-mount-adlsgen2.md)
- [Einbinden von S3 für HDFS-Tiering in einem Big Data Cluster](hdfs-tiering-mount-s3.md)

## <a id="issues"></a>Bekannte Probleme und Einschränkungen

Die folgende Liste enthält bekannte Probleme und die aktuellen Einschränkungen bei der Verwendung von HDFS-Tiering in SQL Server Big Data Clustern:

- Wenn die Festlegung für einen längeren `CREATING` Zeitraum in einem Zustand bleibt, ist wahrscheinlich ein Fehler aufgetreten. Brechen Sie in diesem Fall den Befehl ab, und löschen Sie die Eingabe, falls erforderlich. Vergewissern Sie sich, dass die Parameter und Anmelde Informationen richtig sind

- Für vorhandene Verzeichnisse können keine bereit Stellungen erstellt werden.

- Bereit Stellungen können nicht innerhalb vorhandener bereit Stellungen erstellt werden.

- Wenn keiner der Vorgänger des einstellungspunkts vorhanden ist, wird er mit den Berechtigungen erstellt, die standardmäßig auf r-XR-XR-x (555).

- Die Erstellung der Bereitstellung kann je nach Anzahl und Größe der bereitgestellten Dateien einige Zeit in Anspruch nehmen. Während dieses Vorgangs sind die Dateien unter der einreilegung für die Benutzer nicht sichtbar. Während der Erstellung werden alle Dateien einem temporären Pfad hinzugefügt, dessen Standard `/_temporary/_mounts/<mount-location>`ist.

- Der Befehl "Mount Creation" ist asynchron. Nachdem der Befehl ausgeführt wurde, kann der Einstellungsstatus geprüft werden, um den Status der einreistellung zu verstehen.

- Beim Erstellen der Einrichtung ist das für " **--Mount-Path** " verwendete Argument im Grunde ein eindeutiger Bezeichner für die einreilegung. Die gleiche Zeichenfolge (einschließlich "/" am Ende, falls vorhanden) muss in nachfolgenden Befehlen verwendet werden.

- Die bereit Stellungen sind schreibgeschützt. Es ist nicht möglich, Verzeichnisse oder Dateien unter einer einreilegung zu erstellen.

- Es wird nicht empfohlen, Verzeichnisse und Dateien zu ändern, die sich ändern können. Nachdem die Erstellung erstellt wurde, werden Änderungen oder Aktualisierungen am Remote Speicherort nicht mehr in der einreitung in HDFS berücksichtigt. Wenn am Remote Speicherort Änderungen vorgenommen werden, können Sie die Festlegung löschen und neu erstellen, um den aktualisierten Zustand widerzuspiegeln.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server 2019 Big Data-Clustern finden Sie unter [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md).
