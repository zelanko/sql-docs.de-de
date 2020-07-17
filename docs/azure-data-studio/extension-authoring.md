---
title: Erstellen von Erweiterungen
description: Weitere Informationen zum Erstellen und Hinzufügen von Erweiterungen zu Azure Data Studio
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: adfff7f2aa0fbda1b5e8bdacaddfaef36d16342f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774630"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Erweitern der Funktionalität durch Erstellen von Erweiterungen zu Azure Data Studio

Erweiterungen in Azure Data Studio bieten eine einfache Möglichkeit, der Basisinstallation von Azure Data Studio weitere Funktionen hinzuzufügen.

Erweiterungen werden vom Azure Data Studio-Team (Microsoft) sowie von der Drittanbietercommunity (Ihnen!) bereitgestellt.


## <a name="author-an-extension"></a>Erstellen einer Erweiterung

Wenn Sie Azure Data Studio erweitern möchten, können Sie eine eigene Erweiterung erstellen und im Erweiterungenkatalog veröffentlichen.

**Schreiben einer Erweiterung**

***Voraussetzungen***

Zum Entwickeln einer Erweiterung muss Node.js in Ihrem $PATH installiert und verfügbar sein. Node.js enthält npm, den Node.js-Paket-Manager, der zum Installieren des Erweiterungsgenerators verwendet wird.

Um die neue Erweiterung zu starten, können Sie den Azure Data Studio-Erweiterungsgenerator verwenden. Der Yeoman-[Erweiterungsgenerator](https://www.npmjs.com/package/generator-azuredatastudio) vereinfacht das Erstellen einfacher Erweiterungsprojekte erheblich. Um den Generator zu starten, geben Sie Folgendes in der Eingabeaufforderung ein:

`npm install -g yo generator-azuredatastudio`

`yo azuredatastudio`


**Erweiterbarkeitsreferenzen**

Weitere Informationen zur Erweiterbarkeit von Azure Data Studio finden Sie in der [Erweiterbarkeitsübersicht](extensibility.md). [Hier](https://github.com/Microsoft/azuredatastudio/tree/main/samples) finden Sie auch Beispiele für die Verwendung der API.


## <a name="debug-an-extension"></a>Debuggen einer Erweiterung

Sie können die neue Erweiterung mithilfe der Visual Studio Code-Erweiterung [Azure Data Studio Debug](https://github.com/kevcunnane/sqlops-debug) debuggen.

Schritte
- Öffnen Sie die Erweiterung mit [Visual Studio Code](https://code.visualstudio.com/).
- Installieren der Erweiterung Azure Data Studio Debug
- Drücken Sie **F5**, oder klicken Sie auf das Debugsymbol und dann auf **Start**.
- Eine neue Instanz von Azure Data Studio wird in einem speziellen Modus (Extension Development Host, Erweiterungsentwicklungshost) gestartet, und diese neue Instanz erkennt nun Ihre Erweiterung.


## <a name="create-an-extension-package"></a>Erstellen eines Erweiterungspakets

Nachdem Sie Ihre Erweiterung geschrieben haben, müssen Sie ein VSIX-Paket erstellen, um es in Azure Data Studio installieren zu können. Sie können [vsce](https://github.com/Microsoft/vscode-vsce) zum Erstellen des VSIX-Pakets verwenden.

`npm install -g vsce`

`vsce package`


## <a name="publish-an-extension"></a>Veröffentlichen einer Erweiterung

So veröffentlichen Sie die neue Erweiterung in Azure Data Studio:

1. Fügen Sie die Erweiterung https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json hinzu.
2. Wir bieten derzeit keine Unterstützung zum Hosten von Erweiterungen von Drittanbietern. Statt die Erweiterung herunterzuladen, nutzen Sie die Option von Azure Data Studio, zu einer Downloadseite zu navigieren. Um eine Downloadseite für Ihre Erweiterung festzulegen, legen Sie den Wert der Ressource „Microsoft.AzureDataStudio.DownloadPage“ fest.
3. Erstellen Sie einen Pull Request für den release/extensions-Branch.
4. Senden Sie eine Überprüfungsanforderung an das Team.

Die Erweiterung wird überprüft und dem Erweiterungenkatalog hinzugefügt.

**Veröffentlichung von Erweiterungsupdates** Der Prozess zum Veröffentlichen von Updates entspricht der Veröffentlichung der Erweiterung. Stellen Sie sicher, dass die Version in „package.json“ aktualisiert wird.
