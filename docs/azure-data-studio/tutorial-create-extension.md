---
title: 'Tutorial: Erstellen einer Erweiterung'
titleSuffix: Azure Data Studio
description: In diesem Tutorial wird veranschaulicht, wie eine Erweiterung zum Hinzufügen von benutzerdefinierten Funktionen in Azure Data Studio erstellt wird.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: kevcunnane
ms.author: kcunnane
ms.openlocfilehash: c7c247e739a9b983dd715844262794bd18fca9cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959083"
---
# <a name="tutorial-create-an-azure-data-studio-extension"></a>Tutorial: Erstellen Sie eine Azure Data Studio-Erweiterung

Dieses Tutorial veranschaulicht, wie eine neue Azure Data Studio-Erweiterung. Die Erweiterung erstellt vertraute tastenbindungen für SSMS in Azure Data Studio.

In diesem Tutorial erfahren Sie, wie Sie:
> [!div class="checklist"]
> * Erstellen eines Erweiterungsprojekts
> * Installieren des Erweiterung-Generators
> * Erstellen Sie die Erweiterung
> * Testen Sie die Erweiterung
> * Packen Sie die Erweiterung
> * Die Erweiterung auf Marketplace veröffentlichen

## <a name="prerequisites"></a>Vorraussetzungen

Azure Data Studio aufbaut, in demselben Framework als Visual Studio Code-Erweiterungen für Azure Data Studio mithilfe von Visual Studio-Code erstellt werden. Zunächst benötigen Sie die folgenden Komponenten:

- [Node.js](https://nodejs.org) installiert und kann in Ihrem `$PATH`. Von Node.js umfasst [Npm](https://www.npmjs.com/), den Node.js-Paket-Manager, die verwendet wird, um den Generator für die Erweiterung zu installieren.
- [Visual Studio Code](https://code.visualstudio.com) zum Debuggen der Erweiterung.
- Azure Data Studio [Debuggen Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sqlops-debug) (optional). Dadurch können Sie die Erweiterung ohne Packen und installieren Sie es in Azure Data Studio testen.
- Stellen Sie sicher `azuredatastudio` befindet sich in Ihrem Pfad. Für Windows, stellen Sie sicher, dass Sie auswählen, die `Add to Path` -Option in setup.exe. Führen Sie für Mac oder Linux, die *Installationsbefehl "Azuredatastudio" im Pfad* Option.


## <a name="install-the-extension-generator"></a>Installieren des Erweiterung-Generators

Um den Prozess der Erstellung von Erweiterungen zu vereinfachen, haben wir erstellt eine [Erweiterung Generator](https://code.visualstudio.com/docs/extensions/yocode) mithilfe von Yeoman. Um es zu installieren, führen Sie Folgendes an der Eingabeaufforderung ein:

`npm install -g yo generator-azuredatastudio`

## <a name="create-your-extension"></a>Erstellen Sie die Erweiterung

So erstellen Sie eine Erweiterung:

1. Starten Sie den Generator Erweiterung mit dem folgenden Befehl ein:

   `yo azuredatastudio`

2. Wählen Sie **neue Tastaturlayout** aus der Liste der Erweiterungstypen:

   ![Extension-generator](./media/tutorial-create-extension/extension-generator.png)

3. Führen Sie die Schritte zum Ausfüllen der Name der Erweiterung (verwenden Sie für dieses Tutorial **ssmskeymap2**), und eine Beschreibung hinzufügen.

Die vorherigen Schritte erstellt einen neuen Ordner. Öffnen der Ordner in Visual Studio Code, und Sie können nun Ihre eigenen tastenzuordnung-Erweiterung zu erstellen.


### <a name="add-a-keyboard-shortcut"></a>Fügen Sie eine Tastenkombination hinzu.

**Schritt 1: Suchen Sie die Verknüpfungen zu ersetzen**

Nun, da wir unsere Erweiterung bereit haben, fügen Sie einige SSMS Tastatur Verknüpfungen (oder Keybindings) in Studio für Azure Data. Ich verwendet habe [Andy Mallon Spickzettel](https://am2.co/2018/02/updated-cheat-sheet/) und RedGates Tastatur Verknüpfungen Liste inspirieren.

Die wichtigsten Dinge, die fehlende aufgetreten waren:

- Führen Sie eine Abfrage, mit der tatsächlichen Ausführungsplans aktiviert. Dies ist **STRG + M** in SSMS und eine Bindung kann in Azure Data Studio verfügt nicht über.
- Mit **STRG + UMSCHALT + E** als zweite Möglichkeit der Ausführung einer Abfrage. Feedback von Benutzern angegeben, dass dies nicht vorhanden war.
- Mit **ALT + F1** ausführen `sp_help`. Wir dies in Azure Data Studio hinzugefügt, aber da die Bindung bereits verwendet wurde, zugeordnet wir damit **ALT + F2** stattdessen.
- Vollbild umschalten (**UMSCHALT + ALT + Eingabe**).
- **F8** anzuzeigenden **Objekt-Explorer** / **Ansicht**.

Es ist leicht zu finden und Ersetzen Sie diese tastaturzuordnungen. Führen Sie *Öffnen von Tastenkombinationen* anzuzeigenden der **Tastenkombinationen in Visual Studio** Registerkarte in Azure Data Studio, suchen Sie nach *Abfrage* und wählen Sie dann **Änderungsschlüssel Bindung**. Wenn Sie fertig sind ändern die tastenzuordnung, sehen Sie die aktualisierte Zuordnung in der Datei "KeyBindings.JSON" (ausführen *öffnen Tastenkombinationen* angezeigt).

![Tastenkombinationen](./media/tutorial-create-extension/keyboard-shortcuts.png)

![Erweiterung der Datei "KeyBindings.JSON"](./media/tutorial-create-extension/keybindings-json.png)


**Schritt 2: Hinzufügen von Verknüpfungen mit der Erweiterung**

Um Tastenkombinationen für die Erweiterung hinzuzufügen, öffnen die *"Package.JSON"* (in der Erweiterung)-Datei und Ersetzen Sie die `contributes` -Abschnitt folgendermaßen:

```json
"contributes": {
  "keybindings": [
    {
      "key": "shift+cmd+e",
      "command": "runQueryKeyboardAction"
    },
    {
      "key": "ctrl+cmd+e",
      "command": "workbench.view.explorer"
    },
    {
      "key": "alt+f1",
      "command": "workbench.action.query.shortcut1"
    },
    {
      "key": "shift+alt+enter",
      "command": "workbench.action.toggleFullScreen"
    },
    {
      "key": "f8",
      "command": "workbench.view.connections"
    },
    {
      "key": "ctrl+m",
      "command": "runCurrentQueryWithActualPlanKeyboardAction"
    }
  ]
}
```

## <a name="test-your-extension"></a>Testen Sie die Erweiterung

Stellen Sie sicher `azuredatastudio` befindet sich in Ihrem Pfad mithilfe des Befehls installieren Azuredatastudio im Pfad-Befehl in Azure Data Studio.

Stellen Sie sicher, dass die Erweiterung mit Azure Data Studio Debuggen in Visual Studio Code installiert ist.

Wählen Sie **F5** Studio für Azure Data im Debugmodus gestartet, mit der Erweiterung ausgeführt wird:

![Installieren der Erweiterung](./media/tutorial-create-extension/install-extension.png)

![Testen der Erweiterung](./media/tutorial-create-extension/test-extension.png)

Wichtige Zuordnungen sind eine der schnellsten Erweiterungen zu erstellen, damit die neue Erweiterung jetzt erfolgreich funktionsfähig und teilen möchten sein sollten.

## <a name="package-your-extension"></a>Packen Sie die Erweiterung

Mit anderen Teilen, Sie die Erweiterung in eine einzelne Datei zu packen müssen. Dies kann im Azure Data Studio-Erweiterung Marketplace veröffentlicht, oder für Ihr Team oder der Community gemeinsam verwendet. Zu diesem Zweck müssen Sie ein weiteres Npm-Paket über die Befehlszeile zu installieren:

`npm install -g vsce`

Navigieren Sie zu das Basisverzeichnis der Erweiterung, und führen `vsce package`. Ich musste ein paar zusätzlichen Zeilen zum Beenden hinzufügen der *Vsce* -Tool von beschweren:

```json
"repository": {
    "type": "git",
    "url": "https://github.com/kevcunnane/ssmskeymap.git"
},
"bugs": {
    "url": "https://github.com/kevcunnane/ssmskeymap/issues"
},
```

Sobald dies geschehen ist, war Meine Ssmskeymap-0.1.0.vsix-Datei erstellt und ist bereit zum Installieren und mit der Welt Teilen!

![Installieren der Erweiterung](./media/tutorial-create-extension/extensions.png)


## <a name="publish-your-extension-to-the-marketplace"></a>Die Erweiterung auf Marketplace veröffentlichen

Studio für Azure Data Marketplace-Erweiterung ist völlig noch nicht implementiert, aber der aktuelle Prozess wird zum Hosten der Erweiterungs VSIX an einer beliebigen Stelle (z. B. eine GitHub-Release-Seite) senden dann einen Pull Request aktualisieren [diese JSON-Datei](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) mit Ihrem die Erweiterungsinformationen.


## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Erstellen eines Erweiterungsprojekts
> * Installieren des Erweiterung-Generators
> * Erstellen Sie die Erweiterung
> * Testen Sie die Erweiterung
> * Packen Sie die Erweiterung
> * Die Erweiterung auf Marketplace veröffentlichen


Wir hoffen, dass nach dem Lesen Sie zum Erstellen von eigenen Erweiterungen für Azure Data Studio inspiriert werden. Wir haben Unterstützung für die Dashboard-Informationen (pretty Diagramme, die für Ihre SQL Server ausgeführt), eine Reihe von SQL-spezifische APIs und einer großen vorhandenen Satz von Erweiterungspunkten, die von Visual Studio Code geerbt.

Wenn Sie eine Vorstellung davon haben, aber nicht sicher sind, wie Sie beginnen, öffnen Sie ein Problem oder einen Tweet an das Team: [Azuredatastudio](https://twitter.com/azuredatastudio).

Sie verweisen immer auf die [Leitfaden für Visual Studio Code-Erweiterung](https://code.visualstudio.com/docs/extensions/overview) da hierin sind alle vorhandenen APIs und Muster.


Informationen zum Arbeiten mit T-SQL in Azure Data Studio, schließen Sie das T-SQL-Editor-Tutorial:

> [!div class="nextstepaction"]
> [Verwenden Sie den Transact-SQL-Editor zum Erstellen von Datenbankobjekten](tutorial-sql-editor.md).
