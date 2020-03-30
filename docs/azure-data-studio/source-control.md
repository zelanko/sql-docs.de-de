---
title: Quellcodeverwaltung
titleSuffix: Azure Data Studio
description: Erfahren Sie, wie Sie Quellcodeverwaltung in Azure Data Studio konfigurieren.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: c278bcf6cff451396b3d677b203f207b68fd6dc5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67959287"
---
#  <a name="using-source-control-in-name-sos"></a>Verwenden von Quellcodeverwaltung in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] unterstützt Git zur Versionskontrolle/Quellcodeverwaltung.


## <a name="git-support-in-name-sos"></a>Git-Unterstützung in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] wird mit einem Git-Quellcodeverwaltungs-Manager (Source Control Manager, SCM) bereitgestellt. Sie müssen dennoch weiterhin [Git (Version 2.0.0 oder höher) installieren](https://git-scm.com/download), damit diese Features verfügbar sind. 



## <a name="open-an-existing-git-repository"></a>Öffnen eines vorhandenen Git-Repositorys

1. Wählen Sie im Menü **Datei** den Befehl **Ordner öffnen...** aus.
2. Navigieren Sie zu dem Ordner, der die Dateien enthält, die von Git nachverfolgt werden, und klicken Sie auf **Ordner auswählen**. Unterordner in Ihrem lokalen Repository können hier ausgewählt werden.


## <a name="initialize-a-new-git-repository"></a>Initialisieren eines neuen Git-Repositorys

1. Wählen Sie **Quellcodeverwaltung** und dann das Git-Symbol aus.

   ![Git-Symbol für Quellcodeverwaltung](media/source-control/source-control.png)

1. Geben Sie den Pfad zu dem Ordner ein, den Sie als Git-Repository initialisieren möchten, und drücken Sie die **EINGABETASTE**.

   ![Git-Repository initialisieren](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Arbeiten mit Git-Repositorys

[!INCLUDE[name-sos](../includes/name-sos-short.md)] erbt seine Git-Implementierung von VS Code, unterstützt derzeit jedoch keine weiteren SCM-Anbieter. Ausführliche Informationen über das Arbeiten mit Git, nachdem Sie ein Repository geöffnet oder initialisiert haben, finden Sie unter [Git support in VS Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Zusätzliche Ressourcen
- [Git-Dokumentation](https://git-scm.com/documentation)
