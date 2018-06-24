---
title: Zeichnen reflexiver Beziehungen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08e3d4d09c08abd5453322430f6d6ccfc8456a1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050687"
---
# <a name="draw-reflexive-relationships-visual-database-tools"></a>Zeichnen reflexiver Beziehungen (Visual Database Tools)
  Sie erstellen eine reflexive Beziehung, um eine Spalte oder mehrere Spalten in einer Tabelle mit einer anderen Spalte oder mehreren Spalten in derselben Tabelle zu verknüpfen. Angenommen, in der Tabelle `employee` gibt es die Spalte `emp_id` und die Spalte `mgr_id` . Da jeder Manager gleichzeitig ein Mitarbeiter ist, verknüpfen Sie diese beiden Spalten, indem Sie eine Beziehungslinie innerhalb der Tabelle ziehen. Durch diese Beziehung wird sichergestellt, dass jede der Tabelle hinzugefügte Manager-ID mit einer vorhandenen Mitarbeiter-ID übereinstimmt.  
  
 Bevor Sie eine Beziehung erstellen, müssen Sie zunächst einen Primärschlüssel oder eine UNIQUE-Einschränkung für die Tabelle definieren. Anschließend verknüpfen Sie die Primärschlüsselspalte mit einer übereinstimmenden Spalte. Wenn die Beziehung erstellt ist, wird die übereinstimmende Spalte der Fremdschlüssel für die Tabelle.  
  
### <a name="to-draw-a-reflexive-relationship"></a>So erstellen Sie eine reflexive Beziehung  
  
1.  Klicken Sie im Datenbankdiagramm auf den Zeilenselektor für die Datenbankspalte, die Sie zu einer anderen Spalte in Beziehung setzen möchten, und ziehen Sie den Mauszeiger aus der Tabelle heraus, bis eine Linie angezeigt wird.  
  
2.  Ziehen Sie die Linie zurück in die ausgewählte Tabelle.  
  
3.  Lassen Sie die Maustaste los. Das Dialogfeld **Tabellen und Spalten** wird angezeigt.  
  
4.  Wählen Sie die Fremdschlüsselspalte und die Primärschlüsseltabelle sowie -spalte aus, zu denen eine Beziehung hergestellt werden soll.  
  
5.  Klicken Sie zweimal auf **OK** , um die Beziehung zu erstellen.  
  
 Wenn Sie Abfragen in einer Tabelle ausführen, können Sie mithilfe einer reflexiven Beziehung einen Selbstjoin erstellen. Informationen über das Abfragen von Tabellen mit Joins finden Sie unter [Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  