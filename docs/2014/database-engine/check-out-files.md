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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62786745"
---
# <a name="check-out-files"></a>Auschecken von Dateien
  Sie müssen eine Datei auschecken, bevor Sie sie bearbeiten können, es sei denn, Sie haben die [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Umgebung so konfiguriert, dass eingecheckte Dateien bearbeitet werden können. Beim Auschecken einer Datei wird eine Kopie der Dateiversion auf den lokalen Datenträger kopiert, und der Schreibschutz der Datei wird entfernt.  
  
 Sie können Dateien entweder exklusiv oder im Modus für gemeinsame Nutzung auschecken. Wenn Sie eine Datei exklusiv auschecken, kann sie von einem anderen Benutzer erst dann ausgecheckt werden, nachdem Sie sie wieder eingecheckt haben. Wenn Sie eine Datei im Modus für gemeinsame Nutzung auschecken, können andere Benutzer die Datei auschecken und ändern. Wenn Sie die Datei einchecken, müssen Sie die von Ihnen ausgecheckte Version möglicherweise mit den Versionen zusammenführen, die von anderen Benutzern erstellt wurden.  
  
 Verwenden Sie den Befehl **Auschecken** , um Projekte und Dateien der Quell Code Verwaltung auszuchecken. Wenn Sie mit diesem Befehl eine Projekt Mappe oder ein Projekt Auschecken, werden auch alle Dateien in der Projekt Mappe oder im Projekt ausgecheckt. Das Auschecken einer einzelnen Quell Code Datei führt jedoch nicht dazu, dass das Projekt oder die Projekt Mappe, zu der es gehört, ausgecheckt wird.  
  
> [!NOTE]  
>  Wenn die [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe-Datenbank für Ihr Projekt so konfiguriert ist, dass mehrere Auscheck Vorgänge zulässig sind, und Sie eine Datei exklusiv auschecken möchten, müssen Sie im Dialogfeld **Erweiterte auscheckungs Optionen** die Option **mehrere Auschecken zulassen** deaktivieren, bevor Sie die Datei Auschecken. Damit diese Einstellung wirksam wird, müssen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] neu starten.  
  
### <a name="to-check-out-a-file"></a>So checken Sie eine Datei aus  
  
1.  Wählen Sie das Projekt oder die Datei im Projektmappen-Explorer aus.  
  
2.  Zeigen Sie im Menü **Datei** auf **Quell**Code Verwaltung, und klicken Sie dann auf **Auschecken zum Bearbeiten**.  
  
3.  Wenn das Dialogfeld **Auschecken zum Bearbeiten** angezeigt wird, wählen Sie die gewünschten Elemente aus, und klicken Sie auf **Auschecken**. Wenn Sie die [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Umgebung so konfiguriert haben, dass das Dialogfeld " **Auschecken** " nicht angezeigt wird, werden die Elemente, die in Projektmappen-Explorer ausgewählt wurden, sowie alle untergeordneten Elemente sofort ausgecheckt.  
  
     **Abreise**  
     Die ausgewählten Elemente werden ausgecheckt.  
  
     **Spalten**  
     Bestimmt die anzuzeigenden Spalten und die Reihenfolge, in der sie angezeigt werden.  
  
     **Kommentare**  
     Hier können Sie einen Kommentar für den Auscheckvorgang eingeben.  
  
     **Dialogfeld "Auschecken" beim Auschecken von Elementen nicht anzeigen**  
     Unterdrückt die Anzeige des Dialogfelds während Auscheckvorgängen.  
  
     **Flache Ansicht**  
     Zeigt die Elemente, die ausgecheckt werden, als flache Listen unter der entsprechenden Verbindung mit der Quellcodeverwaltung an.  
  
     **Bearbeiten**  
     Ändern Sie ein Element, ohne es auszuchecken. Die Schaltfläche **Bearbeiten** wird nur angezeigt, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Wenn Sie für die Unterstützung der Bearbeitung von eingecheckten Dateien konfiguriert haben.  
  
     **Name**  
     Zeigt die Namen der Elemente an, die für das Auschecken verfügbar sind. Die ausgewählten Elemente werden mit einem Kontrollkästchen neben dem Namen angezeigt. Wenn ein Element nicht ausgecheckt werden soll, deaktivieren Sie das entsprechende Kontrollkästchen.  
  
     **Optionen**  
     Zeigt die für das Quellcodeverwaltungs-Plug-In spezifischen Optionen zum Auschecken an, wenn Sie auf den Pfeil rechts neben der Schaltfläche klicken.  
  
     **Sortieren**  
     Sortiert die Reihenfolge der angezeigten Spalten.  
  
     **Strukturansicht**  
     Zeigt die Ordner- und Dateihierarchie für das Element an, das ausgecheckt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eingecheckte Dateien bearbeiten](../../2014/database-engine/edit-checked-in-files.md)   
 [Dateien beim Bearbeiten automatisch Auschecken](../../2014/database-engine/automatically-check-out-files-upon-edit.md)   
 [Rückgängigmachen](../../2014/database-engine/undo-checkouts.md)   
 [Verwalten von Auscheckvorgängen](../../2014/database-engine/manage-checkouts.md)  
  
  
