---
title: App Deploy-Erweiterung
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie ein Python- oder R-Skript als Anwendung auf einem Big-Data-Cluster für SQL Server 2019 (Vorschauversion) bereitstellen.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1e5ab6364437432c803a364abd50ef5b1af4f8f6
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958915"
---
# <a name="how-to-use-vs-code-to-deploy-applications-to-sql-server-big-data-clusters"></a>Verwenden von VS Code zum Bereitstellen von Anwendungen auf Big-Data-Clustern für SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie mit der App Deploy-Erweiterung (Erweiterung für App-Bereitstellungen) in Visual Studio Code Anwendungen auf einem Big-Data-Cluster für SQL Server bereitstellen. Diese Funktion wurde in CTP 2.3 eingeführt. 

## <a name="prerequisites"></a>Voraussetzungen

- [Visual Studio Code](https://code.visualstudio.com/)
- [Big-Data-Cluster für SQL Server](big-data-cluster-overview.md) CTP 2.3 oder höher

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

Installieren Sie zuerst die App Deploy-Erweiterung in VS Code:

1. Laden Sie die [App Deploy-Erweiterung](https://aka.ms/app-deploy-vscode) für VS Code herunter.

1. Starten Sie VS Code, und navigieren Sie zur Randleiste mit den Erweiterungen.

1. Klicken Sie oben in der Randleiste auf das Kontextmenü `…` und anschließend auf `Install from vsix`.

   ![Installieren über VSIX](media/vs-extension/install_vsix.png)

1. Wählen Sie die heruntergeladene `sqlservbdc-app-deploy.vsix`-Datei aus, die installiert werden soll.

Nachdem die App Deploy-Erweiterung für Big-Data-Cluster in SQL Server installiert wurde, werden Sie aufgefordert, VS Code neu zu laden. In der Randleiste von VS Code sollte nun der „SQL Server BDC App Explorer“ (App-Explorer für SQL Server BDC) angezeigt werden.

### <a name="app-explorer"></a>App-Explorer

Klicken Sie auf die Erweiterung in der Randleiste, um ein Seitenpanel mit dem App-Explorer zu laden. Auf dem folgenden Screenshot ist der App-Explorer zu sehen. Darin sind in diesem Beispiel keine Apps oder App-Spezifikationen verfügbar:

<img src="media/vs-extension/app_explorer.png" width=350px></img>
<!--![App Explorer](media/vs-extension/app_explorer.png)-->

#### <a name="new-connection"></a>Neue Verbindung

Verwenden Sie eine der folgenden Methoden, um eine Verbindung mit dem Clusterendpunkt herzustellen:

- Klicken Sie unten in der Statusleiste auf `SQL Server BDC Disconnected`.
- Alternativ können Sie auch im oberen Bereich auf die Schaltfläche `New Connection` klicken, auf der ein Pfeil auf einen Eingang zeigt.

   ![Neue Verbindung](media/vs-extension/connect_to_cluster.png)

Sie werden von VS Code dazu aufgefordert, den Endpunkt, den Benutzernamen und das Kennwort anzugeben. Wenn Sie die richtigen Anmeldeinformationen und den korrekten App-Endpunkt angeben, werden Sie von VS Code benachrichtigt, dass Sie mit dem Cluster verbunden wurden. In der Randleiste werden außerdem alle bereitgestellten Apps angezeigt. Wenn die Verbindung hergestellt wird, werden der Endpunkt und Benutzername als Teil Ihres Benutzerprofils in `./sqldbc` gespeichert. Kennwörter oder Token werden nie gespeichert. Wenn Sie sich erneut anmelden, werden der gespeicherte Host- und Benutzername automatisch in der Eingabeaufforderung ergänzt. Sie müssen jedoch immer das Kennwort eingeben. Wenn Sie eine Verbindung mit einem anderen Clusterendpunkt herstellen möchten, klicken Sie einfach noch einmal auf `New Connection`. Die Verbindung wird automatisch getrennt, wenn Sie VS Code schließen oder einen anderen Arbeitsbereich öffnen und dann die Verbindung wiederherstellen müssen.

### <a name="app-template"></a>App-Vorlage

Sie können eine neue App mithilfe einer unserer Vorlagen bereitstellen. Klicken Sie dazu im Bereich `App Specifications` auf die Schaltfläche `New App Template`. Sie werden aufgefordert, den Namen, die Runtime und den Speicherort der App auf Ihrem lokalen Computer anzugeben. Sie sollten die App in Ihrem aktuellen VS Code-Arbeitsbereich platzieren, damit Sie alle Funktionen der Erweiterung nutzen können. Sie können jedoch auch einen anderen Speicherort auf Ihrem lokalen Dateisystem angeben.

![Neue App-Vorlage](media/vs-extension/new_app_template.png)

Eine neue App-Vorlage wird am angegebenen Speicherort erstellt. Anschließend wird die Bereitstellungsdatei `spec.yaml` im Arbeitsbereich geöffnet. Wenn sich das ausgewählte Verzeichnis in Ihrem Arbeitsbereich befindet, sollte es auch im Bereich `App Specifications` angezeigt werden:

![Geladene App-Vorlage](media/vs-extension/loading_app_template.png)

Die Vorlage enthält eine einfache `Hello World`-App, die aus folgenden Dateien besteht:

- **spec.yaml**
   - Dieser Datei entnimmt der Cluster die Informationen darüber, wie die App bereitgestellt werden soll.
- **run-spec.yaml**
   - Dieser Datei entnimmt der Cluster den Namen der App.
- **handler.py**
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

Wenn Sie auf `Links` klicken, können Sie auf die Datei `swagger.json` Ihrer bereitgestellten App zugreifen. Dadurch können Sie eigene Clients programmieren, die Ihre App aufrufen:

![Swagger](media/vs-extension/swagger.png)

Weitere Informationen finden Sie unter [Nutzen von Anwendungen auf Big-Data-Clustern](big-data-cluster-consume-apps.md).

### <a name="app-run"></a>Ausführen der App

Sobald die App bereit ist, rufen Sie sie mit der Datei `run-spec.yaml` auf, die in der App-Vorlage angegeben wurde:

![Ausführungsspezifikation](media/vs-extension/run_spec.png)

Ersetzen Sie `hello` durch eine beliebige Zeichenfolge, und führen Sie die Spezifikation noch einmal mit der CodeLens-Verknüpfung oder der Schaltfläche mit dem Blitz in der Randleiste neben `run-spec.yaml` aus. Wenn keine Ausführungsspezifikation vorliegt, müssen Sie diese mithilfe der auf dem Cluster bereitgestellten App generieren:

![„Get Run Spec“ (Ausführungsspezifikation abrufen)](media/vs-extension/get_run_spec.png)

Bearbeiten Sie die abgerufene Spezifikation entsprechend Ihren Anforderungen, und führen Sie sie danach aus. Nach der Ausführung der App stellt VS Code Feedback bereit:

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

Im Artikel [Nutzen von Anwendungen auf Big Data-Clustern](big-data-cluster-consume-apps.md) erfahren Sie, wie Sie Apps, die auf Big Data-Clustern für SQL Server bereitgestellt wurden, in Ihre eigenen Anwendungen integrieren können. Zusätzliche Beispiele für die Erweiterung sind unter [Bereitstellen von Anwendungen auf Big-Data-Clustern für SQL Server](https://aka.ms/sql-app-deploy) verfügbar.

Weitere Informationen zu Big Data-Clustern für SQL Server finden Sie unter [Was sind Big Data-Cluster für SQL Server 2019?](big-data-cluster-overview.md).


Die vorgestellte Erweiterung soll Ihnen einen echten Mehrwert bieten. Wir freuen uns daher über Feedback. Bitte senden Sie dieses an das [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Team](https://aka.ms/sqlfeedback).
