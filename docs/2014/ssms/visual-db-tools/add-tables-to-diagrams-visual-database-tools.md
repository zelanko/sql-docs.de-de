---
title: Hinzufügen von Tabellen zu Diagrammen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
ms.assetid: 5440fdf7-ac04-4325-9f32-181f4cd402e5
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 59ede7a063cf0f804dee05654c652afc516b2d5f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299550"
---
# <a name="add-tables-to-diagrams-visual-database-tools"></a>Hinzufügen von Tabellen zu Diagrammen (Visual Database Tools)
  Sie können dem Datenbankdiagramm eine Tabelle hinzufügen, um die Diagrammstruktur zu bearbeiten oder Beziehungen zu anderen Tabellen im Diagramm zu erstellen. Sie können der Datenbank entweder bereits vorhandene Datenbanktabellen oder eine neue Tabelle hinzufügen, die noch nicht in der Datenbank definiert ist.  
  
### <a name="to-insert-a-new-table-into-a-diagram"></a>So fügen Sie eine neue Tabelle in ein Diagramm ein  
  
1.  Vergewissern Sie sich, dass Sie mit der Datenbank verbunden sind, in der die Tabelle erstellt werden soll.  
  
     Zum Erstellen einer Tabelle im aktuellen Diagramm klicken Sie auf der Symbolleiste auf die Schaltfläche **Neue Tabelle** .  
  
     – Oder –  
  
     Klicken Sie mit der rechten Maustaste auf das Diagramm, und wählen Sie **Neue Tabelle**aus.  
  
2.  Übernehmen oder ändern Sie den vom System zugewiesenen Namen der Tabelle im Dialogfeld **Namen auswählen** , und klicken Sie auf **OK**.  
  
     In der Standardansicht des Diagramms wird nun eine neue Tabelle angezeigt.  
  
3.  Geben Sie in der ersten Zelle der neuen Tabelle einen Spaltennamen ein. Drücken Sie dann die TAB-TASTE, um zur nächsten Zelle zu wechseln.  
  
4.  Wählen Sie unter **Datentyp**einen Datentyp für die Spalte aus. Jeder Spalte muss ein Name und ein Datentyp zugewiesen werden.  
  
     Sie können die anderen Eigenschaften der Spalte im Tabellen-Designer festlegen.  
  
5.  Wiederholen Sie die Schritte 3 und 4 für jede Spalte, die Sie der Tabelle hinzufügen möchten.  
  
> [!NOTE]  
>  Wenn Sie das Datenbankdiagramm speichern, wird die neue Tabelle der Datenbank hinzugefügt.  
  
### <a name="to-add-an-existing-table-to-a-diagram"></a>So fügen Sie einem Diagramm eine vorhandene Tabelle zu  
  
1.  Vergewissern Sie sich, dass Sie mit der Datenbank verbunden sind, deren Tabellen Sie bearbeiten möchten.  
  
2.  Markieren Sie eine Tabelle im Ordner **Tabellen** .  
  
3.  Ziehen Sie die Tabelle in das Datenbankdiagramm.  
  
4.  Lassen Sie die Maustaste los.  
  
> [!NOTE]  
>  Wenn Beziehungen zwischen der ausgewählten Tabelle und anderen Tabellen im Diagramm bestehen, werden automatisch Beziehungslinien gezogen.  
  
### <a name="to-add-related-tables-to-a-diagram"></a>So fügen Sie einem Diagramm verknüpfte Tabellen hinzu  
  
1.  Wählen Sie eine oder mehrere Tabellen mit Fremdschlüsseleinschränkungen im Datenbankdiagramm aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine der ausgewählten Tabellen, und wählen Sie **Verknüpfte Tabellen hinzufügen**aus.  
  
> [!NOTE]  
>  Daraufhin werden dem Diagramm sowohl die Tabellen hinzugefügt, auf die die ausgewählten Tabellen mit einer Fremdschlüsseleinschränkung verweisen, als auch die Tabellen, die mit einer Fremdschlüsseleinschränkung auf die ausgewählten Tabellen verweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Datenbankdiagrammen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Verwenden von Tabellen in Datenbankdiagrammen &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
