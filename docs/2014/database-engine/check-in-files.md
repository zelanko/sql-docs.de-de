---
title: Einchecken von Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckInDialog
helpviewer_keywords:
- checking in files
ms.assetid: 0657a387-8411-4406-bef9-d262a5bfa269
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5debb7c80e7365e67d8661709b09b16f5d25b7b9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62812584"
---
# <a name="check-in-files"></a>Einchecken von Dateien
  Um von Ihnen geänderte quellcodeverwaltete Dateien für andere Benutzer verfügbar zu machen, müssen Sie die Dateien zunächst in die Quellcodeverwaltung einchecken. Wenn Sie eine Datei einchecken, wird die von Ihnen eingecheckte Version in den Quellcodeverwaltungsanbieter geschrieben und als aktuelle Dateiversion festgelegt.  
  
 Sie können der **Einchecken** Befehl aus, um die Dateien einzuchecken. Wenn Sie mit diesem Befehl eine Projektmappe oder ein Projekt einchecken, werden auch alle Dateien eingecheckt, die sich in der Projektmappe bzw. im Projekt befinden. Umgekehrt wird durch das Einchecken einer einzelnen Quellcodedatei nicht das Projekt bzw. die Projektmappe eingecheckt, zu der sie gehört.  
  
### <a name="to-check-in-a-file"></a>So checken Sie eine Datei ein  
  
1.  Im Projektmappen-Explorer mit der Maustaste der Datei einchecken, und klicken Sie dann auf **Einchecken**.  
  
2.  Wenn die **Einchecken** Dialogfeld angezeigt wird, wählen die gewünschten Optionen aus, und klicken Sie dann auf **OK**.  
  
     **Ankunft**  
     Checkt die ausgewählten Elemente ein.  
  
     **Spalten**  
     Bestimmt die anzuzeigenden Spalten und die Reihenfolge, in der sie angezeigt werden.  
  
     **Kommentare**  
     Fügt einen Kommentar für den Eincheckvorgang hinzu.  
  
     **Überprüfen Sie nicht im Dialogfeld angezeigt werden, beim Einchecken von Elementen**  
     Unterdrückt die Anzeige des Dialogfelds bei Eincheckvorgängen.  
  
     **Flache Ansicht**  
     Zeigt die Dateien, die eingecheckt werden, als flache Listen unter der entsprechenden Verbindung mit der Quellcodeverwaltung an.  
  
     **Name**  
     Zeigt die Namen der einzucheckenden Elemente an. Die Elemente werden mit einem aktivierten Kontrollkästchen neben dem Namen angezeigt. Wenn ein Element nicht eingecheckt werden soll, deaktivieren Sie das entsprechende Kontrollkästchen.  
  
     **Options**  
     Zeigt die für das Quellcodeverwaltungs-Plug-In spezifischen Eincheckoptionen an, wenn Sie auf den Pfeil rechts neben der Schaltfläche klicken.  
  
     **Sort**  
     Sortiert die Reihenfolge der Anzeigespalten.  
  
     **Strukturansicht**  
     Zeigt die Ordner- und Dateihierarchie für die eingecheckten Elemente an.  
  
 Wenn die Datei, die Sie eingecheckt haben, nicht zu einem freigegebenen ausgecheckten Element gehört, wird die Datei von der [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Umgebung unmittelbar eingecheckt. Ist dies nicht der Fall, werden Sie unter Umständen aufgefordert, Ihre Version mit Versionen zusammenzuführen, die von anderen Benutzern erstellt wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen einer Liste geänderter Dateien](../../2014/database-engine/view-a-list-of-modified-files.md)   
 [Verwalten von Eincheckvorgängen](../../2014/database-engine/manage-checkins.md)  
  
  
