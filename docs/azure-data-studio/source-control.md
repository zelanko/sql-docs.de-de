---
title: Quellcodeverwaltung
description: Erfahren Sie, wie Sie Quellcodeverwaltung in Azure Data Studio konfigurieren.
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: c4f586e355ad31422c75a5abb10a4c7e42f5eda6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758375"
---
# <a name="source-control-in-azure-data-studio"></a>Quellcodeverwaltung in Azure Data Studio

Azure Data Studio unterstützt Git für die Versionskontrolle/Quellcodeverwaltung.

## <a name="git-support-in-azure-data-studio"></a>Git-Unterstützung in Azure Data Studio

Azure Data Studio wird mit einem Git-Quellcodeverwaltungs-Manager (Source Control Manager, SCM) bereitgestellt. Sie müssen dennoch weiterhin [Git (Version 2.0.0 oder höher) installieren](https://git-scm.com/download), damit diese Features verfügbar sind. 

## <a name="open-an-existing-git-repository"></a>Öffnen eines vorhandenen Git-Repositorys

1. Wählen Sie im Menü **Datei** den Befehl **Ordner öffnen...** aus.
2. Navigieren Sie zu dem Ordner, der die Dateien enthält, die von Git nachverfolgt werden, und klicken Sie auf **Ordner auswählen**. Unterordner in Ihrem lokalen Repository können hier ausgewählt werden.

## <a name="initialize-a-new-git-repository"></a>Initialisieren eines neuen Git-Repositorys

1. Wählen Sie **Quellcodeverwaltung** und dann das Git-Symbol aus.

   ![Git-Symbol für Quellcodeverwaltung](media/source-control/source-control.png)

1. Geben Sie den Pfad zu dem Ordner ein, den Sie als Git-Repository initialisieren möchten, und drücken Sie die **EINGABETASTE**.

   ![Git-Repository initialisieren](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Arbeiten mit Git-Repositorys

Azure Data Studio erbt die Git-Implementierung von VS Code, unterstützt derzeit jedoch keine weiteren SCM-Anbieter. Ausführliche Informationen über das Arbeiten mit Git, nachdem Sie ein Repository geöffnet oder initialisiert haben, finden Sie unter [Git support in VS Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).

## <a name="additional-resources"></a>Zusätzliche Ressourcen

- [Git-Dokumentation](https://git-scm.com/documentation)
