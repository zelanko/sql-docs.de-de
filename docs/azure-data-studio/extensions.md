---
title: Hinzufügen von Erweiterungen
titleSuffix: Azure Data Studio
description: Fügen Sie Erweiterungen aus dem Erweiterungen-Marketplace zu Azure Data Studio hinzu.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 10/03/2019
ms.openlocfilehash: 6f0a2ab021873a2a9414bfbcdb7aed63c2d31056
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "72166714"
---
# <a name="extend-the-functionality-of-includename-sosincludesname-sos-shortmd"></a>Erweitern der Funktionalität von [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Erweiterungen in [!INCLUDE[name-sos](../includes/name-sos-short.md)] bieten eine einfache Möglichkeit, der Basisinstallation von [!INCLUDE[name-sos](../includes/name-sos-short.md)] weitere Funktionen hinzuzufügen. 

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
