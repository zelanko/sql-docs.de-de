---
title: Einbinden von ADLS Gen2 für HDFS-Tiering
titleSuffix: How to mount ADLS Gen2
description: In diesem Artikel wird erläutert, wie HDFS, die Informationen zum Einbinden von eines externen Systems von Azure Data Lake Store-Datei in HDFS auf eine SQL Server-2019 big Data-Cluster (Vorschau) tiering konfiguriert.
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 504559fab3078b03ea3b8aea923035654f60ce47
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782138"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Wie Sie Mount ADLS Gen2 für HDFS-Staffelung in einem big Data-cluster

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

## <a name="credentials-for-mounting"></a>Anmeldeinformationen für die Einbindung

## <a name="use-oauth-credentials-to-mount"></a>Verwenden von OAuth-Anmeldeinformationen bereitstellen

Um OAuth-Anmeldeinformationen verwenden, um die bereitstellen, müssen Sie führen die folgenden Schritte aus:

1. Wechseln Sie zu der [Azure-Portal](https://portal.azure.com)
1. Wechseln Sie zu "Dienste" im linken Navigationsbereich, und Systemzeit auf "Azure Active Directory"
1. Verwenden im Menü "App-Registrierungen", erstellen Sie eine "Web-Anwendung und führen Sie den Assistenten. **Notieren Sie sich den Namen, die Sie hier erstellen**. Sie müssen diesen Namen zu Ihrem ADLS-Konto als autorisierte Benutzer hinzufügen.
1. Nachdem die Webanwendung erstellt wurde, wechseln Sie zu "Schlüssel" unter "Einstellungen" für die app.
1. Wählen Sie, die eine Dauer für den Schlüssel und klicken Sie auf Speichern. **Speichern Sie den generierten Schlüssel ein.**
1.  Wechseln Sie zurück zu der Seite "App-Registrierungen", und klicken Sie oben auf "Endpunkte". **Notieren Sie sich die URL "Token-Endpunkt"**
1. Sie verfügen nun über die folgenden Schritte für OAuth notiert:

    - Die "Anwendungs-ID" der Web-App Sie weiter oben in Schritt 3 erstellte
    - Der Schlüssel, den Sie gerade erstellt haben, in Schritt 5
    - Die token-Endpunkt aus Schritt 6

### <a name="adding-the-service-principal-to-your-adls-account"></a>Der Dienstprinzipal hinzufügen mit Ihrem ADLS-Konto

1. In diesem Fall zum Portal wechseln Sie und öffnen Sie ein ADLS-Konto, und wählen Sie die Zugriffssteuerung (IAM) im linken Menü.
1. Wählen Sie "Eine rollenzuweisung hinzufügen", und suchen Sie nach den Namen, die, den Sie in Schritt 3 oben (Beachten Sie, die nicht in der Liste angezeigt, sondern wird bei der Suche gefunden werden, für den vollständigen Namen) erstellt haben.
1. Fügen Sie jetzt "Storage-BLOB-Daten Rolle"Mitwirkender "(Vorschau)" hinzu.

Warten Sie 5 bis 10 Minuten, bevor Sie mit den Anmeldeinformationen für Bereitstellung

### <a name="create-credential-file"></a>Erstellen Sie die Datei

Öffnen Sie eine Eingabeaufforderung auf einem Clientcomputer, der Ihre big Data-Cluster zugreifen können.

Erstellen Sie eine lokale Datei mit dem Namen **filename.creds** , enthält die Anmeldeinformationen Ihres Azure Data Lake-Speicher Gen2-Kontos mithilfe des folgenden Formats:

   ```text
    fs.azure.account.auth.type=OAuth
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above]
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above]
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Verwenden Sie Zugriffsschlüssel bereitstellen

Sie können auch bereitstellen, mithilfe von Zugriffsschlüsseln, die Sie für Ihre ADLS-Konto im Azure-Portal abrufen können.

 > [!TIP]
   > Weitere Informationen dazu, wie den Zugriffsschlüssel finden (`<storage-account-access-key>`) finden Sie in Ihrem Storage-Konto [anzeigen und kopieren Sie den Zugriffsschlüssel](https://docs.microsoft.com/azure/storage/common/storage-account-manage?#view-and-copy-access-keys).

### <a name="create-credential-file"></a>Erstellen Sie die Datei

1. Öffnen Sie eine Eingabeaufforderung auf einem Clientcomputer, der Ihre big Data-Cluster zugreifen können.

1. Erstellen Sie eine lokale Datei mit dem Namen **filename.creds** , enthält die Anmeldeinformationen Ihres Azure Data Lake-Speicher Gen2-Kontos mithilfe des folgenden Formats:

   ```text
   fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a> Bereitstellen der HDFS-Remotespeicher

Nun, da Sie eine Datei mit Zugriffstasten oder mithilfe von OAuth vorbereitet haben, können Sie die Einbindung beginnen. Die folgenden Schritte stellen remote HDFS-Speicher in Azure Data Lake im lokalen HDFS-Speicher, der Ihre big Data-Cluster bereit.

1. Verwendung **"kubectl"** finden Sie die IP-Adresse für den Endpunkt **Controller-svc-External** -Dienst in Ihre big Data-Cluster. Suchen Sie nach der **externe IP-** .

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Melden Sie sich mit **Mssqlctl** verwenden die externe IP-Adresse des Endpunkts Controller mit Ihrem Benutzernamen und Kennwort:

   ```bash
   mssqlctl login -e https://<IP-of-controller-svc-external>:30080/
   ```

1. Bereitstellen der remote-HDFS-Speicher in Azure mithilfe **Mssqlctl Cluster Speicher-Pool einbinden erstellen**. Ersetzen Sie die Platzhalter-Werte, bevor Sie den folgenden Befehl ausführen:

   ```bash
   mssqlctl cluster storage-pool mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name> --credential-file <path-to-adls-credentials>/file.creds
   ```

   > [!NOTE]
   > Create-Befehl für die Bereitstellung erfolgt asynchron. Zu diesem Zeitpunkt keine Nachricht vorliegt, der angibt, ob die Bereitstellung erfolgreich war. Finden Sie unter den [Status](#status) Abschnitt aus, um den Status Ihrer Bereitstellungen zu überprüfen.

Wenn erfolgreich bereitgestellt wurde, sollten Sie möglicherweise die HDFS-Daten Abfragen und führt Spark-Aufträge für diese. Er wird in das HDFS für Ihre big Data-Cluster in der vom angegebenen Position angezeigt `--mount-path`.

## <a id="status"></a> Abrufen des Status von Bereitstellungen

Um den Status aller Bereitstellungen in Ihrer big Data-Cluster aufzulisten, verwenden Sie den folgenden Befehl aus:

```bash
mssqlctl cluster storage-pool mount status
```

Um den Status einer Bereitstellung in einem bestimmten Pfad in HDFS aufzulisten, verwenden Sie den folgenden Befehl aus:

```bash
mssqlctl cluster storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Löschen Sie die Bereitstellung

Verwenden Sie zum Löschen der Bereitstellung der **Mssqlctl Cluster Speicher-Pool einbinden löschen** Befehl aus, und geben Sie den Bereitstellungspfad in HDFS:

```bash
mssqlctl cluster storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-2019 big Data-Cluster, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
