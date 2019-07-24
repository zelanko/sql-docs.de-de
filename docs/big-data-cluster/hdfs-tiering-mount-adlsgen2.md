---
title: Einbinden von ADLS Gen2 für HDFS-Tiering
titleSuffix: How to mount ADLS Gen2
description: In diesem Artikel wird beschrieben, wie Sie HDFS-Tiering konfigurieren, um ein externes Azure Data Lake Storage Dateisystem in HDFS in einem SQL Server 2019 Big Data-Cluster (Vorschau) einbinden zu können.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7d8a6dd53452700853dca9774ed0196ed7546fe
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419347"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Einbinden von ADLS Gen2 für HDFS-Tiering in einem Big Data Cluster

In den folgenden Abschnitten wird ein Beispiel für die Konfiguration von HDFS-Tiering mit einer Azure Data Lake Storage Gen2-Datenquelle bereitgestellt.

## <a name="prerequisites"></a>Vorraussetzungen

- [Bereitgestellter Big Data Cluster](deployment-guidance.md)
- [Big Data-Tools](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a id="load"></a>Laden von Daten in Azure Data Lake Storage

Im folgenden Abschnitt wird beschrieben, wie Sie Azure Data Lake Storage Gen2 zum Testen des HDFS-Tiering einrichten. Wenn Sie bereits Daten in Azure Data Lake Storage gespeichert haben, können Sie diesen Abschnitt überspringen, um Ihre eigenen Daten zu verwenden.

1. [Erstellen Sie ein Speicherkonto mit Data Lake Storage Gen2-Funktionen](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. Erstellen Sie in diesem Speicherkonto [einen BlobContainer](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) für Ihre externen Daten.

1. Laden Sie eine CSV-oder Parkett Datei in den Container hoch. Dies sind die externen HDFS-Daten, die in HDFS im Big Data Cluster eingebunden werden.

## <a name="credentials-for-mounting"></a>Anmelde Informationen für die Einbindung

## <a name="use-oauth-credentials-to-mount"></a>Verwenden von OAuth-Anmelde Informationen zum Einbinden

Um OAuth-Anmelde Informationen zum einbinden zu verwenden, müssen Sie die folgenden Schritte ausführen:

1. Wechseln Sie zum [Azure-Portal](https://portal.azure.com)
1. Wechseln Sie im linken Navigationsbereich zu "Dienste", und klicken Sie auf "Azure Active Directory".
1. Erstellen Sie mithilfe von "App-Registrierungen" im Menü eine "Webanwendung, und folgen Sie dem Assistenten. **Merken Sie sich den Namen, den Sie hier erstellen**. Sie müssen diesen Namen Ihrem ADLS-Konto als autorisierten Benutzer hinzufügen.
1. Nachdem die Webanwendung erstellt wurde, wechseln Sie unter "Einstellungen" für die APP zu "Schlüssel".
1. Wählen Sie eine Schlüssel Dauer aus, und klicken Sie auf speichern. **Speichern Sie den generierten Schlüssel.**
1.  Wechseln Sie zurück zur Seite App-Registrierungen, und klicken Sie oben auf die Schaltfläche "Endpunkte". **Notieren Sie sich die URL für den tokenendpunkt.**
1. Für OAuth sollten Sie nun folgende Punkte beachten:

    - Die "Anwendungs-ID" der Web-App, die Sie in Schritt 3 erstellt haben.
    - Der Schlüssel, den Sie soeben in Schritt 5 erstellt haben.
    - Der tokenendpunkt aus Schritt 6

### <a name="adding-the-service-principal-to-your-adls-account"></a>Hinzufügen des Dienst Prinzipals zu Ihrem ADLS-Konto

1. Wechseln Sie erneut zum Portal, öffnen Sie das ADLS-Konto, und wählen Sie im linken Menü die Option Zugriffs Steuerung (IAM) aus.
1. Wählen Sie "Rollenzuweisung hinzufügen" aus, und suchen Sie nach dem Namen, den Sie oben in Schritt 3 erstellt haben (Beachten Sie, dass er nicht in der Liste angezeigt wird, aber gefunden wird, wenn Sie nach dem vollständigen Namen suchen).
1. Fügen Sie jetzt die Rolle "Speicher-blobdatenmitwirkender (Vorschau)" hinzu.

Warten Sie 5-10 Minuten, bevor Sie die Anmelde Informationen für die Einbindung verwenden.

### <a name="set-environment-variable-for-oauth-credentials"></a>Umgebungsvariable für OAuth-Anmelde Informationen festlegen

Öffnen Sie eine Eingabeaufforderung auf einem Client Computer, der auf den Big Data Cluster zugreifen kann. Legen Sie eine Umgebungsvariable im folgenden Format fest: Beachten Sie, dass sich die Anmelde Informationen in einer durch Trennzeichen getrennten Liste befinden müssen. Der Befehl "Set" wird unter Windows verwendet. Wenn Sie Linux verwenden, verwenden Sie stattdessen "Export".

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above],
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above],
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Verwenden von Zugriffs Schlüsseln zum Einbinden

Sie können auch mithilfe von Zugriffs Schlüsseln einbinden, die Sie für Ihr ADLS-Konto auf dem Azure-Portal abrufen können.

 > [!TIP]
   > Weitere Informationen zum Suchen des Zugriffsschlüssels (`<storage-account-access-key>`) für Ihr Speicherkonto finden Sie unter Anzeigen von [Konto Schlüsseln und Verbindungs Zeichenfolgen](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string).

### <a name="set-environment-variable-for-access-key-credentials"></a>Umgebungsvariable für Zugriffsschlüssel-Anmelde Informationen festlegen

1. Öffnen Sie eine Eingabeaufforderung auf einem Client Computer, der auf den Big Data Cluster zugreifen kann.

1. Öffnen Sie eine Eingabeaufforderung auf einem Client Computer, der auf den Big Data Cluster zugreifen kann. Legen Sie eine Umgebungsvariable im folgenden Format fest. Beachten Sie, dass sich die Anmelde Informationen in einer durch Trennzeichen getrennten Liste befinden müssen. Der Befehl "Set" wird unter Windows verwendet. Wenn Sie Linux verwenden, verwenden Sie stattdessen "Export".

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a>Einbinden des HDFS-Remote Speichers

Nachdem Sie die MOUNT_CREDENTIALS-Umgebungsvariable für Zugriffsschlüssel oder mithilfe von OAuth festgelegt haben, können Sie mit der Bereitstellung beginnen. In den folgenden Schritten wird der Remote-HDFS-Speicher in Azure Data Lake in den lokalen HDFS-Speicher Ihres Big Data Clusters einbinden.

1. Verwenden Sie **kubectl** , um die IP-Adresse für den Endpunkt **Controller-SVC-externen** Dienst im Big Data Cluster zu ermitteln. Suchen Sie nach der **externen IP-Adresse**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Melden Sie sich mit **azdata** über die externe IP-Adresse des Controller Endpunkts mit Ihrem Cluster Benutzernamen und-Kennwort an:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. Umgebungsvariable festlegen MOUNT_CREDENTIALS (Scrollen Sie nach oben, um Anweisungen zu finden)

1. Einbinden des HDFS-Remote Speichers in Azure mithilfe von **azdata BDC Storage-Pool Mount Create**. Ersetzen Sie die Platzhalter Werte, bevor Sie den folgenden Befehl ausführen:

   ```bash
   azdata bdc storage-pool mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
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
