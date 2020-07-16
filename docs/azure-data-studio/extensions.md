---
title: Hinzufügen von Erweiterungen
description: Fügen Sie Erweiterungen aus dem Erweiterungen-Marketplace zu Azure Data Studio hinzu.
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 10/03/2019
ms.openlocfilehash: 7e74d0dd7b904cba5b332eb20163c96237ac6d6e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774625"
---
# <a name="extend-the-functionality-of-azure-data-studio"></a>Erweitern der Funktionalität von Azure Data Studio

Erweiterungen in Azure Data Studio bieten eine einfache Möglichkeit, der Basisinstallation von Azure Data Studio weitere Funktionen hinzuzufügen.

Erweiterungen werden vom Azure Data Studio-Team (Microsoft) sowie von der Drittanbietercommunity (Ihnen!) bereitgestellt. Weitere Informationen zum Erstellen von Erweiterungen finden Sie unter [Erweiterungserstellung](extension-authoring.md).

## <a name="add-azure-data-studio-extensions"></a>Hinzufügen von Azure Data Studio-Erweiterungen

1. Greifen Sie auf die verfügbaren Erweiterungen zu, indem Sie auf das Symbol „Erweiterungen“ klicken oder **Erweiterungen** im Menü **Ansicht** auswählen.

    ![Erweiterungs-Manager-Symbol](media/extensions/extension-manager-icon.png)

    Sie können auch schnell auf den Erweiterungs-Manager zugreifen, indem Sie `Ctrl+Shift+X` (Windows/Linux) oder `Command+Shift+X` (Mac) drücken.

2. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.
    ![Details zur Erweiterung](media/extensions/extension-details.png)

3. Wählen Sie die gewünschte Erweiterung aus, und **installieren** Sie diese.

4. Klicken Sie nach der Installation auf **Erneut laden**, um die Erweiterung in Azure Data Studio zu aktivieren (nur bei der ersten Installation einer Erweiterung erforderlich).

Wenn Sie Probleme beim Zugriff auf den Erweiterungs-Manager von Azure Data Studio haben, können Sie die benötigte Erweiterung aus unserem [GitHub-Wiki](https://github.com/microsoft/azuredatastudio/wiki/List-of-Extensions) herunterladen.


## <a name="access-installed-azure-data-studio-extensions"></a>Zugreifen auf installierte Azure Data Studio-Erweiterungen

Jede Erweiterung verbessert die Benutzerfreundlichkeit in Azure Data Studio auf eine andere Weise. Infolgedessen kann der Einstiegspunkt für Erweiterungen unterschiedlich sein. Informationen dazu, wie auf die Features zugegriffen werden kann, finden Sie in der Dokumentation der jeweiligen installierten Erweiterung.
