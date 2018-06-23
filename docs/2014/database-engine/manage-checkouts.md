---
title: Verwalten von Auscheckvorgängen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source controls [SQL Server Management Studio], checkouts
- checkouts [SQL Server Management Studio]
- checking out files
ms.assetid: ddd4adba-d432-4005-9cb2-bb9ee3163d8e
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0540aade3a2e05a6b74a5a16ef9b9ddcfdb6d3f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161401"
---
# <a name="manage-checkouts"></a>Verwalten von Auscheckvorgängen
  Nachdem eine Datei der Quellcodeverwaltung hinzugefügt wurde, müssen Sie die Datei auschecken, bevor Sie sie ändern können. Beim Auschecken einer Datei aus der Quellcodeverwaltung erstellt der Quellcodeverwaltungsanbieter auf dem lokalen Datenträger eine Kopie der letzten Version und entfernt den Schreibschutz der Datei. In bestimmten Situationen müssen Sie möglicherweise eine Datei bearbeiten, ohne sie auszuchecken. Weitere Informationen zum Bearbeiten einer Datei ohne vorheriges Auschecken finden Sie unter [Bearbeiten eingecheckter Dateien](../../2014/database-engine/edit-checked-in-files.md).  
  
 Sie können [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Dateien manuell oder automatisch auschecken. Sie Dateien auschecken manuell durch Öffnen der Projektmappe mit den Dateien in der [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Umgebung, und klicken Sie dann auf die **Auschecken** Befehl. Sie können Dateien automatisch auschecken, wenn Sie die [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]-Umgebung entsprechend konfigurieren.  
  
 Abhängig von den Optionen, die der Administrator für den Quellcodeverwaltungsanbieter festlegt, können Sie Dateien zudem im Modus für exklusive oder gemeinsame Nutzung auschecken. Wenn Sie eine Datei exklusiv auschecken, können nur Sie diese Datei bearbeiten. Ein anderer Benutzer kann die Datei erst dann auschecken, nachdem Sie sie wieder eingecheckt haben. Wenn Sie eine Datei im freigegebenen Modus auschecken, kann sie von beliebig vielen Benutzern gleichzeitig ausgecheckt werden. Da jeder Benutzer die Datei eincheckt, versucht der Quellcodeverwaltungsanbieter, die Datei mit der letzten Serverversion der Datei zusammenzuführen. Wenn Konflikte zwischen der eingecheckten Version und der letzten Version auftreten, wird der Benutzer vom Quellcodeverwaltungsanbieter aufgefordert, die Konflikte zu lösen.  
  
 In der folgenden Tabelle werden die Themen in diesem Abschnitt beschrieben.  
  
|Thema|Description|  
|-----------|-----------------|  
|[Auschecken von Dateien](../../2014/database-engine/check-out-files.md)|Enthält Anweisungen zum Auschecken von Dateien, damit Sie sie ändern können.|  
|[Rückgängigmachen von Auscheckvorgängen](../../2014/database-engine/undo-checkouts.md)|Erläutert, wie Sie ein vorhandenes Auschecken abbrechen können.|  
|[Automatisches Auschecken von Dateien beim Bearbeiten](../../2014/database-engine/automatically-check-out-files-upon-edit.md)|Beschreibt, wie Sie die Quellcodeverwaltung konfigurieren können, damit Dateien beim Beginnen der Bearbeitung ausgecheckt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Eincheckvorgängen](../../2014/database-engine/manage-checkins.md)   
 [Bearbeiten eingecheckter Dateien](../../2014/database-engine/edit-checked-in-files.md)  
  
  