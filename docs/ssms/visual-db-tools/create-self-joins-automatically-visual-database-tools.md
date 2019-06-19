---
title: Automatisches Erstellen von Selbstverknüpfungen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 770d6c0813d210843f4606783aa3e9e025b81eb3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65095640"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Automatisches Erstellen von Selbstjoins (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Wenn die Tabelle über eine reflexive Beziehung in der Datenbank verfügt, können Sie diese automatisch mit sich selbst verknüpfen.  
  
### <a name="to-create-a-self-join-automatically"></a>So erstellen Sie automatisch einen Selbstjoin  
  
1.  Fügen Sie dem [Diagrammbereich](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) die Tabelle hinzu, mit der Sie arbeiten möchten.  
  
2.  Fügen Sie dieselbe Tabelle erneut hinzu, sodass die Tabelle im Diagrammbereich zweimal angezeigt wird.  
  
    Der [Abfrage- und Sicht-Designer](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) weist der zweiten Instanz einen Alias zu, indem er dem Tabellennamen eine laufende Nummer hinzufügt. Außerdem erstellt der Abfrage- und Sicht-Designer eine Joinlinie zwischen den zwei Rechtecken, die die zwei verschiedenen Beteiligungsarten der Tabelle an der Abfrage darstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
