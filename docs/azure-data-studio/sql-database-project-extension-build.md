---
title: Erstellen und Veröffentlichen eines Projekts
description: Hier erfahren Sie, wie Sie mit der Erweiterung „SQL Server-Datenbankprojekte“ ein Projekt erstellen und veröffentlichen.
ms.custom: seodec18
ms.date: 06/25/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 4348f117b57c9b13a70f4a6db39ab6710eafd0ef
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2020
ms.locfileid: "85519166"
---
# <a name="build-and-publish-a-project"></a>Erstellen und Veröffentlichen eines Projekts

Mit der Erweiterung „SQL Server-Datenbankprojekte“ für Azure Data Studio können Sie für Windows-, macOS- und Linux-Umgebungen ein Projekt im *DACPAC*-Format erstellen. Das Projekt kann im Veröffentlichungsprozess in einer lokalen oder Cloudumgebung bereitgestellt werden.

## <a name="prerequisites"></a>Voraussetzungen
- Installieren und konfigurieren Sie die [Erweiterung „SQL Server-Datenbankprojekte“ für Azure Data Studio](sql-database-project-extension.md).


## <a name="build-a-database-project"></a>Erstellen eines Datenbankprojekts

 Klicken Sie im Viewlet **Projekte** unter **Explorer** mit der rechten Maustaste auf den Stammknoten *SQLPROJ*, und klicken Sie auf **Erstellen**.

 Es wird automatisch der Ausgabebereich mit der Ausgabe des Buildprozesses angezeigt.  War der Buildprozess erfolgreich, endet die Meldung mit: 

 ``` ... exited with code: 0 ```


## <a name="publish-a-database-project"></a>Veröffentlichen eines Datenbankprojekts

Nachdem Sie das Projekt erfolgreich im Buildprozess kompiliert haben, können Sie die Datenbank in einer SQL Server-Instanz veröffentlichen. Klicken Sie dazu im Viewlet **Projekte** unter **Explorer** mit der rechten Maustaste auf den Stammknoten *SQLPROJ*, und klicken Sie auf **Veröffentlichen**.

Geben Sie im angezeigten Dialogfeld **Datenbank veröffentlichen** eine Serververbindung und den Namen der Datenbank an, die erstellt werden soll.

## <a name="next-steps"></a>Nächste Schritte

- [Erweiterung „SQL Server-Datenbankprojekte“ für Azure Data Studio](sql-database-project-extension.md)
- [Datenschichtanwendungen](../relational-databases/data-tier-applications/data-tier-applications.md)


