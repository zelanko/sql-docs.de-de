---
title: App-Bereitstellung-Erweiterung
titleSuffix: SQL Server big data clusters
description: Eine Python- oder R-Skript als eine Anwendung auf SQL Server-2019 big Data-Cluster (Vorschau) bereitstellen.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: jroth
manager: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0b0d76db3813e0a399f1ece841d729711743cbd9
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801904"
---
# <a name="how-to-use-vs-code-to-deploy-applications-to-sql-server-big-data-clusters"></a>Gewusst wie: Verwenden Sie Visual Studio Code zum Bereitstellen von Anwendungen auf SQL Server-big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Anwendungen auf einer SQL Server-big Data-Cluster mithilfe von Visual Studio-Code mit der Bereitstellung der App-Erweiterung bereitgestellt wird. Diese Funktion wurde in CTP 2.3 eingeführt. 

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Visual Studio-Code](https://code.visualstudio.com/).
- [SQL Server-big Data-Cluster](big-data-cluster-overview.md) CTP 2.3 oder höher.

## <a name="capabilities"></a>Funktionen

Diese Erweiterung unterstützt die folgenden Aufgaben in Visual Studio Code:

- Authentifizieren Sie mit SQL Server-big Data-Cluster.
- Abrufen von Anwendungsvorlagen aus GitHub-Repository für die Bereitstellung mit allen unterstützten Runtimes.
- Verwalten Sie aktuell geöffneten Anwendungsvorlagen, in dem Arbeitsbereich des Benutzers.
- Stellen Sie eine Anwendung über eine Spezifikation in YAML-Format bereit.
- Verwalten von bereitgestellten apps innerhalb von SQL Server-big Data-Cluster.
- Zeigen Sie alle apps, die Sie bereitgestellt haben, in der Seitenleiste mit zusätzlichen Informationen.
- Generieren Sie eine ausführen-Spezifikation zum Nutzen der app, oder löschen Sie die app aus dem Cluster.
- Nutzen Sie die bereitgestellten apps durch eine Ausführung YAML-Spezifikation.

Die folgenden Abschnitte führen jedoch während des Installationsvorgangs und bietet eine Übersicht über die Funktionsweise die Erweiterung. 

### <a name="install"></a>Installieren

Installieren Sie zunächst die Bereitstellung der App-Erweiterung in Visual Studio Code:

1. Herunterladen [Bereitstellen von App-Erweiterung](https://aka.ms/app-deploy-vscode) zum Installieren der Erweiterung als Teil von Visual Studio Code.

1. Starten Sie VS Code, und navigieren Sie zu der Randleiste Erweiterungen.

1. Klicken Sie auf die `…` Kontextmenü oben auf der Seitenleiste, und wählen `Install from vsix`.

   ![Installieren Sie VSIX](media/vs-extension/install_vsix.png)

1. Suchen der `sqlservbdc-app-deploy.vsix` Datei heruntergeladen, und Sie auswählen, um zu installieren.

Nach der Bereitstellung der SQL Server-big Data-Cluster-Apps Erweiterung installiert wurde, sie werden aufgefordert, VS Code neu zu laden. SQL Server BDC-App-Explorer in der Randleiste VS Code sollte nun angezeigt werden.

### <a name="app-explorer"></a>App-Explorer

Klicken Sie auf die Erweiterung in der Randleiste aus, um eine Seitenleiste, zeigt der Explorer-App zu laden. Der folgende Beispiel-Screenshot des App-Explorers zeigt keine apps oder app-Spezifikationen zur Verfügung:

<img src="media/vs-extension/app_explorer.png" width=350px></img>
<!--![App Explorer](media/vs-extension/app_explorer.png)-->

#### <a name="new-connection"></a>Neue Verbindung

Um eine Verbindung herzustellen, für den clusterendpunkt, verwenden Sie eine der folgenden Methoden:

- Klicken Sie auf der Statusleiste am unteren Rand, die besagt, `SQL Server BDC Disconnected`.
- Oder klicken Sie auf die `New Connection` Schaltfläche am Anfang der Pfeil zeigt in einem Tor.

   ![Neue Verbindung](media/vs-extension/connect_to_cluster.png)

Visual Studio Code fordert den geeigneten Endpunkt, Benutzername und Kennwort. Wenn die richtigen Anmeldeinformationen und die app-Endpunkt angegeben werden, benachrichtigt Visual Studio Code, Sie mit dem Cluster verbunden wurde haben, und Sie alle bereitgestellten apps, die in der Randleiste aufgefüllt sehen. Wenn Sie eine Verbindung herstellen, die-Endpunkt und den Benutzernamen gespeichert `./sqldbc` als Teil Ihres Benutzerprofils. Kein Kennwort oder das Token werden immer gespeichert werden. Beim erneut anmelden, wird die Eingabeaufforderung mit Ihren gespeicherten Host und den Benutzernamen vorab ausfüllen aber immer zur Eingabe eines Kennworts erforderlich. Wenn Sie an einen anderen Cluster-Endpunkt eine Verbindung herstellen möchten, klicken Sie einfach die `New Connection` erneut aus. Die Verbindung wird automatisch geschlossen, wenn Sie Visual Studio Code schließen, oder wenn Sie einen anderen Arbeitsbereich öffnen, und Sie eine Verbindung herzustellen müssen.

### <a name="app-template"></a>App-Vorlage

Um eine neue app über eine der Vorlagen bereitzustellen, klicken Sie auf die `New App Template` Schaltfläche der `App Specifications` Bereich, in dem Sie werden für den Namen, die Common Language Runtime und welche aufgefordert Speicherort, in die neue app auf Ihrem lokalen Computer platzieren möchten. Es wird empfohlen, dass Sie in Ihrem aktuellen Arbeitsbereich von Visual Studio Code platzieren, damit Sie die vollständige Funktionalität der Erweiterung können, aber Sie sie beliebig, in Ihrem lokalen Dateisystem platzieren können.

![Neue App-Vorlage](media/vs-extension/new_app_template.png)

Danach wird eine neue app-Vorlage für Sie am angegebenen Speicherort, und die Bereitstellung Gerüst `spec.yaml` in Ihrem Arbeitsbereich geöffnet. Ist das Verzeichnis, das Sie ausgewählt haben in Ihrem Arbeitsbereich, Sie sollten auch sehen, aufgeführt, unter dem `App Specifications` Bereich:

![App-Vorlage geladen](media/vs-extension/loading_app_template.png)

Die Vorlage ist eine einfache `Hello World` -app, die wie folgt angeordnet:

- **spec.yaml**
   - Weist dem Cluster wie zum Bereitstellen Ihrer app
- **run-spec.yaml**
   - Weist dem Cluster, wie Sie Ihre app aufrufen möchten
- **handler.py**
   - Dies ist der Quellcodedatei laut `src` in `spec.yaml`
   - Es wurde eine Funktion mit dem Namen `handler` , gilt die `entrypoint` der app Siehe `spec.yaml`. Er wird in eine Zeichenfolgeneingabe, die Namen `msg` und gibt die Zeichenfolgenausgabe eine mit dem Namen `out`. Diese werden angegeben `inputs` und `outputs` von der `spec.yaml`.

Wenn Sie nicht, dass eine erstellte Vorlage möchten und nur eine `spec.yaml` für die Bereitstellung einer App, die Sie die bereits erstellt haben, klicken Sie auf die `New Deploy Spec` neben der `New App Template` Schaltfläche und geht durch den gleichen Prozess, aber Sie erhalten nur die `spec.yaml`, die Sie ändern können, wie Sie auswählen.

### <a name="deploy-app"></a>Bereitstellen der App

Sie können diese App über den codelens sofort bereitstellen `Deploy App` in die `spec.yaml` , oder drücken Sie die Schaltfläche "Lightning-Ordner" neben der `spec.yaml` -Datei in das Menü "App-Spezifikationen". Die Erweiterung wird zippen Sie alle Dateien im Verzeichnis, in dem Ihre `spec.yaml` befindet und Bereitstellen Ihrer app für den Cluster. 

>[!NOTE]
>Stellen Sie sicher, dass alle Dateien Ihrer Anwendung im gleichen Verzeichnis wie sind Ihre `spec.yaml`. Die `spec.yaml` muss auf der Stammebene von Ihrer app Quellcodeverzeichnis sein. 

![App-Schaltfläche "Bereitstellen"](media/vs-extension/deploy_app_lightning.png)

![Bereitstellen von App-CodeLens](media/vs-extension/deploy_app_codelens.png)

Sie werden benachrichtigt, wenn die app zur Nutzung, die abhängig vom Status der app in der Randleiste bereit ist:

![App-Bereitstellung](media/vs-extension/app_deploy.png)

![App kann jetzt-Seitenleiste](media/vs-extension/app_ready_side_bar.png)

![Bereit für die App-Benachrichtigung](media/vs-extension/app_ready_notification.png)

Klicken Sie im Bereich "Seite" werden Sie für Sie verfügbaren Folgendes angezeigt:

Sie können alle apps, die von die Ihnen bereitgestellte anzeigen, in der Seitenleiste mit den folgenden Informationen:

- state
- version
- Eingabeparameter
- Output-Parameter
- Verknüpfungen
  - Swagger
  - Details

Wenn Sie auf `Links`, sehen Sie, dass Sie zugreifen können, die `swagger.json` Ihrer bereitgestellten App, damit Sie Ihren eigenen Kunden schreiben können, die Ihre app aufrufen:

![Swagger](media/vs-extension/swagger.png)

Finden Sie unter [Anwendungen für big Data-Cluster nutzen](big-data-cluster-consume-apps.md) für Weitere Informationen.

### <a name="app-run"></a>App-Ausführung

Sobald die app bereit ist, rufen Sie die app mit der `run-spec.yaml` , die als Teil der app-Vorlage angegeben wurde:

![Führen Sie die Spezifikation](media/vs-extension/run_spec.png)

Geben Sie eine beliebige Zeichenfolge, die Sie anstelle von möchten `hello` und dann erneut führen Sie es über den codelens-Link oder die Schaltfläche "Lightning" in der Seitenleiste neben der `run-spec.yaml`. Wenn Sie eine ausführen-Spezifikation aus irgendeinem Grund nicht haben, generieren Sie aus der bereitgestellten app im Cluster:

![Abrufen von Durchläufen Sie Spezifikation](media/vs-extension/get_run_spec.png)

Nachdem Sie einen aufweisen und zu Ihrer Zufriedenheit bearbeitet haben, führen Sie ihn. Visual Studio Code gibt das entsprechende Feedback zurück, wenn die app ausgeführt wurde:

![App-Ausgabe](media/vs-extension/app_output.png)

Wie Sie oben sehen können, erhält die Ausgabe in eine temporäre `.json` Datei in Ihrem Arbeitsbereich. Wenn Sie diese Ausgabe zu behalten, können Sie sie speichern möchten, wird hingegen er auf die schließende gelöscht werden. Wenn Ihre app keine Ausgabe in eine Datei ausgegeben wurde, erhalten Sie nur die `Successful App Run` Benachrichtigung unten. Wenn Sie bei einer erfolgreiche Ausführung keinen, erhalten Sie eine entsprechende Fehlermeldung angezeigt, mit denen Sie bestimmen, was falsch ist.

Wenn eine app ausführen, gibt es eine Vielzahl von Möglichkeiten zum Übergeben von Parametern:

Sie können angeben, dass alle Eingaben, die erforderlich sind, über eine `.json`, d. h.:

- `inputs: ./example.json`

Beim Aufrufen einer bereitgestellten app, wenn keine Eingabeparameter ausgeprägten oder Benutzer, die angegeben werden, und geben Sie, dass die angegebene input-Parameters etwas anderes als ein primitiver Typ, z. B. ein Array, Vektor, Datenframe abgerufen wird ist, komplexe JSON- usw. der Parametertyp direkt in Zeile wann die app, aufrufen d. h.:

- Vektor
    - `inputs:`
        - `x: [1, 2, 3]`
- Matrix
    - `inputs:`
        - `x: [[A,B,C],[1,2,3]]`
- Objekt
    - `inputs:`
        - `x: {A: 1, B: 2, C: 3}`

Oder geben Sie eine Zeichenfolge als relative oder absolute Dateipfad zu einer `.txt`, `.json`, oder `.csv` , die die erforderliche Eingabe erhalten, in dem Format, das Ihre app benötigt. Analysieren der Datei basiert auf `Node.js Path library`, bei dem Pfad zu einer Datei, als definiert ist eine `string that contains a / or \ character`.

Wenn es sich bei Bedarf input-Parameters nicht bereitgestellt wird, wird eine entsprechende Fehlermeldung mit dem falschen Dateipfad angezeigt werden, wenn es sich bei ein Zeichenfolge-Dateipfad wurde oder diesen Parameter war ungültig. Die Verantwortung wird an den Ersteller der app zugewiesen, um sicherzustellen, dass sie die Parameter verstehen, die sie definieren.

Löschen einer app, klicken Sie einfach auf das Papierkorbsymbol können auf die Schaltfläche neben der app in der `Deployed Apps` Seitenbereich.

## <a name="next-steps"></a>Nächste Schritte

Informationen zur Integration von apps, die auf SQL Server, die in Ihren eigenen Anwendungen auf big Data-Cluster bereitgestellten [Anwendungen für big Data-Cluster nutzen](big-data-cluster-consume-apps.md) für Weitere Informationen. Außerdem sehen Sie sich an den zusätzlichen Beispielen [Beispiele für das Bereitstellen von Apps](https://aka.ms/sql-app-deploy) , mit der Erweiterung zu testen.

Weitere Informationen zu SQL Server-big Data-Clustern, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).


Unser Ziel ist es, diese Erweiterung für Sie nützlich zu gestalten, und wir schätzen Sie Feedback. Bitte senden Sie diese an [ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Team](https://aka.ms/sqlfeedback).
