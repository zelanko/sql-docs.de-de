---
title: Erstellen von Erweiterungen
description: Sie können Funktionen mithilfe einer Erweiterung zu Azure Data Studio hinzufügen. Hier erfahren Sie, wie Sie eine Erweiterung erstellen und im Erweiterungskatalog veröffentlichen.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu
ms.custom: seodec18
ms.date: 08/26/2020
ms.openlocfilehash: 477e93dc272c4a26e40333b02728c643299161ce
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283717"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Erweitern der Funktionalität durch Erstellen von Erweiterungen zu Azure Data Studio

Erweiterungen in Azure Data Studio bieten eine einfache Möglichkeit, der Basisinstallation von Azure Data Studio weitere Funktionen hinzuzufügen.

Erweiterungen werden vom Azure Data Studio-Team (Microsoft) sowie von der Drittanbietercommunity (Ihnen!) bereitgestellt.

## <a name="author-an-extension"></a>Erstellen einer Erweiterung

Wenn Sie Azure Data Studio erweitern möchten, können Sie eine eigene Erweiterung erstellen und im Erweiterungenkatalog veröffentlichen.

**Schreiben einer Erweiterung**

***Voraussetzungen***

Zum Entwickeln einer Erweiterung muss [Node.js](https://nodejs.org/) in Ihrem `$PATH` installiert und verfügbar sein. Node.js enthält npm, den Node.js-Paket-Manager, der zum Installieren des Erweiterungsgenerators verwendet wird.

Um die neue Erweiterung zu erstellen, können Sie den Azure Data Studio-Erweiterungs-Generator verwenden. Der Yeoman-[Erweiterungs-Generator](https://www.npmjs.com/package/generator-azuredatastudio) ist ein vorteilhafter Ausgangspunkt für Erweiterungsprojekte. Um den Generator zu starten, geben Sie Folgendes in einer Eingabeaufforderung ein:

```console
npm install -g yo generator-azuredatastudio # Install the generator
yo azuredatastudio
```

Eine ausführliche Anleitung zu den ersten Schritten mit ihrer Erweiterungsvorlage finden Sie unter [Erstellen einer Erweiterung](./tutorial-create-extension.md?view=sql-server-ver15), worin Sie durch die Erstellung einer keymap-Erweiterung geführt werden.

**Erweiterbarkeitsreferenzen**

Weitere Informationen zur Erweiterbarkeit von Azure Data Studio finden Sie in der [Erweiterbarkeitsübersicht](extensibility.md). [Hier](https://github.com/Microsoft/azuredatastudio/tree/main/samples) finden Sie auch Beispiele für die Verwendung der API.

## <a name="debug-an-extension"></a>Debuggen einer Erweiterung

Sie können die neue Erweiterung mithilfe der Visual Studio Code-Erweiterung [Azure Data Studio Debug](https://github.com/kevcunnane/sqlops-debug) debuggen.

Schritte:

1. Öffnen Sie Ihre Erweiterung mit [Visual Studio Code](https://code.visualstudio.com/).
2. Installieren Sie die Azure Data Studio-Debug-Erweiterung.
3. Drücken Sie **F5**, oder klicken Sie auf das Debugsymbol und dann auf **Start**.
4. Eine neue Instanz von Azure Data Studio wird in einem speziellen Modus (Extension Development Host, Erweiterungsentwicklungshost) gestartet, und diese neue Instanz erkennt nun Ihre Erweiterung.

## <a name="create-an-extension-package"></a>Erstellen eines Erweiterungspakets

Nachdem Sie Ihre Erweiterung geschrieben haben, müssen Sie ein VSIX-Paket erstellen, um es in Azure Data Studio installieren zu können. Sie können [vsce](https://github.com/Microsoft/vscode-vsce) (Visual Studio Code-Erweiterungen) zum Erstellen des VSIX-Pakets verwenden.

```console
npm install -g vsce
cd myExtensionName
vsce package
# The myExtensionName.vsix file has now been generated
```

Mit einem VSIX-Paket können Sie Ihre Erweiterung lokal und privat freigeben, indem Sie die `.vsix`-Datei freigeben und den Befehl **Erweiterungen: Aus VSIX-Datei installieren** aus der Befehlspalette verwenden, um die Erweiterung in Azure Data Studio zu installieren.

## <a name="publish-an-extension"></a>Veröffentlichen einer Erweiterung

So veröffentlichen Sie die neue Erweiterung in Azure Data Studio:

1. Fügen Sie die Erweiterung https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json hinzu.
2. Wir bieten derzeit keine Unterstützung zum Hosten von Erweiterungen von Drittanbietern. Statt die Erweiterung herunterzuladen, nutzen Sie die Option von Azure Data Studio, zu einer Downloadseite zu navigieren. Um eine Downloadseite für Ihre Erweiterung festzulegen, legen Sie den Wert der Ressource „Microsoft.AzureDataStudio.DownloadPage“ fest.
3. Erstellen Sie einen Pull Request für den release/extensions-Branch.
4. Senden Sie eine Überprüfungsanforderung an das Team.

Die Erweiterung wird überprüft und dem Erweiterungenkatalog hinzugefügt.

**Veröffentlichen von Updates für Erweiterungen**

Der Prozess zum Veröffentlichen von Updates entspricht der Veröffentlichung der Erweiterung. Stellen Sie sicher, dass die Version in „package.json“ aktualisiert wird.

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Tutorials zum Entwickeln von Erweiterungen finden Sie ausführliche Informationen zum Einstieg:

- [Tutorial für eine Tastenzuordnungserweiterung](extensions/keymap-extension.md)
- [Tutorial für eine Dashboarderweiterung](extensions/dashboard-extension.md)
- [Tutorial für eine Notebookerweiterung](extensions/notebook-extension.md)
- [Tutorial für eine Jupyter Notebook-Erweiterung](extensions/jupyter-book-extension.md)
- [Tutorial für eine Assistenten-Erweiterung](extensions/wizard-extension.md)