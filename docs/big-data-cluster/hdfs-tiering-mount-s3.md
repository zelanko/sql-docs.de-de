---
title: Mount S3 für das tiering von HDFS
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie HDFS, die Informationen zum Einbinden von eines externen Systems des S3-Datei in HDFS auf big Data-Cluster (Vorschau) eine SQL Server-2019 tiering konfiguriert.
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 79c09d5bcff26c9f5867e5b0fb38bd019b681b5c
ms.sourcegitcommit: 89abd4cd4323ae5ee284571cd69a9fe07d869664
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "64330595"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Wie Sie Mount S3 für HDFS-Staffelung in einem big Data-cluster

Die folgenden Abschnitte enthalten ein Beispiel für horizontale Skalierung mit einer Datenquelle für die S3-Speicher HDFS zu konfigurieren.

## <a name="prerequisites"></a>Vorraussetzungen

- [Bereitgestellte big Data-cluster](deployment-guidance.md)
- [Big Data-tools](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**
- Erstellen und Hochladen von Daten in einem S3-bucket 
  - Hochladen von CSV oder Parquet-Dateien in Ihrem S3-Bucket. Dies ist die externe HDFS-Daten, die in HDFS in die big Data-Cluster bereitgestellt werden.

## <a name="access-keys"></a>Zugriffstasten

1. Öffnen Sie eine Eingabeaufforderung auf einem Clientcomputer, der Ihre big Data-Cluster zugreifen können.

1. Erstellen Sie eine lokale Datei mit dem Namen **filename.creds** , enthält die Anmeldeinformationen Ihres S3-Kontos mithilfe des folgenden Formats:

   ```text
    fs.s3a.access.key=<Access Key ID of the key>
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Weitere Informationen zum Erstellen von Zugriffstasten für S3 finden Sie unter [S3-Zugriffsschlüssel](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a> Bereitstellen der HDFS-Remotespeicher

Nun, da Sie eine Datei mit Zugriffstasten vorbereitet haben, können Sie die Einbindung beginnen. Die folgenden Schritte aus bereit den HDFS Remotespeicher s3 im lokalen HDFS-Speicher, der Ihre big Data-cluster

1. Verwendung **"kubectl"** finden Sie die IP-Adresse für den **Mgmtproxy-svc-External** -Dienst in Ihre big Data-Cluster. Suchen Sie nach der **externe IP-**.

   ```bash
   kubectl get svc mgmtproxy-svc-external -n <your-cluster-name>
   ```

1. Melden Sie sich mit **Mssqlctl** verwenden die externe IP-Adresse den verwaltungsendpunkt für den Proxy mit Ihrem Benutzernamen und Kennwort:

   ```bash
   mssqlctl login -e https://<IP-of-mgmtproxy-svc-external>:30777/ -u <username> -p <password>
   ```

1. Bereitstellen der remote-HDFS-Speicher in Azure mithilfe **Mssqlctl Speicher bereitstellen erstellen**. Ersetzen Sie die Platzhalter-Werte, bevor Sie den folgenden Befehl ausführen:

   ```bash
   mssqlctl storage mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name> --credential-file <path-to-s3-credentials>/file.creds
   ```

   > [!NOTE]
   > Create-Befehl für die Bereitstellung erfolgt asynchron. Zu diesem Zeitpunkt keine Nachricht vorliegt, der angibt, ob die Bereitstellung erfolgreich war. Finden Sie unter den [Status](#status) Abschnitt aus, um den Status Ihrer Bereitstellungen zu überprüfen.

Wenn erfolgreich bereitgestellt wurde, sollten Sie möglicherweise die HDFS-Daten Abfragen und führt Spark-Aufträge für diese. Er wird in das HDFS für Ihre big Data-Cluster in der vom angegebenen Position angezeigt `--mount-path`.

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

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-2019 big Data-Cluster, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
