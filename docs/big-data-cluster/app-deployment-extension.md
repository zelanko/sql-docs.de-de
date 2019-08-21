---
title: App Deploy-Erweiterung
titleSuffix: SQL Server big data clusters
description: Stellen Sie ein Python-oder R-Skript als [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] Anwendung auf (Vorschau) bereit.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 49a59650c406e3b48394da45ad0eeb4589fc4374
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653657"
---
# <a name="how-to-use-visual-studio-code-to-deploy-applications-to-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Verwenden von Visual Studio Code zum Bereitstellen von Anwendungen[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie Anwendungen in einem SQL Server Big Data Cluster mithilfe Microsoft Visual Studio Codes mit der APP-Bereitstellungs Erweiterung bereitstellen. Diese Funktion wurde in CTP 2.3 eingeführt. 

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Visual Studio Code](https://code.visualstudio.com/)
- [SQL Server Big Data Cluster](big-data-cluster-overview.md) CTP 2,3 oder höher

## <a name="capabilities"></a>Funktionen

Diese Erweiterung unterstützt die folgenden Aufgaben in Visual Studio Code:

- Durchführen einer Authentifizierung bei einem Big-Data-Cluster für SQL Server
- Abrufen einer Anwendungsvorlage aus dem GitHub-Repository zur Bereitstellung unterstützter Runtimes
- Verwalten geöffneter Anwendungsvorlagen im Arbeitsbereich des Benutzers
- Bereitstellen einer Anwendung mithilfe einer Spezifikation im YAML-Format
- Verwalten bereitgestellter Apps auf Big-Data-Clustern für SQL Server
- Anzeigen aller bereitgestellten Apps in der Randleiste mit zusätzlichen Informationen
- Generieren einer Ausführungsspezifikation zur Nutzung der App oder zur Löschung der App aus dem Cluster
- Nutzen bereitgestellter Apps mithilfe einer Ausführungsspezifikation im YAML-Format

In den folgenden Abschnitten wird der zuerst der Installationsvorgang beschrieben. Anschließend wird eine Übersicht über die Funktionsweise der Erweiterung bereitgestellt. 

### <a name="install"></a>Installieren

Installieren Sie zunächst die Erweiterung der APP-Bereitstellung in Visual Studio Code:

1. App-Bereitstellungs [Erweiterung](https://aka.ms/app-deploy-vscode) herunterladen, um die Erweiterung im Rahmen der Visual Studio Code zu installieren.

1. Starten Sie Visual Studio Code, und navigieren Sie zur Rand Leiste Erweiterungen.

1. Klicken Sie oben in der Randleiste auf das Kontextmenü `…` und anschließend auf `Install from vsix`.

   ![Installieren über VSIX](media/vs-extension/install_vsix.png)

1. Wählen Sie die heruntergeladene `sqlservbdc-app-deploy.vsix`-Datei aus, die installiert werden soll.

Nachdem die SQL Server Big Data Cluster-App Bereitstellung installiert wurde, werden Sie aufgefordert, Visual Studio Code neu zu laden. Nun sollte der SQL Server BDC App Explorer in der Visual Studio Code Rand Leiste angezeigt werden.

### <a name="app-explorer"></a>App-Explorer

Klicken Sie auf die Erweiterung in der Randleiste, um ein Seitenpanel mit dem App-Explorer zu laden. Auf dem folgenden Screenshot ist der App-Explorer zu sehen. Darin sind in diesem Beispiel keine Apps oder App-Spezifikationen verfügbar:

![App-Explorer](media/vs-extension/app_explorer.png)

#### <a name="connect-to-cluster"></a>Verbindung mit Cluster herstellen

Verwenden Sie eine der folgenden Methoden, um eine Verbindung mit dem Clusterendpunkt herzustellen:

- Klicken Sie unten in der Statusleiste auf `SQL Server BDC Disconnected`.
- Alternativ können Sie auch im oberen Bereich auf die Schaltfläche `Connect to Cluster` klicken, auf der ein Pfeil auf einen Eingang zeigt.

Visual Studio Code Eingabeaufforderung für den entsprechenden Endpunkt, Benutzernamen und das Kennwort ein.

Der Endpunkt für die Verbindungs Herstellung `Cluster Management Service` ist der Endpunkt mit Port 30080.

Sie können diesen Endpunkt auch über die Befehlszeile suchen. 

```
azdata bdc endpoint list
```

Eine der anderen Möglichkeiten, diese Informationen zu erhalten, besteht darin, mit der rechten Maustaste auf dem Server in Azure Data Studio zu **Verwalten** , wo Sie die Endpunkte der aufgelisteten Dienste finden.

![ADS-Endpunkt](media/vs-extension/ads_end_point.png)

Nachdem Sie den zu verwendenden Endpunkt gefunden haben, stellen Sie eine Verbindung mit dem Cluster her.

![Neue Verbindung](media/vs-extension/connect_to_cluster.png)

 Wenn die richtigen Anmelde Informationen und der APP-Endpunkt angegeben werden, wird Visual Studio Code benachrichtigt, dass Sie mit dem Cluster verbunden sind. in der Rand Leiste werden alle bereitgestellten apps angezeigt. Wenn die Verbindung hergestellt wird, werden der Endpunkt und Benutzername als Teil Ihres Benutzerprofils in `./sqldbc` gespeichert. Kennwörter oder Token werden nie gespeichert. Wenn Sie sich erneut anmelden, werden der gespeicherte Host- und Benutzername automatisch in der Eingabeaufforderung ergänzt. Sie müssen jedoch immer das Kennwort eingeben. Wenn Sie eine Verbindung mit einem anderen Clusterendpunkt herstellen möchten, klicken Sie einfach noch einmal auf `New Connection`. Die Verbindung wird automatisch geschlossen, wenn Sie Visual Studio Code schließen, oder wenn Sie einen anderen Arbeitsbereich öffnen und die Verbindung wiederherstellen müssen.

### <a name="app-template"></a>App-Vorlage

Sie müssen den *Arbeitsbereich* in Visual Studio Code öffnen, in dem Sie die Artefakte der APP speichern.

Sie können eine neue App mithilfe einer unserer Vorlagen bereitstellen. Klicken Sie dazu im Bereich `App Specifications` auf die Schaltfläche `New App Template`. Sie werden aufgefordert, den Namen, die Runtime und den Speicherort der App auf Ihrem lokalen Computer anzugeben. Der Name und die Version, die Sie angeben, sollten eine DNS-1035-Bezeichnung sein und aus alphanumerischen Zeichen Kleinbuchstaben oder "-" bestehen, mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.

Es wird empfohlen, dass Sie Sie in Ihrem aktuellen Visual Studio Code Arbeitsbereich platzieren, damit Sie die vollständige Funktionalität der Erweiterung verwenden können, aber Sie können Sie an einer beliebigen Stelle in Ihrem lokalen Dateisystem platzieren.

![Neue App-Vorlage](media/vs-extension/new_app_template.png)

Eine neue App-Vorlage wird am angegebenen Speicherort erstellt. Anschließend wird die Bereitstellungsdatei `spec.yaml` im Arbeitsbereich geöffnet. Wenn sich das ausgewählte Verzeichnis in Ihrem Arbeitsbereich befindet, sollte es auch im Bereich `App Specifications` angezeigt werden:

![Geladene App-Vorlage](media/vs-extension/loading_app_template.png)

Die Vorlage ist eine einfache `helloworld` APP, die im Bereich "App-Spezifikationen" wie folgt angeordnet ist:

- **spec.yaml**
   - Dieser Datei entnimmt der Cluster die Informationen darüber, wie die App bereitgestellt werden soll.
- **run-spec.yaml**
   - Dieser Datei entnimmt der Cluster den Namen der App.

Der Quellcode der APP würde sich im Arbeitsbereichs Ordner befinden.

- **Quell Dateiname**
   - Dies ist die Quellcodedatei, die in `spec.yaml` durch `src` angegeben ist.
   - Sie verfügt über eine Funktion (`handler`), die als Einstiegspunkt (`entrypoint`) der App entsprechend den Informationen in `spec.yaml` betrachtet wird. Die Funktion nimmt eine Zeichenfolgeneingabe namens `msg` entgegen und gibt eine Zeichenfolgenausgabe mit dem Namen `out` zurück. Diese Zeichenfolgen werden in `inputs` und `outputs` in der Datei `spec.yaml` angegeben.

Wenn Sie keine vordefinierte Vorlage, sondern die Datei `spec.yaml` für die Bereitstellung einer bereits erstellten App verwenden möchten, klicken Sie auf die Schaltfläche `New Deploy Spec` neben der Schaltfläche`New App Template`. Führen Sie anschließend dieselben Schritte wie vorher aus. Dadurch wird ausschließlich die Datei `spec.yaml` zur Verfügung gestellt, die Sie beliebig anpassen können.

### <a name="deploy-app"></a>Bereitstellen einer App

Sie können die App sofort mit der CodeLens-Verknüpfung `Deploy App` in `spec.yaml` bereitstellen oder im Menü „App Specifications“ (App-Spezifikationen) neben der Datei `spec.yaml` auf die Schaltfläche klicken, auf der sich ein Ordnersymbol mit einem Blitz befindet. Die Erweiterung zippt alle Dateien in dem Verzeichnis, in dem sich `spec.yaml` befindet, und stellt die App auf dem Cluster bereit. 

>[!NOTE]
>Achten Sie darauf, dass sich alle App-Dateien im selben Verzeichnis wie `spec.yaml` befinden. `spec.yaml` muss sich auf der Stammebene des App-Quellcodeverzeichnisses befinden. 

![Schaltfläche „Deploy App“ (App bereitstellen)](media/vs-extension/deploy_app_lightning.png)

![CodeLens-Verknüpfung „Deploy App“ (App bereitstellen)](media/vs-extension/deploy_app_codelens.png)

Wenn die App zur Nutzung bereitsteht, werden Sie durch eine Statusänderung der App in der Randleiste benachrichtigt:

![App bereitgestellt](media/vs-extension/app_deploy.png)

![Status „App Ready“ (App bereit) in Randleiste](media/vs-extension/app_ready_side_bar.png)

![Benachrichtigung „App Ready“ (App bereit)](media/vs-extension/app_ready_notification.png)

Im Seitenbereich wird Folgendes angezeigt:

Sie können sich alle bereitgestellten Apps mit den folgenden Informationen in der Randleiste anzeigen lassen:

- state
- version
- Eingabeparameter
- Ausgabeparameter
- Verknüpfungen
  - Swagger
  - Details

Wenn Sie auf `Links`klicken, sehen Sie, dass Sie auf die `swagger.json` ihrer bereitgestellten App zugreifen können, damit Sie Ihre eigenen Clients schreiben können, die Ihre APP aufrufen:

![Swagger](media/vs-extension/swagger.png)

Weitere Informationen finden Sie unter [Nutzen von Anwendungen auf Big-Data-Clustern](big-data-cluster-consume-apps.md).

### <a name="app-run"></a>Ausführen der App

Sobald die App bereit ist, rufen Sie sie mit der Datei `run-spec.yaml` auf, die in der App-Vorlage angegeben wurde:

![Ausführungsspezifikation](media/vs-extension/run_spec.png)

Ersetzen Sie `hello` durch eine beliebige Zeichenfolge, und führen Sie die Spezifikation noch einmal mit der CodeLens-Verknüpfung oder der Schaltfläche mit dem Blitz in der Randleiste neben `run-spec.yaml` aus. Wenn keine Ausführungsspezifikation vorliegt, müssen Sie diese mithilfe der auf dem Cluster bereitgestellten App generieren:

![„Get Run Spec“ (Ausführungsspezifikation abrufen)](media/vs-extension/get_run_spec.png)

Bearbeiten Sie die abgerufene Spezifikation entsprechend Ihren Anforderungen, und führen Sie sie danach aus. Visual Studio Code gibt das entsprechende Feedback zurück, wenn die Ausführung der APP abgeschlossen ist:

![App-Ausgabe](media/vs-extension/app_output.png)

Wie auf dem obigen Screenshot zu sehen ist, enthält eine temporäre `.json`-Datei in Ihrem Arbeitsbereich die Ausgabe. Sie können diese Ausgabe speichern, um sie beizubehalten. Andernfalls wird sie beim Schließen der Datei gelöscht. Wenn Ihre App keine Informationen in einer Datei ausgibt, wird nur die Benachrichtigung `Successful App Run` im unteren Bereich angezeigt. Wenn die Ausführung fehlschlägt, wird eine Fehlermeldung angezeigt, mit der Sie die Ursache des Problems ermitteln können.

Beim Ausführen einer App können Parameter auf unterschiedliche Weisen übergeben werden:

Sie können alle Eingaben in der folgenden `.json`-Datei festlegen:

- `inputs: ./example.json`

Wenn Sie eine bereitgestellte App aufrufen, die Eingabeparameter in der App hinterlegt oder benutzerdefiniert sind und der Eingabeparameter nicht einem primitiven Typ entspricht (beispielsweise im Fall eines Arrays, Vektors, Datenframes oder komplexen JSON-Objekts), müssen Sie den Parametertyp direkt beim Aufruf der App über die Eingabeaufforderung angeben:

- Vektor
    - `inputs:`
        - `x: [1, 2, 3]`
- Matrix
    - `inputs:`
        - `x: [[A,B,C],[1,2,3]]`
- Objekt
    - `inputs:`
        - `x: {A: 1, B: 2, C: 3}`

Alternativ können Sie auch eine Zeichenfolge als relativen oder absoluten Pfad zu einer `.txt`-, `.json`- oder `.csv`-Datei angeben, die die erforderliche Eingabe in einem Format zur Verfügung stellt, das Ihre App benötigt. Die Datei wird auf Grundlage von `Node.js Path library` analysiert. In dieser Bibliothek wird ein Dateipfad wie folgt definiert: `string that contains a / or \ character` (Zeichenfolge, die das Zeichen „/“ oder „\“ enthält).

Wenn der Eingabeparameter benötigt, jedoch nicht angegeben wird, wird eine Fehlermeldung angezeigt. Diese enthält entweder die Zeichenfolge mit dem falschen Dateipfad (falls angegeben) oder den ungültigen Parameter. Es liegt in der Verantwortung des App-Erstellers, verständliche Parameter zu definieren.

Wenn Sie eine App löschen möchten, klicken Sie neben der App im Seitenbereich `Deployed Apps` auf die Schaltfläche mit dem Papierkorb.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie apps [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] , die in in ihren eigenen Anwendungen bereitgestellt werden, unter Verwenden von [Anwendungen auf Big Data Clustern](big-data-cluster-consume-apps.md) für weitere Informationen integrieren. Zusätzliche Beispiele für die Erweiterung sind unter [Bereitstellen von Anwendungen auf Big-Data-Clustern für SQL Server](https://aka.ms/sql-app-deploy) verfügbar.

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]finden Sie unter [was [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]ist?](big-data-cluster-overview.md).


Die vorgestellte Erweiterung soll Ihnen einen echten Mehrwert bieten. Wir freuen uns daher über Feedback. Bitte senden Sie dieses an das [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Team](https://aka.ms/sqlfeedback).
