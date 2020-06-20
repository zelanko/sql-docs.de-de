---
title: MSSQLSERVER_8621 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e054232776435a5d7825427393e6fbfa0bf232d6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053561"
---
# <a name="mssqlserver_8621"></a>MSSQLSERVER_8621
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8621|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|OPTIMIZER_STACK_OVERFLOW_ERR|  
|Meldungstext|Der Abfrageprozessor hatte während der Abfrageoptimierung zu wenig Stapelspeicherplatz. Vereinfachen Sie die Abfrage.|  
  
## <a name="explanation"></a>Erklärung  
 Die Größe der erweiterten Abfrage ist die wahrscheinlichste Ursache für den Fehler. Die erweiterte Abfrage ersetzt in der ursprünglichen Abfrage die Definitionen aller Ansichten, berechneten Spalten, [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktionen und allgemeinen Tabellenausdrücke, auf die sie verweist, sowie kaskadierende Aktionen wie das Aktualisieren von sekundären Indizes, Ansichten und Triggern.  
  
 Höchstwahrscheinlich ist die Abfrage in einer Dimension groß, wie z. B. in der Anzahl der Tabellen, auf die von Sichtdefinitionen verwiesen wird, oder in einem sehr großen Skalarausdruck.  
  
## <a name="user-action"></a>Benutzeraktion  
 Vereinfachen Sie die Abfrage, indem Sie sie in mehrere Abfragen entlang der größten Dimension teilen. Entfernen Sie zuerst alle Abfrageelemente, die nicht wirklich erforderlich sind. Versuchen Sie dann, eine temporäre Tabelle hinzuzufügen und die Abfrage in zwei Teile zu teilen.  Es genügt nicht, lediglich einen Teil der Abfrage in eine Unterabfrage, eine Funktion oder einen allgemeinen Tabellenausdruck zu verschieben, da diese durch den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Compiler erneut kombiniert werden.  
  
  
