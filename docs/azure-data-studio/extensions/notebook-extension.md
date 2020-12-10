---
title: Entwickeln einer Jupyter Notebook-Erweiterung
description: Hier erfahren Sie, wie Sie Notebooks mit dem Erweiterungs-Generator in eine Erweiterung packen.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: 44080250d95d21cecca16ff605ca22683e5b4440
ms.sourcegitcommit: 7f76975c29d948a9a3b51abce564b9c73d05dcf0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96900813"
---
# <a name="create-a-jupyter-notebook-extension"></a>Entwickeln einer Jupyter Notebook-Erweiterung

Dieses Tutorial veranschaulicht, wie Sie eine neue Azure Data Studio-Erweiterung für Jupyter Notebook erstellen. Die Erweiterung enthält ein Beispiel für eine Jupyter Notebook-Instanz, die in Azure Data Studio geöffnet und ausgeführt werden kann.

In diesem Artikel wird Folgendes behandelt:

> [!div class="checklist"]
> - Erstellen eines Erweiterungsprojekts
> - Installieren des Erweiterungs-Generators
> - Entwickeln einer Notebookerweiterung
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
- Stellen Sie sicher, dass sich `azuredatastudio` in Ihrem Pfad befindet. Wenn Sie unter Windows arbeiten, wählen Sie in „setup.exe“ die Option **Zu PATH hinzufügen** aus. Wenn Sie unter Mac oder Linux arbeiten, führen Sie die Option **azuredatastudio-Befehl in PATH installieren** aus.

## <a name="install-the-extension-generator"></a>Installieren des Erweiterungsgenerators

Um den Prozess der Erstellung von Erweiterungen zu vereinfachen, haben wir einen [Erweiterungsgenerator](https://www.npmjs.com/package/generator-azuredatastudio) erstellt, der Yeoman verwendet. Um diesen zu installieren, führen Sie an der Eingabeaufforderung den folgenden Befehl aus:

```console
npm install -g yo generator-azuredatastudio
```

## <a name="create-your-extension"></a>Erstellen der Erweiterung

So erstellen Sie eine Erweiterung:

1. Starten Sie den Erweiterungs-Generator mit dem folgenden Befehl:

   `yo azuredatastudio`

2. Wählen Sie **New Notebooks (Individual)** (Neue Notebooks (einzeln)) aus der Liste der Erweiterungstypen aus:

   :::image type="content" source="media/notebook-extension/notebook-extension-generator.png" alt-text="Erweiterungs-Generator für Notebooks":::

3. Führen Sie die Schritte zum Ausfüllen des Erweiterungsnamens aus. Verwenden Sie für dieses Tutorial den Namen **Test Notebook**. Geben Sie dann einen Herausgebernamen ein. Verwenden Sie für dieses Tutorial **Microsoft**. Geben Sie schließlich eine Beschreibung ein.

An dieser Stelle gibt es einige Verzweigungen. Sie können entweder bereits erstellte Jupyter Notebook-Instanzen hinzufügen oder die über den Generator bereitgestellten Beispielnotebooks verwenden.

Verwenden Sie für dieses Tutorial ein Python-Beispielnotebook:

   :::image type="content" source="media/notebook-extension/notebook-sample-generator.png" alt-text="Python-Beispiel auswählen":::

Wenn Sie über Notebooks verfügen, die Sie gern verwenden würden, geben Sie dies als Antwort an. Geben Sie den absoluten Dateipfad an, unter dem alle Notebooks oder Markdowndateien gespeichert sind.

Wenn Sie die vorherigen Schritte abschließen, wird ein neuer Ordner mit dem Beispiel-Notebook erstellt. Öffnen Sie den Ordner in Visual Studio Code. Nun sind Sie bereit, selbst eine Notebookerweiterung zu entwickeln.

## <a name="understand-your-extension"></a>Informationen zur Erweiterung

Ihr Projekt sollte derzeit wie folgt aussehen:

   :::image type="content" source="media/notebook-extension/notebook-file-structure-generator.png" alt-text="Dateistruktur der Erweiterung":::

Die Datei `vsc-extension-quickstart.md` enthält einen Verweis auf die wichtigen Dateien. In der Datei `README.md` können Sie die Dokumentation für Ihre neue Erweiterung bereitstellen. Beachten Sie die Dateien `package.json`, `notebook.ts` und `pySample.ipynb`.

Wenn Dateien oder Ordner vorhanden sind, die Sie nicht veröffentlichen möchten, können Sie deren Namen in die Datei `.vscodeignore` einschließen.

Werfen wir einen Blick auf `notebook.ts`, um zu verstehen, was unsere neu erstellte Erweiterung bewirkt.

```javascript
// This function is called when you run the command `Launch Notebooks: Test Notebook` from the
// command palette in Azure Data Studio. If you want any additional functionality
// to occur when you launch the book, add it to the activate function.
export function activate(context: vscode.ExtensionContext) {
    context.subscriptions.push(vscode.commands.registerCommand('launchNotebooks.test-notebook', () => {
        let notebooksToDisplay: Array<string> = processNotebooks();
        notebooksToDisplay.forEach(name => {
            azdata.nb.showNotebookDocument(vscode.Uri.file(name));
        });
    }));

    // Add other code here if you want to register another command.
}
```

Das ist die Hauptfunktion in `notebook.ts`. Diese wird immer dann aufgerufen, wenn die Erweiterung über den folgenden Befehl ausgeführt wird: **Launch Notebooks: Test Notebook** (Notebook starten: Notebook testen). Wir erstellen den neuen Befehl mithilfe der API `vscode.commands.registerCommand`. Die folgende Definition in geschweiften Klammern ist der Code, der jedes Mal ausgeführt wird, wenn der Befehl aufgerufen wird. Jedes Notebook, das von der Funktion `processNotebooks` ermittelt wird, kann in Azure Data Studio über `azdata.nb.showNotebookDocument` geöffnet werden.

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

Für den Befehl sind nun ein Aktivierungsereignis und spezifische Beitragspunkte vorhanden. Diese Beitragspunkte werden im Marketplace für Erweiterungen angezeigt. Dort werden Erweiterungen für Benutzer veröffentlicht. Wenn Sie weitere Befehle hinzufügen, müssen Sie diese auch dem Feld `activationEvents` hinzufügen. Weitere Optionen finden Sie unter [Aktivierungsereignisse](https://code.visualstudio.com/api/references/activation-events).

## <a name="package-your-extension"></a>Packen der Erweiterung

Um Ihre Erweiterung für andere Benutzer freizugeben, müssen Sie sie in eine einzelne Datei packen. Ihre Erweiterung kann im Marketplace für Azure Data Studio-Erweiterungen veröffentlicht oder für Ihr Team oder Ihre Community freigegeben werden. Zu diesem Zweck müssen Sie über die Befehlszeile ein weiteres npm-Paket installieren.

```console
npm install -g vsce
```

Bearbeiten Sie die `README.md`-Datei nach Ihren Wünschen. Navigieren Sie anschließend zum Basisverzeichnis der Erweiterung, und führen Sie `vsce package` aus. Optional können Sie ein Repository mit ihrer Erweiterung verknüpfen oder den Vorgang ohne Repository fortsetzen. Um ein Repository hinzuzufügen, fügen Sie der Datei `package.json` eine ähnliche Zeile hinzu.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/laurajjiang/testnotebook.git"
}
```

Sobald diese Zeilen hinzugefügt werden, wird die Datei `my test-notebook-0.0.1.vsix` erstellt und ist nun für die Installation bereit und kann geteilt werden.

## <a name="run-your-extension"></a>Ausführen der Erweiterung

Um die Erweiterung auszuführen und zu testen, öffnen Sie Azure Data Studio, und öffnen Sie dann die Befehlspalette, indem Sie **STRG+UMSCHALT+P** drücken. Suchen Sie nach dem Befehl **Extensions: Install from VSIX** (Erweiterungen: Aus VSIX installieren), und navigieren Sie zu dem Ordner, der die neue Erweiterung enthält.

   :::image type="content" source="media/notebook-extension/install-vsix.png" alt-text="Installieren über VSIX":::

Ihre Erweiterung sollte nun in Ihrem Erweiterungsbereich in Azure Data Studio angezeigt werden. Öffnen Sie die Befehlspalette noch mal. Dort sehen Sie den neuen Befehl, den Sie mit der Erweiterung erstellt haben: **Launch Notebook: Test Notebook** (Notebook starten: Notebook testen). Bei der Ausführung sollte das Jupyter Book geöffnet werden, das wir mit unserer Erweiterung gepackt haben.

   :::image type="content" source="media/notebook-extension/notebook-launch-ads.png" alt-text="Notebook-Befehl":::

Herzlichen Glückwunsch! Sie haben Ihre erste Jupyter Notebook-Erweiterung entwickelt und können sie jetzt bereitstellen.

## <a name="publish-your-extension-to-the-marketplace"></a>Veröffentlichen der Erweiterung im Marketplace

Der Marketplace für Azure Data Studio-Erweiterungen befindet sich in Bearbeitung. Zum Veröffentlichen hosten Sie die Erweiterung VSIX an einem beliebigen Ort, z. B. auf einer GitHub-Releaseseite. Senden Sie anschließend einen Pull Request, der [diese JSON-Datei](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) mit Ihren Erweiterungsinformationen aktualisiert.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie Folgendes gelernt:
> [!div class="checklist"]
> - Erstellen eines Erweiterungsprojekts
> - Installieren des Erweiterungs-Generators
> - Entwickeln einer Notebookerweiterung
> - Erstellen der Erweiterung
> - Packen der Erweiterung
> - Veröffentlichen der Erweiterung im Marketplace

Hoffentlich hat Sie dieser Artikel dazu inspiriert, selbst eine Erweiterung für Azure Data Studio zu erstellen.

Wenn Sie eine Idee haben, aber nicht sicher sind, wie Sie anfangen sollen, erstellen Sie ein Issue, oder senden Sie einen Tweet an das Team unter [azuredatastudio](https://twitter.com/azuredatastudio).

Weitere Informationen finden Sie im [Visual Studio Code-Erweiterungsleitfaden](https://code.visualstudio.com/docs/extensions/overview). Dieser enthält alle vorhandenen APIs und Muster.
