---
title: Erstellen und Anpassen von Tastenkombinationen in Visual Studio
titleSuffix: Azure Data Studio
description: Erfahren Sie, wie zum Erstellen und Anpassen von Tastenkombinationen im Azure-Data-Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: b5a07ce70b57f5d62d53bf8ae9b570edcc78d7e6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800238"
---
# <a name="keyboard-shortcuts-in-includename-sosincludesname-sosmd"></a>Tastenkombinationen in [!INCLUDE[name-sos](../includes/name-sos.md)]

Dieser Artikel enthält die Schritte, um schnell anzeigen, bearbeiten und Erstellen von Tastenkombinationen in [!INCLUDE[name-sos](../includes/name-sos-short.md)].

Da [!INCLUDE[name-sos](../includes/name-sos-short.md)] erbt die tastenzuordnung-Funktionalität von Visual Studio Code, ausführliche Informationen zu erweiterten Anpassungen, mit verschiedenen Tastaturlayouts usw., in der [Tastenbindungen für Visual Studio Code](https://code.visualstudio.com/docs/getstarted/keybindings) Artikel. Einige tastenzuordnung Features möglicherweise nicht zur Verfügung (z. B. Tastaturlayout Erweiterungen werden in nicht unterstützt [!INCLUDE[name-sos](../includes/name-sos-short.md)]).


## <a name="open-the-keyboard-shortcuts-editor"></a>Öffnen Sie die Tastenkombinationen in Visual Studio-editor

So zeigen Sie alle aktuell definierten Tastenkombinationen an:

Öffnen der **Tastenkombinationen** Editor von der **Datei** Menü: **Datei** > **Voreinstellungen** > **Tastenkombinationen** ( **[!INCLUDE[name-sos](../includes/name-sos-short.md)]**  >   **Voreinstellungen** > **Tastenkombinationen** auf Mac).

Zusätzlich zur Anzeige der aktueller tastaturzuordnungen, die **Tastenkombinationen** Editor Listet die verfügbaren Befehle, die keine Tastenkombinationen in Visual Studio definiert haben. Die **Tastenkombinationen** -Editor können Sie ganz einfach ändern, entfernen, zurücksetzen und definieren neue tastenzuordnungen.  


## <a name="edit-existing-keyboard-shortcuts"></a>Bearbeiten vorhandener Tastenkombinationen

So ändern Sie die tastenzuordnung für eine vorhandene Tastenkombination

1. Suchen Sie die Tastenkombination, die Sie ändern, indem Sie mithilfe des Suchfelds, oder durch die Liste scrollen möchten.
   > [!TIP]
   > Suchen Sie nach Schlüssel, durch den Befehl, Quelle, usw., um alle relevanten Tastenkombinationen zurückzugeben.

1. Mit der rechten Maustaste in des gewünschten Eintrags aus, und wählen Sie **Änderungsschlüssel-Bindung**

   ![Bearbeiten Sie die Tastenkombination](media/keyboard-shortcuts/change-keybinding.png)

1. Drücken Sie die gewünschte Kombination von Schlüsseln, und drücken Sie dann **EINGABETASTE** zu speichern. 

   ![Speichern Sie die Tastenkombination](media/keyboard-shortcuts/save-keybinding.png)

## <a name="create-new-keyboard-shortcuts"></a>Erstellen Sie neue Tastenkombinationen

So erstellen Sie neue Tastenkombinationen:

1. Mit der rechten Maustaste eines Befehls, der eine beliebige Taste, Bindung und die Option keine **-Schlüssel hinzufügen Bindung**.

   ![Erstellen Sie die Tastenkombination](media/keyboard-shortcuts/add-keybinding.png)

1. Drücken Sie die gewünschte Kombination von Schlüsseln, und drücken Sie dann **EINGABETASTE** zu speichern.


