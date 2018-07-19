---
title: Quellcodeverwaltung des Projektmappen-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual SourceSafe
- SQL Server Management Studio [SQL Server], source control services
- source-controlled files [SQL Server]
- source controls [SQL Server Management Studio], services
- version control services [SQL Server]
- file source control services [SQL Server]
- VSS [Visual SourceSafe]
ms.assetid: 6373adb8-3d81-4945-a9fc-1d0d5799d29a
caps.latest.revision: 28
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3975c43263e8ad7dc19c5bd8b01c1f32badea35c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213700"
---
# <a name="solution-explorer-source-control"></a>Quellcodeverwaltung des Projektmappen-Explorers
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Projektmappen-Explorer kann in ein separates Quellcodeverwaltungssystem integriert werden. Wenn eine Projektmappe oder ein Projekt in ein Quellcodeverwaltungssystem integriert wird, können Sie Dateizugriff und Versionsverwaltung für die Skripts und Abfragen in Ihren Projekten steuern.  
  
## <a name="solution-and-project-source-control"></a>Quellcodeverwaltung in Projektmappen und Projekten  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]  
  
 Die Quellcodeverwaltung steht für ein System, in dem eine Serversoftware Dateiversionen speichert und nachverfolgt sowie den Zugriff auf Dateien steuert. Ein typisches Quellcodeverwaltungssystem enthält einen Quellcodeverwaltungsanbieter und zwei oder mehr Quellcodeverwaltungsclients. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] kann in einen Quellcodeverwaltungsdienst integriert werden. Das bedeutet, dass Sie das Tool als einen Client für den Quellcodeverwaltungsanbieter verwenden können. Sie können auf einfache Weise eigene und teambasierte Projekte verwalten, ohne die Umgebung zu verlassen. Der Quellcodeverwaltungsanbieter ist nicht in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] enthalten.  
  
#### <a name="to-select-a-source-control-provider"></a>So wählen Sie einen Quellcodeverwaltungsanbieter aus  
  
1.  Installieren Sie den Teil des Clients auf den Quellcodeverwaltungsanbieter.  
  
2.  Klicken Sie in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]im Menü **Extras** auf **Optionen**.  
  
3.  In der **Optionen** Dialogfeld erweitern Sie **Quellcodeverwaltung**, und klicken Sie dann auf die **Plug-in-Auswahl** Seite.  
  
4.  In der **aktuelles Quellcodeverwaltungs-Plug-in** wählen das Quellcodeverwaltungs-Plug-in.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Grundlagen zur Quellcodeverwaltung](../../2014/database-engine/source-control-basics.md)|Definiert die allgemeinen Terminologie für die Quellcodeverwaltung und beschreibt, auf welche Weise das Projekt von Quellcodeverwaltungsdiensten profitieren kann.|  
|[Hinzufügen von Projektmappen und Projekten zur Quellcodeverwaltung](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)|Beschreibt, wie Sie mithilfe der [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]-Umgebung Projektmappen und Projekte zur Quellcodeverwaltung hinzufügen.|  
|[Öffnen von Projektmappen und Projekten aus der Quellcodeverwaltung](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)|Beschreibt, wie Sie mithilfe der [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]-Umgebung quellcodeverwaltete Projektmappen und Projekte öffnen.|  
|[Verwalten von Auscheckvorgängen](../../2014/database-engine/manage-checkouts.md)|Beschreibt, wie Sie Projektmappen und Dateien aus der Quellcodeverwaltung auschecken.|  
|[Verwalten von Eincheckvorgängen](../../2014/database-engine/manage-checkins.md)|Beschreibt, wie Sie Projektmappen und Dateien in die Quellcodeverwaltung einchecken.|  
|[Festlegen und Abrufen von Versionsinformationen](../../2014/database-engine/set-and-retrieve-version-information.md)|Beschreibt, wie Sie den Verlauf für ein Projekt oder Element abrufen, eine lokale Kopie eines Elements abrufen oder zwei Elementversionen vergleichen.|  
|||  
  
## <a name="see-also"></a>Siehe auch  
 [Projektmappen-Explorer](../ssms/solution/solution-explorer.md)   
 [Lösungen &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)   
 [Projekte &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md)   
 [Dateien zum Verwalten von Projektmappen und Projekten](../ssms/solution/files-that-manage-solutions-and-projects.md)  
  
  
