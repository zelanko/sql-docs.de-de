---
title: Rückgängigmachen von Auscheckvorgängen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 84fe5f531edfa8f122dea1b021aa4534b7c2a1f6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047461"
---
# <a name="undo-checkouts"></a>Rückgängigmachen von Auscheckvorgängen
  Sie können die **Rückgängig: Auschecken** Befehl aus, um einen vorhandenen Auscheckvorgang abbrechen. Dies bietet sich vor allem an, wenn Sie eine Datei geändert und gespeichert haben und zu einem späteren Zeitpunkt ein Rollback für die Änderungen ausführen müssen.  
  
 Abhängig von den Optionen, die Sie im Festlegen der **Rückgängig: Auschecken erweiterte Optionen** (Dialogfeld), die Studio-Umgebung die Arbeitskopie des Elements verlässt, auf dem lokalen Datenträger oder durch die neueste Version unter quellcodeverwaltung ersetzt. Wenn ein Benutzer das Element außerhalb des Kontexts des Quellcodeverwaltungssystems geändert hat, handelt es sich bei der abgerufenen Version möglicherweise nicht um die letzte Version.  
  
### <a name="to-undo-a-checkout"></a>So machen Sie einen Auscheckvorgang rückgängig  
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2.  Auf der **Datei** Sie im Menü **Quellcodeverwaltung**, und klicken Sie dann auf **Rückgängig: Auschecken**.  
  
3.  In der **Rückgängig: Auschecken** (Dialogfeld), wählen die gewünschten Optionen aus, und klicken Sie dann auf die **Rückgängig: Auschecken** Schaltfläche.  
  
     **Spalten**  
     Bestimmt die anzuzeigenden Spalten und die Reihenfolge, in der sie angezeigt werden.  
  
     **Flache Ansicht**  
     Zeigt die Elemente als flache Listen unter der entsprechenden Verbindung mit der Quellcodeverwaltung an.  
  
     **Name**  
     Zeigt die Namen der Elemente an, für die das Auschecken rückgängig gemacht werden soll. Die Elemente werden mit einem aktivierten Kontrollkästchen neben dem Namen angezeigt. Wenn für ein Element das Auschecken nicht rückgängig gemacht werden soll, deaktivieren Sie das entsprechende Kontrollkästchen.  
  
     **Optionen**  
     Zeigt die für das Quellcodeverwaltungs-Plug-In spezifischen Optionen zum Rückgängigmachen des Auscheckens, wenn Sie auf den Pfeil rechts neben der Schaltfläche klicken.  
  
     **Sort**  
     Sortiert die Reihenfolge der Anzeigespalten.  
  
     **Strukturansicht**  
     Zeigt den Ordner und die Elementhierarchie für die Elemente an, für die das Auschecken rückgängig gemacht wird.  
  
     **Rückgängig: Auschecken**  
     Macht das Auschecken rückgängig, wobei alle Änderungen an der ausgecheckten Datei verworfen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auschecken von Dateien](../../2014/database-engine/check-out-files.md)   
 [Verwalten von Auscheckvorgängen](../../2014/database-engine/manage-checkouts.md)  
  
  