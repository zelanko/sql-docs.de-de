---
title: Einbinden von S3 für HDFS-Tiering
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie Sie HDFS-Tiering zum Einbinden eines externen S3-Dateisystems in HDFS in einem [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] einbinden.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 653f9a48c03df18fc0591f7bd8060d951567c779
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652309"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Einbinden von S3 für HDFS-Tiering in einen Big Data-Cluster

Die folgenden Abschnitte zeigen ein Beispiel für die Konfiguration von HDFS-Tiering mit einer S3-Speicherdatenquelle.

## <a name="prerequisites"></a>Voraussetzungen

- [Bereitgestellte Big Data-Cluster](deployment-guidance.md)
- [Big Data-Tools](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**
- Erstellen von Daten und Hochladen in einen S3-Bucket 
  - Laden Sie CSV- oder Parquet-Dateien in Ihren S3-Bucket hoch. Dies sind die externen HDFS-Daten, die im Big Data-Cluster in HDFS eingebunden werden.

## <a name="access-keys"></a>Zugriffsschlüssel

### <a name="set-environment-variable-for-access-key-credentials"></a>Festlegen der Umgebungsvariablen für Zugriffsschlüssel-Anmeldeinformationen

Öffnen Sie eine Eingabeaufforderung auf einem Clientcomputer, der auf Ihren Big Data-Cluster zugreifen kann. Legen Sie eine Umgebungsvariable im folgenden Format fest. Beachten Sie, dass sich die Anmeldeinformationen in einer durch Trennzeichen getrennten Liste befinden müssen. Der „Set“-Befehl wird unter Windows verwendet. Wenn Sie Linux verwenden, verwenden Sie stattdessen „export“.

   ```text
    set MOUNT_CREDENTIALS=fs.s3a.access.key=<Access Key ID of the key>,
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Weitere Informationen zum Erstellen von S3-Zugriffsschlüsseln finden Sie unter [S3-Zugriffsschlüssel](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a> Einbinden des HDFS-Remotespeichers

Nachdem Sie nun eine Anmeldeinformationendatei mit Zugriffsschlüsseln vorbereitet haben, können Sie mit dem Einbinden beginnen. In den folgenden Schritten wird der HDFS-Remotespeicher in S3 in den lokalen HDFS-Speicher Ihres Big Data-Clusters eingebunden.

1. Suchen Sie mit **kubectl** die IP-Adresse für den Endpunkt **controller-svc-external**-Dienst in Ihrem Big Data-Cluster. Suchen Sie nach der **externen IP-Adresse**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Melden Sie sich mit **azdata** über die externe IP-Adresse des Controllerendpunkts mit Ihrem Benutzernamen und -kennwort für den Cluster an:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
   
1. Legen Sie die Umgebungsvariable MOUNT_CREDENTIALS gemäß der obigen Anweisungen fest.

1. Binden Sie den HDFS-Remotespeicher mit dem Befehl **azdata bdc hdfs mount create** in Azure ein. Ersetzen Sie die Platzhalterwerte, bevor Sie den folgenden Befehl ausführen:

   ```bash
   azdata bdc hdfs mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Der „mount create“-Befehl ist asynchron. Zurzeit gibt keine Meldung an, ob die Einbindung erfolgreich war. Weitere Informationen zum Überprüfen des Status Ihrer Einbindungen finden Sie im [Statusabschnitt](#status).

Wenn die Einbindung erfolgreich war, sollten Sie in der Lage sein, die HDFS-Daten abzufragen und Spark-Aufträge dafür auszuführen. Sie wird im HDFS für Ihren Big Data-Cluster an dem Speicherort angezeigt, der durch `--mount-path` angegeben wird.

## <a id="status"></a> Abrufen des Status von Einbindungen

Verwenden Sie den folgenden Befehl, um die Status aller Einbindungen in Ihrem Big Data-Cluster aufzulisten:

```bash
azdata bdc hdfs mount status
```

Verwenden Sie den folgenden Befehl, um den Status einer Einbindung in einem bestimmten Pfad im HDFS aufzulisten:

```bash
azdata bdc hdfs mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Aktualisieren einer Einbindung

Im folgenden Beispiel wird die Einbindung aktualisiert.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Löschen der Einbindung

Verwenden Sie zum Löschen den Einbindung den Befehl **azdata bdc hdfs mount delete**, und geben Sie den Einbindungspfad in HDFS an:

```bash
azdata bdc hdfs mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
