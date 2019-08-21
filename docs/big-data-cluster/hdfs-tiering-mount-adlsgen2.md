---
title: Einbinden von ADLS Gen2 für HDFS-Tiering
titleSuffix: How to mount ADLS Gen2
description: In diesem Artikel wird beschrieben, wie Sie HDFS-Tiering zum Einbinden eines externen Azure Data Lake Storage Dateisystems in HDFS auf einem [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]konfigurieren.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 822c10ad41232d213302e4bb5e328449d9f5f764
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652316"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Einbinden von ADLS Gen2 für HDFS-Tiering in einen Big Data-Cluster

Die folgenden Abschnitte zeigen ein Beispiel für die Konfiguration von HDFS-Tiering mit einer Azure Data Lake Storage Gen2-Datenquelle.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Bereitgestellte Big Data-Cluster](deployment-guidance.md)
- [Big Data-Tools](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a id="load"></a> Laden von Daten in Azure Data Lake Storage Gen2

Im folgenden Abschnitt wird beschrieben, wie Sie Azure Data Lake Storage Gen2 zum Testen des HDFS-Tierings einrichten. Wenn Sie bereits Daten in Azure Data Lake Storage gespeichert haben, können Sie diesen Abschnitt überspringen, um Ihre eigenen Daten zu verwenden.

1. [Erstellen eines Azure Data Lake Storage Gen2-Speicherkontos](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Schnellstart: Hochladen, Herunterladen und Auflisten von Blobs mit dem Azure-Portal](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal).

1. Laden Sie eine CSV- oder Parquet-Datei in den Container hoch. Dies sind die externen HDFS-Daten, die im Big Data-Cluster in HDFS eingebunden werden.

## <a name="credentials-for-mounting"></a>Anmeldeinformationen für die Einbindung

## <a name="use-oauth-credentials-to-mount"></a>Verwenden von OAuth-Anmeldeinformationen zum Einbinden

Um OAuth-Anmeldeinformationen zum Einbinden zu verwenden, müssen Sie die folgenden Schritte ausführen:

1. Wechseln Sie zum [Azure-Portal](https://portal.azure.com).
1. Wechseln Sie im linken Navigationsbereich zu „Dienste“, und klicken Sie auf „Azure Active Directory“.
1. Erstellen Sie mithilfe von „App-Registrierungen“ im Menü eine Webanwendung, und folgen Sie dem Assistenten. **Merken Sie sich den Namen, den Sie hier erstellen**. Sie müssen diesen Namen Ihrem ADLS-Konto als autorisierter Benutzer hinzufügen.
1. Wechseln Sie nach dem Erstellen der Webanwendung unter „Einstellungen“ für die App zu „Schlüssel“.
1. Wählen Sie eine Schlüsseldauer aus, und klicken Sie auf „Speichern“. **Speichern Sie den generierten Schlüssel.**
1.  Wechseln Sie zurück zur Seite „App-Registrierungen“, und klicken Sie oben auf die Schaltfläche „Endpunkte“. **Notieren Sie sich den „Tokenendpunkt“ für die URL**.
1. Für OAuth sollten Sie nun folgende Punkte notiert haben:

    - Die „Anwendungs-ID“ der Web-App, die Sie oben in Schritt 3 erstellt haben.
    - Den Schlüssel, den Sie soeben in Schritt 5 erstellt haben.
    - Den Tokenendpunkt aus Schritt 6.

### <a name="adding-the-service-principal-to-your-adls-account"></a>Hinzufügen des Dienstprinzipals zu Ihrem ADLS-Konto

1. Wechseln Sie erneut zum Portal, öffnen Sie das ADLS-Konto, und wählen Sie im linken Menü die Option „Zugriffssteuerung (IAM)“ aus.
1. Wählen Sie „Rollenzuweisung hinzufügen“ aus, und suchen Sie nach dem Namen, den Sie oben in Schritt 3 erstellt haben (beachten Sie, dass er nicht in der Liste angezeigt wird, aber Sie finden ihn, wenn Sie nach dem vollständigen Namen suchen).
1. Fügen Sie jetzt die Rolle „Mitwirkender an Storage-Blobdaten (Vorschau)“ hinzu.

Warten Sie 5-10 Minuten, bevor Sie die Anmeldeinformationen für die Einbindung verwenden.

### <a name="set-environment-variable-for-oauth-credentials"></a>Festlegen der Umgebungsvariablen für OAuth-Anmeldeinformationen

Öffnen Sie eine Eingabeaufforderung auf einem Clientcomputer, der auf Ihren Big Data-Cluster zugreifen kann. Legen Sie eine Umgebungsvariable im folgenden Format fest: Beachten Sie, dass sich die Anmeldeinformationen in einer durch Trennzeichen getrennten Liste befinden müssen. Der „Set“-Befehl wird unter Windows verwendet. Wenn Sie Linux verwenden, verwenden Sie stattdessen „export“.

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above],
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above],
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Verwenden von Zugriffsschlüsseln zum Einbinden

Sie können die Einbindung auch mithilfe von Zugriffsschlüsseln durchführen, die Sie für Ihr ADLS-Konto im Azure-Portal abrufen können.

 > [!TIP]
   > Weitere Informationen zum Suchen des Zugriffsschlüssels (`<storage-account-access-key>`) für Ihr Speicherkonto finden Sie unter [Anzeigen von Kontoschlüsseln und Verbindungszeichenfolgen](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string).

### <a name="set-environment-variable-for-access-key-credentials"></a>Festlegen der Umgebungsvariablen für Zugriffsschlüssel-Anmeldeinformationen

1. Öffnen Sie eine Eingabeaufforderung auf einem Clientcomputer, der auf Ihren Big Data-Cluster zugreifen kann.

1. Öffnen Sie eine Eingabeaufforderung auf einem Clientcomputer, der auf Ihren Big Data-Cluster zugreifen kann. Legen Sie eine Umgebungsvariable im folgenden Format fest. Beachten Sie, dass sich die Anmeldeinformationen in einer durch Trennzeichen getrennten Liste befinden müssen. Der „Set“-Befehl wird unter Windows verwendet. Wenn Sie Linux verwenden, verwenden Sie stattdessen „export“.

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a> Einbinden des HDFS-Remotespeichers

Nachdem Sie die MOUNT_CREDENTIALS-Umgebungsvariable für Zugriffsschlüssel oder die Verwendung von OAuth festgelegt haben, können Sie mit der Einbindung beginnen. In den folgenden Schritten wird der HDFS-Remotespeicher in Azure Data Lake in den lokalen HDFS-Speicher Ihres Big Data-Clusters eingebunden.

1. Suchen Sie mit **kubectl** die IP-Adresse für den Endpunkt **controller-svc-external**-Dienst in Ihrem Big Data-Cluster. Suchen Sie nach der **externen IP-Adresse**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Melden Sie sich mit **azdata** über die externe IP-Adresse des Controllerendpunkts mit Ihrem Benutzernamen und -kennwort für den Cluster an:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. Legen Sie die Umgebungsvariable MOUNT_CREDENTIALS fest (scrollen Sie für die Anweisungen nach oben).

1. Einbinden des HDFS-Remote Speichers in Azure mithilfe von **azdata BDC HDFS Mount Create**. Ersetzen Sie die Platzhalterwerte, bevor Sie den folgenden Befehl ausführen:

   ```bash
   azdata bdc hdfs mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
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

Verwenden Sie den Befehl **azdata BDC HDFS Mount DELETE** , um die Eingabe zu löschen, und geben Sie den einstellungspfad in HDFS an:

```bash
azdata bdc hdfs mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]finden Sie unter [was [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]ist?](big-data-cluster-overview.md).
