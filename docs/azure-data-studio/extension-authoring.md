---
title: Erstellen von Erweiterungen
titleSuffix: Azure Data Studio
description: Informationen Sie zum Erstellen und Hinzufügen von Erweiterungen zu Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: d7d51459c49bd170b676a219474d35d8e50c1862
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105134"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Erweitern Sie die Funktionalität durch das Erstellen von Azure Data Studio-Erweiterungen

Erweiterungen in [!INCLUDE[name-sos](../includes/name-sos-short.md)] bieten eine einfache Möglichkeit, weitere Funktionen hinzufügen, auf die Basis [!INCLUDE[name-sos](../includes/name-sos-short.md)] Installation.

Erweiterungen werden vom Azure Data Studio-Team (Microsoft), sowie die 3rd Party-Community (Ihnen!) bereitgestellt.


## <a name="author-an-extension"></a>Eine Erweiterung erstellen

Erweitern von Azure Data Studio haben, können Sie eine eigene Erweiterung erstellen und veröffentlichen es in den Erweiterungskatalog.

**Schreiben einer Erweiterungs**

***Erforderliche Komponenten***

Um eine Erweiterung entwickeln benötigen Sie Node.js installiert ist und in Ihre $PATH verfügbar. Node.js umfasst Npm, den Node.js-Paket-Manager, der verwendet wird, um den Generator für die Erweiterung zu installieren.

Um die neue Erweiterung zu starten, können Sie den Studio-Erweiterung für Azure Data-Generator verwenden. Das Yeoman [Erweiterung Generator](https://www.npmjs.com/package/generator-azuredatastudio) ist es sehr einfach, einfache Erweiterung Projekte zu erstellen. Um den Generator zu starten, geben Sie an einer Eingabeaufforderung Folgendes ein:

`npm install -g yo generator-azuredatastudio`

`yo azuredatastudio`


**Erweiterbarkeit Verweise**

Informationen zu Azure Data Studio-Erweiterbarkeit finden Sie unter [erweiterbarkeitsübersicht](extensibility.md). Sie sehen auch Beispiele für die Verwendung der API in vorhandenen [Beispiele](https://github.com/Microsoft/azuredatastudio/tree/master/samples).


## <a name="debug-an-extension"></a>Debuggen Sie eine Erweiterung

Sie können die neue Erweiterung, die mit Visual Studio Code-Erweiterung Debuggen [Debuggen von Azure Data Studio](https://github.com/kevcunnane/sqlops-debug).

Schritte
- Öffnen Sie die Erweiterung mit [Visual Studio Code](https://code.visualstudio.com/)
- Debuggen von Azure Data Studio-Erweiterung installieren
- Drücken Sie **F5** oder klicken Sie auf das Symbol "Debuggen", und klicken Sie auf **starten**.
- Eine neue Instanz der Azure Data Studio in einem speziellen Modus (Extension Development-Host) beginnt, und diese neue Instanz ist nun der Erweiterung.


## <a name="create-an-extension-package"></a>Ein Erweiterungspaket erstellen

Nach dem Schreiben der Erweiterung, müssen Sie zum Erstellen eines VSIX-Pakets, um es in Azure Data Studio installieren zu können. Sie können [Vsce](https://github.com/Microsoft/vscode-vsce) das VSIX-Paket zu erstellen.

`npm install -g vsce`

`vsce package`


## <a name="publish-an-extension"></a>Veröffentlichen einer extension

So veröffentlichen Sie die neue Erweiterung für Azure Data Studio:

1. Hinzufügen der Erweiterungs, um https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json
2. Es gibt derzeit keine Unterstützung für Erweiterungen von Drittanbietern hosten, sodass anstelle der Extension wird heruntergeladen, Studio für Azure Data die Möglichkeit, navigieren Sie zu einer Downloadseite hat. Um einen Download-Seite für die Erweiterung zu festzulegen, legen Sie den Wert des Medienobjekts "Microsoft.AzureDataStudio.DownloadPage".
3. Erstellen Sie einen PR für Release/Extensions-Branch.
4. Senden Sie eine Anforderung an das Team.

Die Erweiterung werden überprüft und den Erweiterungskatalog hinzugefügt.

**Veröffentlichen von Updates der Erweiterung** ähnelt der Prozess zum Veröffentlichen von Updates zum Veröffentlichen der Erweiterungs. Stellen Sie sicher, dass die Version in "Package.JSON" aktualisiert wird
