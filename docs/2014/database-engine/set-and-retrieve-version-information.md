---
title: Festlegen und Abrufen von Versionsinformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 52fdedc502bc2d8c53a01b0bc69d8a3168957b97
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820266"
---
# <a name="set-and-retrieve-version-information"></a>Festlegen und Abrufen von Versionsinformationen
  Zu den Versionsinformationen zählen der Verlauf und der aktuelle Status einer Datei unter Quellcodeverwaltung. Für jede Datei unter Quellcodeverwaltung verwaltet [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe umfassende Verlaufsdaten. Dadurch können Sie die Entwicklung einer oder mehrerer Dateien über einen bestimmten Zeitraum verfolgen. Sie können diese Informationen auch dazu verwenden, um eine lokale Kopie einer beliebigen Version der Datei abzurufen oder zwei beliebige Versionen miteinander zu vergleichen.  
  
 Zum Verlauf einer Datei gehört:  
  
-   Die Versionsnummer, die die Sequenz in Bezug auf andere Versionen dieser Datei identifiziert.  
  
-   Die ausgeführte Aktion. Zu den Vorgängen der Ablaufverfolgung zählen das Erstellen der Datei, das Einchecken und das Löschen.  
  
-   Der Benutzername der Person, die eine Aktion für die Datei ausgeführt hat.  
  
-   Datum und Uhrzeit der Ausführung des Vorgangs.  
  
 Visual SourceSafe verwaltet außerdem aktuelle Statusinformationen für die zurzeit geladene Projektmappe. Diese Informationen liefern eine Momentaufnahme des aktuellen Status der Datei. Dazu zählen:    
  
-   Die Identität des Benutzers, der die Datei ausgecheckt hat.  
  
-   Die letzte Versionsnummer der ausgewählten Datei.  
  
-   Das Datum, an dem die Version erstellt wurde.  
  
-   Der Benutzerkommentar, der der Version zugewiesen ist.  
  
-   Die Pfade zu den Projekten, für die die Datei freigegeben ist.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Anzeigen des Dateiverlaufs](../../2014/database-engine/view-file-history.md)  
  
-   [Anzeigen der Projektversionsgeschichte](../../2014/database-engine/view-project-history.md)  
  
-   [Anzeigen des Dateistatus](../../2014/database-engine/view-file-status.md)  
  
-   [Abrufen von Dateien](../../2014/database-engine/retrieve-files.md)  
  
-   [Angeben einer Version als letzte Version](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [Vergleichen von Dateien](../../2014/database-engine/compare-files.md)  
  
-   [Freigeben von Dateien](../../2014/database-engine/share-files.md)  
  
-   [Erstellen von Verlaufs- und Statusberichten](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen zur Quellcodeverwaltung](../../2014/database-engine/source-control-basics.md)  
  
  
