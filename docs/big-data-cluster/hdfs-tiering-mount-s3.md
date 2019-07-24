---
title: Einbinden von S3 für HDFS-Tiering
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird beschrieben, wie Sie HDFS-Tiering konfigurieren, um ein externes S3-Dateisystem in HDFS in einem SQL Server 2019 Big Data-Cluster (Vorschauversion) einbinden zu können.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 28c80d6076f07c8a4f1605149f4b5c730c8349a1
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419338"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Einbinden von S3 für HDFS-Tiering in einem Big Data Cluster

In den folgenden Abschnitten wird ein Beispiel für die Konfiguration von HDFS-Tiering mit einer S3-Speicherdaten Quelle bereitgestellt.

## <a name="prerequisites"></a>Vorraussetzungen

- [Bereitgestellter Big Data Cluster](deployment-guidance.md)
- [Big Data-Tools](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**
- Erstellen und Hochladen von Daten in einen S3-Bucket 
  - Laden Sie CSV-oder Parkett Dateien in Ihren S3-Bucket hoch. Dies sind die externen HDFS-Daten, die in HDFS im Big Data Cluster eingebunden werden.

## <a name="access-keys"></a>Zugriffsschlüssel

### <a name="set-environment-variable-for-access-key-credentials"></a>Umgebungsvariable für Zugriffsschlüssel-Anmelde Informationen festlegen

Öffnen Sie eine Eingabeaufforderung auf einem Client Computer, der auf den Big Data Cluster zugreifen kann. Legen Sie eine Umgebungsvariable im folgenden Format fest. Beachten Sie, dass sich die Anmelde Informationen in einer durch Trennzeichen getrennten Liste befinden müssen. Der Befehl "Set" wird unter Windows verwendet. Wenn Sie Linux verwenden, verwenden Sie stattdessen "Export".

   ```text
    set MOUNT_CREDENTIALS=fs.s3a.access.key=<Access Key ID of the key>,
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Weitere Informationen zum Erstellen von S3-Zugriffs Schlüsseln finden Sie unter [S3 Access Keys (S3-Zugriffsschlüssel](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)).

## <a id="mount"></a>Einbinden des HDFS-Remote Speichers

Nachdem Sie nun eine Anmelde Informationsdatei mit Zugriffs Schlüsseln vorbereitet haben, können Sie mit der Bereitstellung beginnen. In den folgenden Schritten wird der Remote-HDFS-Speicher in S3 in den lokalen HDFS-Speicher Ihres Big Data Clusters einbinden.

1. Verwenden Sie **kubectl** , um die IP-Adresse für den Endpunkt **Controller-SVC-externen** Dienst im Big Data Cluster zu ermitteln. Suchen Sie nach der **externen IP-Adresse**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Melden Sie sich mit **azdata** über die externe IP-Adresse des Controller Endpunkts mit Ihrem Cluster Benutzernamen und-Kennwort an:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
   
1. Umgebungsvariable festlegen MOUNT_CREDENTIALS befolgen Sie die obigen Anweisungen.

1. Einbinden des HDFS-Remote Speichers in Azure mithilfe von **azdata BDC Storage-Pool Mount Create**. Ersetzen Sie die Platzhalter Werte, bevor Sie den folgenden Befehl ausführen:

   ```bash
   azdata bdc storage-pool mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Der Befehl "Mount Create" ist asynchron. Zurzeit gibt es keine Meldung, die angibt, ob die einreilegung erfolgreich war. Weitere Informationen zum Status Ihrer bereit Stellungen finden Sie im Abschnitt " [Status](#status) ".

Wenn die Bereitstellung erfolgreich war, sollten Sie in der Lage sein, die HDFS-Daten abzufragen und Spark-Aufträge dafür auszuführen. Er wird im HDFS für Ihren Big Data Cluster an dem Speicherort angezeigt, der `--mount-path`durch angegeben wird.

## <a id="status"></a>Status von bereit Stellungen erhalten

Verwenden Sie den folgenden Befehl, um den Status aller bereit Stellungen in Ihrem Big Data Cluster aufzulisten:

```bash
azdata bdc storage-pool mount status
```

Verwenden Sie den folgenden Befehl, um den Status einer Einstellung in einem bestimmten Pfad in HDFS aufzulisten:

```bash
azdata bdc storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Ein einbinden aktualisieren

Im folgenden Beispiel wird das Einbinden aktualisiert.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a>Das Einbinden löschen

Zum Löschen der Anwendung verwenden Sie den Befehl **azdata BDC Storage-Pool Mount DELETE** , und geben Sie den einstellungspfad in HDFS an:

```bash
azdata bdc storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server 2019 Big Data-Clustern finden Sie unter [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md).
