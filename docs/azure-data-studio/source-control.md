---
title: Quellcodeverwaltung
titleSuffix: Azure Data Studio
description: Informationen Sie zum Konfigurieren der quellcodeverwaltung in Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 6431b869af8abc91a9de319f32c0576b82428a0a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798024"
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
