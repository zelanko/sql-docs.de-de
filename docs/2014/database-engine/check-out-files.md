---
title: Auschecken von Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bde4d7fa738bdc952abc936ea13caa7225887ad6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786745"
---
# <a name="check-out-files"></a>Auschecken von Dateien
  Sie müssen eine Datei auschecken, bevor Sie sie bearbeiten können, es sei denn, Sie haben die [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Umgebung so konfiguriert, dass eingecheckte Dateien bearbeitet werden können. Beim Auschecken einer Datei wird eine Kopie der Dateiversion auf den lokalen Datenträger kopiert, und der Schreibschutz der Datei wird entfernt.  
  
 Sie können Dateien entweder exklusiv oder im Modus für gemeinsame Nutzung auschecken. Wenn Sie eine Datei exklusiv auschecken, kann sie von einem anderen Benutzer erst dann ausgecheckt werden, nachdem Sie sie wieder eingecheckt haben. Wenn Sie eine Datei im Modus für gemeinsame Nutzung auschecken, können andere Benutzer die Datei auschecken und ändern. Wenn Sie die Datei einchecken, müssen Sie die von Ihnen ausgecheckte Version möglicherweise mit den Versionen zusammenführen, die von anderen Benutzern erstellt wurden.  
  
 Verwenden der **Auschecken** Befehl zum Auschecken der quellcodeverwaltung unterliegende Projekte und Dateien. Wenn Sie diesen Befehl verwenden, um eine Projektmappe oder ein Projekt auschecken, werden auch alle Dateien in der Projektmappe oder das Projekt ausgecheckt. Allerdings führt beim Auschecken einer einzelnen Quellcodedatei nicht zu Auschecken eines Projekts oder der Projektmappe, die zu der er gehört.  
  
> [!NOTE]  
>  Wenn die [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe-Datenbank für das Projekt ist so konfiguriert, dass Mehrfaches Auschecken ermöglicht, und Sie eine Datei exklusiv auschecken, müssen Sie löschen möchten die **Mehrfaches Auschecken zulassen** option die  **Erweiterte Optionen für das Auschecken** (Dialogfeld), bevor Sie die Datei auschecken. Damit diese Einstellung wirksam wird, müssen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] neu starten.  
  
### <a name="to-check-out-a-file"></a>So checken Sie eine Datei aus  
  
1.  Wählen Sie das Projekt oder die Datei im Projektmappen-Explorer aus.  
  
2.  Auf der **Datei** Startmenü **Quellcodeverwaltung**, und klicken Sie dann auf **Auschecken zum Bearbeiten**.  
  
3.  Wenn die **Auschecken zum Bearbeiten** Dialogfeld angezeigt wird, wählen Sie die Elemente, die Sie möchten, und klicken Sie auf **Auschecken**. Wenn Sie konfiguriert haben die [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Umgebung nicht zum Anzeigen der **Auschecken** Dialogfeld, in der Projektmappen-Explorer und alle untergeordneten Elemente haben möglicherweise ausgewählten Elemente sofort ausgecheckt.  
  
     **Abreise**  
     Die ausgewählten Elemente werden ausgecheckt.  
  
     **Spalten**  
     Bestimmt die anzuzeigenden Spalten und die Reihenfolge, in der sie angezeigt werden.  
  
     **Kommentare**  
     Hier können Sie einen Kommentar für den Auscheckvorgang eingeben.  
  
     **Nicht auschecken anzeigen (Dialogfeld), wenn das Auschecken von Elementen**  
     Unterdrückt die Anzeige des Dialogfelds während Auscheckvorgängen.  
  
     **Flache Ansicht**  
     Zeigt die Elemente, die ausgecheckt werden, als flache Listen unter der entsprechenden Verbindung mit der Quellcodeverwaltung an.  
  
     **Bearbeiten**  
     Ändern Sie ein Element ohne vorheriges Auschecken. Die **bearbeiten** Schaltfläche nur angezeigt, wenn man [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] so konfiguriert, dass das Bearbeiten von eingecheckten Dateien unterstützt.  
  
     **Name**  
     Zeigt die Namen der Elemente an, die für das Auschecken verfügbar sind. Die ausgewählten Elemente werden mit einem Kontrollkästchen neben dem Namen angezeigt. Wenn ein Element nicht ausgecheckt werden soll, deaktivieren Sie das entsprechende Kontrollkästchen.  
  
     **Optionen**  
     Zeigt die für das Quellcodeverwaltungs-Plug-In spezifischen Optionen zum Auschecken an, wenn Sie auf den Pfeil rechts neben der Schaltfläche klicken.  
  
     **Sort**  
     Sortiert die Reihenfolge der angezeigten Spalten.  
  
     **Strukturansicht**  
     Zeigt die Ordner- und Dateihierarchie für das Element an, das ausgecheckt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten von eingecheckten Dateien](../../2014/database-engine/edit-checked-in-files.md)   
 [Automatisches Auschecken von Dateien beim Bearbeiten](../../2014/database-engine/automatically-check-out-files-upon-edit.md)   
 [Rückgängigmachen von Auscheckvorgängen](../../2014/database-engine/undo-checkouts.md)   
 [Verwalten von Auscheckvorgängen](../../2014/database-engine/manage-checkouts.md)  
  
  
