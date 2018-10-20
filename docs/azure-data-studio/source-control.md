---
title: Quellcodeverwaltung in Azure Data Studio | Microsoft-Dokumentation
description: Informationen Sie zum Konfigurieren von Datenquellen-Steuerelement in Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 956ead73c4fe28a045f5ff24280012ed32937f9c
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356311"
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>Verwenden der quellcodeverwaltung in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] unterstützt Git für die Version/quellcodeverwaltung an.


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Git-Unterstützung in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] umfasst ein Git Source dienststeuerungs-Manager (SCM), aber Sie müssen dennoch [installieren Sie Git (Version 2.0.0 oder höher)](https://git-scm.com/download) , bevor diese Features verfügbar sind. 



## <a name="open-an-existing-git-repository"></a>Öffnen Sie ein vorhandenes Git-repository

1. Unter den **Datei** , wählen Sie im Menü **"Ordner öffnen"...**
2. Navigieren Sie zu dem Ordner, die Dateien, die von Git nachverfolgt werden enthält, und klicken Sie auf **Ordner auswählen**. Unterordner in Ihrem lokalen Repository werden hier auswählen.


## <a name="initialize-a-new-git-repository"></a>Initialisiert ein neues Git-repository

1. Wählen Sie **Quellcodeverwaltung**, wählen Sie dann auf das Symbol "Git".

   ![Source-Control-Git-Symbol](media/source-control/source-control.png)

1. Geben Sie den Pfad zu dem Ordner, die Sie als ein Git-Repository, und drücken Sie initialisieren möchten **EINGABETASTE**.

   ![Git-Repository initialisieren](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Arbeiten mit Git-Repositorys

[!INCLUDE[name-sos](../includes/name-sos-short.md)] die Git-Implementierung von Visual Studio Code erbt jedoch zusätzliche SCM-Anbieter wird derzeit nicht unterstützt. Ausführliche Informationen zum Arbeiten mit Git, nachdem Sie geöffnet, oder initialisieren Sie ein Repository, finden Sie unter [Git-Unterstützung in Visual Studio Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Weitere Ressourcen
- [Git-Dokumentation](https://git-scm.com/documentation)
