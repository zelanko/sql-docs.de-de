---
title: Entfernen von Joins (Visual Database Tools)|Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a9bcc6fa9915635b2bc7c7bffb98e85a4f021de
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43809236"
---
# <a name="remove-joins-visual-database-tools"></a>Entfernen von Joins (Visual Database Tools)
  Wenn Tabellen nicht über einen inneren oder äußeren Join miteinander verknüpft werden sollen, können Sie den Join zwischen diesen Tabellen entfernen. Sie können z. B. einen Join entfernen, die der [Abfrage- und Ansicht-Designer](visual-database-tools.md) automatisch zwischen zwei Tabellen erstellt hat.  
  
> [!NOTE]  
>  Durch das Entfernen eines Joins aus einer Abfrage wird die zugrunde liegende Beziehung in der Datenbank nicht geändert.  
  
 Wenn zwei verknüpfte Tabellen Teil der Abfrage sind und Sie alle Joinbedingungen zwischen diesen entfernen, entsteht die resultierende Abfrage als Produkt aus beiden Tabellen, d. h. sie wird als CROSS JOIN bezeichnet.  
  
### <a name="to-remove-a-join"></a>So entfernen Sie einen Join  
  
-   Markieren Sie im [Diagrammbereich](diagram-pane-visual-database-tools.md)die Joinlinie für den zu entfernenden Join, und drücken Sie anschließend die ENTF-TASTE. Sie können mehrere Joinlinien gleichzeitig markieren und löschen.  
  
 Der Abfrage- und Sicht-Designer entfernt die Joinlinie und ändert die Anweisung im [SQL-Bereich](sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisches Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md)   
 [Manuelles Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md)   
 [Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  
