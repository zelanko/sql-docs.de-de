---
title: Auschecken rückgängig machen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 00662ef396ff114e4b77d70aa2f60863e8f94bd3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927843"
---
# <a name="undo-checkouts"></a>Rückgängigmachen von Auscheckvorgängen
  Mit dem Befehl **Rückgängig** Auschecken können Sie ein vorhandenes Checkout abbrechen. Dies bietet sich vor allem an, wenn Sie eine Datei geändert und gespeichert haben und zu einem späteren Zeitpunkt ein Rollback für die Änderungen ausführen müssen.  
  
 Abhängig von den Optionen, die Sie im Dialogfeld **Erweiterte Optionen rückgängig machen** festlegen, verlässt die Studio-Umgebung entweder die Arbeitskopie des Elements auf dem lokalen Datenträger oder ersetzt Sie durch die neueste Version der Quell Code Verwaltung. Wenn ein Benutzer das Element außerhalb des Kontexts des Quellcodeverwaltungssystems geändert hat, handelt es sich bei der abgerufenen Version möglicherweise nicht um die letzte Version.  
  
### <a name="to-undo-a-checkout"></a>So machen Sie einen Auscheckvorgang rückgängig  
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2.  Zeigen Sie im Menü **Datei** auf **Quell**Code Verwaltung, und klicken Sie dann auf Auschecken **rückgängig machen**.  
  
3.  Wählen Sie im Dialogfeld **rückgängig machen** die entsprechenden Optionen aus, und klicken Sie dann auf die Schaltfläche **rückgängig machen** .  
  
     **Spalten**  
     Bestimmt die anzuzeigenden Spalten und die Reihenfolge, in der sie angezeigt werden.  
  
     **Flache Ansicht**  
     Zeigt die Elemente als flache Listen unter der entsprechenden Verbindung mit der Quellcodeverwaltung an.  
  
     **Name**  
     Zeigt die Namen der Elemente an, für die das Auschecken rückgängig gemacht werden soll. Die Elemente werden mit einem aktivierten Kontrollkästchen neben dem Namen angezeigt. Wenn für ein Element das Auschecken nicht rückgängig gemacht werden soll, deaktivieren Sie das entsprechende Kontrollkästchen.  
  
     **Optionen**  
     Zeigt die für das Quellcodeverwaltungs-Plug-In spezifischen Optionen zum Rückgängigmachen des Auscheckens, wenn Sie auf den Pfeil rechts neben der Schaltfläche klicken.  
  
     **Sortieren**  
     Sortiert die Reihenfolge der Anzeigespalten.  
  
     **Strukturansicht**  
     Zeigt den Ordner und die Elementhierarchie für die Elemente an, für die das Auschecken rückgängig gemacht wird.  
  
     **Rückgängig machen**  
     Macht das Auschecken rückgängig, wobei alle Änderungen an der ausgecheckten Datei verworfen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auschecken von Dateien](../../2014/database-engine/check-out-files.md)   
 [Verwalten von Auscheckvorgängen](../../2014/database-engine/manage-checkouts.md)  
  
  
