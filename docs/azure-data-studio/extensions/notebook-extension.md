---
title: Entwickeln einer Jupyter Notebook-Erweiterung
description: Hier erfahren Sie, wie Sie Notebooks mit dem Erweiterungs-Generator in eine Erweiterung packen.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: 52a38a8074814737a30cb2f31d22da922eb76901
ms.sourcegitcommit: b6ee0d434b3e42384b5d94f1585731fd7d0eff6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89288152"
---
# <a name="create-a-jupyter-notebook-extension"></a>Entwickeln einer Jupyter Notebook-Erweiterung

Dieses Tutorial veranschaulicht, wie Sie eine neue Azure Data Studio-Erweiterung für Notebooks entwickeln. Die Erweiterung enthält ein Beispiel für eine Jupyter Notebook-Instanz, die in Azure Data Studio geöffnet und ausgeführt werden kann.

In diesem Tutorial lernen Sie Folgendes:
> [!div class="checklist"]
> - Erstellen eines Erweiterungsprojekts
> - Installieren des Erweiterungsgenerators
> - Entwickeln einer Notebook-Erweiterung
> - Ausführen der Erweiterung
> - Packen der Erweiterung
> - Veröffentlichen der Erweiterung im Marketplace

## <a name="apis-used"></a>Verwendete APIs

- `azdata.nb.showNotebookDocument`

### <a name="extension-use-cases"></a>Anwendungsfälle für Erweiterungen

Es gibt verschiedene Gründe, eine Notebook-Erweiterung zu entwickeln: 
- Freigeben interaktiver Dokumentationen 
- Speichern des Notebooks und dauerhafter Zugriff auf dieses
- Programmieranweisungen für Benutzer
- Versionserstellung und Nachverfolgung von Notebook-Updates

## <a name="prerequisites"></a>Voraussetzungen

Azure Data Studio ist auf dem gleichen Framework wie Visual Studio Code aufgebaut, sodass Erweiterungen für Azure Data Studio mithilfe von Visual Studio Code erstellt werden. Sie benötigen die folgenden Komponenten:

- [Node.js](https://nodejs.org) – installiert und in Ihrem `$PATH` verfügbar. Node.js enthält [npm](https://www.npmjs.com/), den Node.js-Paket-Manager, der zum Installieren des Erweiterungsgenerators verwendet wird.
- [Visual Studio Code](https://code.visualstudio.com) zum Debuggen der Erweiterung.
- Stellen Sie sicher, dass sich `azuredatastudio` in Ihrem Pfad befindet. Wenn Sie unter Windows arbeiten, wählen Sie in „setup.exe“ die Option `Add to Path` aus. Wenn Sie unter Mac oder Linux arbeiten, führen Sie die Option *azuredatastudio-Befehl in PATH installieren* aus.

## <a name="install-the-extension-generator"></a>Installieren des Erweiterungsgenerators

Um den Prozess der Erstellung von Erweiterungen zu vereinfachen, haben wir einen [Erweiterungsgenerator](https://www.npmjs.com/package/generator-azuredatastudio) erstellt, der Yeoman verwendet. Um diesen zu installieren, führen Sie an der Eingabeaufforderung folgenden Befehl aus:

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-extension"></a>Erstellen der Erweiterung

So erstellen Sie eine Erweiterung:

1. Starten Sie den Erweiterungsgenerator mit dem folgenden Befehl:

   `yo azuredatastudio`

2. Wählen Sie **New Notebooks (Individual)** (Neue Notebooks (einzeln)) aus der Liste der Erweiterungstypen aus:

   :::image type="content" source="media/notebook-extension/notebook-extension-generator.png" alt-text="Erweiterungs-Generator für Notebooks":::

3. Befolgen Sie die Schritte zum Angeben des Erweiterungsnamens (verwenden Sie für dieses Tutorial **Test Notebook**), des Herausgebernamen (verwenden Sie für dieses Tutorial **Microsoft**) und einer Beschreibung.

Nun haben Sie die Wahl, ob Sie bereits erstellte Jupyter Notebook-Instanzen hinzufügen möchten, oder ob Sie die über den Generator bereitgestellten Beispiel-Notebooks verwenden möchten.

Verwenden Sie für dieses Tutorial ein Python-Beispiel-Notebook:

   :::image type="content" source="media/notebook-extension/notebook-sample-generator.png" alt-text="Python-Beispiel auswählen":::

Wenn Sie Notebooks übertragen möchten, wählen Sie die entsprechende Option aus, und geben Sie den absoluten Pfad an, an dem Ihre Notebooks oder Markdowndateien gespeichert sind.

Wenn Sie die vorherigen Schritte abschließen, wird ein neuer Ordner mit dem Beispiel-Notebook erstellt. Öffnen Sie den Ordner in Visual Studio Code. Nun sind Sie bereit, selbst eine Notebook-Erweiterung zu entwickeln.

## <a name="understanding-your-extension"></a>Grundlegendes zu Ihrer Erweiterung

Ihr Projekt sollte derzeit wie folgt aussehen:

   :::image type="content" source="media/notebook-extension/notebook-file-structure-generator.png" alt-text="Dateistruktur der Erweiterung":::

`vsc-extension-quickstart.md` enthält einen Verweis auf die wichtigen Dateien. In `README.md` können Sie die Dokumentation für Ihre neue Erweiterung bereitstellen. Beachten Sie die Dateien `package.json`, `notebook.ts` und `pySample.ipynb`.

Wenn Dateien oder Ordner vorhanden sind, die Sie nicht veröffentlichen möchten, können Sie deren Namen in die Datei `.vscodeignore` einschließen.

Werfen wir einen Blick auf `notebook.ts`, um zu verstehen, was unsere neu erstellte Erweiterung bewirkt.

```javascript
// This function is called when you run the command `Launch Notebooks: Test Notebook` from
// command palette in Azure Data Studio. If you would like any additional functionality
// to occur when you launch the book, add to the activate function.
export function activate(context: vscode.ExtensionContext) {
    context.subscriptions.push(vscode.commands.registerCommand('launchNotebooks.test-notebook', () => {
        let notebooksToDisplay: Array<string> = processNotebooks();
        notebooksToDisplay.forEach(name => {
            azdata.nb.showNotebookDocument(vscode.Uri.file(name));
        });
    }));

    // Add other code here if you want to register another command
}
```

Das ist die Hauptfunktion in `notebook.ts`. Diese wird immer dann aufgerufen, wenn die Erweiterung über den Befehl **Launch Notebooks: Test Notebook** (Notebook starten: Notebook testen) ausgeführt wird. Erstellen Sie den neuen Befehl mithilfe der API `vscode.commands.registerCommand`. Die Definition in den geschweiften Klammern entspricht dem Code, der bei jedem Aufruf des Befehls ausgeführt wird. Jedes Notebook, das von der Funktion `processNotebooks` ermittelt wird, kann in Azure Data Studio über `azdata.nb.showNotebookDocument` geöffnet werden. 

Die Datei `package.json` spielt außerdem eine wichtige Rolle beim Registrieren eines Befehls wie **Launch Notebooks: Test Notebook** (Notebook starten: Notebook testen).

```json
"activationEvents": [
        "onCommand:launchNotebooks.test-notebook"
    ],
    "main": "./out/notebook.js",
    "contributes": {
        "commands": [
            {
                "command": "launchNotebooks.test-notebook",
                "title": "Launch Notebooks: Test Notebook"
            }
        ]
    }
```

Für den Befehl sind nun ein Aktivierungsereignis und spezifische Beitragspunkte vorhanden. Diese werden im Marketplace für Erweiterungen angezeigt. Dort werden Erweiterungen für Benutzer veröffentlicht. Wenn Sie weitere Befehle hinzufügen, müssen Sie diese auch dem Feld `activationEvents` hinzufügen. Weitere Optionen finden Sie unter [Aktivierungsereignisse](https://code.visualstudio.com/api/references/activation-events).

## <a name="package-your-extension"></a>Packen der Erweiterung

Um Ihre Erweiterung für andere Benutzer freizugeben, müssen Sie sie in eine einzige Datei packen. Diese kann im Marketplace für Azure Data Studio-Erweiterungen veröffentlicht oder für Ihr Team oder Ihre Community freigegeben werden. Zu diesem Zweck müssen Sie über die Befehlszeile ein weiteres npm-Paket installieren:

```console
`npm install -g vsce`
```

Bearbeiten Sie `README.md` wie gewünscht, und navigieren Sie dann zum Basisverzeichnis der Erweiterung, und führen Sie `vsce package` aus. Optional können Sie ein Repository mit ihrer Erweiterung verknüpfen oder den Vorgang ohne Repository fortsetzen. Um ein Repository hinzuzufügen, fügen Sie der Datei `package.json` eine ähnliche Zeile hinzu.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/laurajjiang/testnotebook.git"
}
```

Nun ist die Datei „my-test-notebook-0.0.1.vsix“ erstellt und kann installiert und veröffentlicht werden.

## <a name="run-your-extension"></a>Ausführen der Erweiterung

Um die Erweiterung auszuführen und zu testen, öffnen Sie Azure Data Studio, und öffnen Sie dann die Befehlspalette (`Ctrl + Shift + P`). Suchen Sie nach dem Befehl **Extensions: Install from VSIX** (Erweiterungen: Aus VSIX installieren), und navigieren Sie zu dem Ordner, der die neue Erweiterung enthält.

   :::image type="content" source="media/notebook-extension/install-vsix.png" alt-text="Installieren über VSIX":::

Sie sollte nun in Ihrem Erweiterungsbereich in Azure Data Studio angezeigt werden. Öffnen Sie die Befehlspalette noch mal. Dort sehen Sie den neuen Befehl, den Sie mit der Erweiterung erstellt haben: **Launch Notebook: Test Notebook** (Notebook starten: Notebook testen). Bei der Ausführung sollte das Jupyter Book geöffnet werden, das wir mit unserer Erweiterung gepackt haben.

   :::image type="content" source="media/notebook-extension/notebook-launch-ads.png" alt-text="Notebook-Befehl":::

Herzlichen Glückwunsch! Sie haben Ihre erste Jupyter Notebook-Erweiterung entwickelt und können sie jetzt bereitstellen.

## <a name="publish-your-extension-to-the-marketplace"></a>Veröffentlichen der Erweiterung im Marketplace

Der Marketplace für Azure Data Studio-Erweiterungen ist noch nicht vollständig implementiert. Zum Veröffentlichen hosten Sie die VSIX-Datei der Erweiterung irgendwo (z. B. auf einer GitHub-Releaseseite) und senden eine PR, die [diese JSON-Datei](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) mit ihren Erweiterungsinformationen aktualisiert.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie Folgendes gelernt:
> [!div class="checklist"]
> - Erstellen eines Erweiterungsprojekts
> - Installieren des Erweiterungs-Generators – Entwickeln einer Notebook-Erweiterung
> - Erstellen der Erweiterung
> - Packen der Erweiterung
> - Veröffentlichen der Erweiterung im Marketplace

Wir hoffen, dass dieser Artikel Sie auch dazu inspiriert, selbst eine Erweiterung für Azure Data Studio zu erstellen.

Wenn Sie eine Idee haben, aber nicht sicher sind, wo Sie anfangen sollen, eröffnen Sie ein Issue, oder senden Sie einen Tweet an das Team: [azuredatastudio](https://twitter.com/azuredatastudio).

Sie können jederzeit im [Visual Studio Code-Erweiterungsleitfaden](https://code.visualstudio.com/docs/extensions/overview) nachschlagen, dieser enthält alle vorhandenen APIs und Muster.