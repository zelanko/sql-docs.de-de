---
title: Automatisches Erstellen von Selbstverknüpfungen (Visual Database Tools) | Microsoft-Dokumentation
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
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d541ce3229ee01c2fb213eafb1e8c7f55a4b984a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196550"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Automatisches Erstellen von Selbstjoins (Visual Database Tools)
  Wenn die Tabelle über eine reflexive Beziehung in der Datenbank verfügt, können Sie diese automatisch mit sich selbst verknüpfen.  
  
### <a name="to-create-a-self-join-automatically"></a>So erstellen Sie automatisch einen Selbstjoin  
  
1.  Fügen Sie dem [Diagrammbereich](visual-database-tools.md) die Tabelle hinzu, mit der Sie arbeiten möchten.  
  
2.  Fügen Sie dieselbe Tabelle erneut hinzu, sodass die Tabelle im Diagrammbereich zweimal angezeigt wird.  
  
     Der [Abfrage- und Sicht-Designer](query-and-view-designer-tools-visual-database-tools.md) weist der zweiten Instanz einen Alias zu, indem er dem Tabellennamen eine laufende Nummer hinzufügt. Außerdem erstellt der Abfrage- und Sicht-Designer eine Joinlinie zwischen den zwei Rechtecken, die die zwei verschiedenen Beteiligungsarten der Tabelle an der Abfrage darstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  
