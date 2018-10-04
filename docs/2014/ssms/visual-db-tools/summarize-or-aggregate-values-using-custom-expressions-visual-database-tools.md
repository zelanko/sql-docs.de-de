---
title: Wertzusammenfassung oder-Aggregation über benutzerdefinierte Ausdrücke (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6af00799e343ced8005cec118398c50eb8996c7c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202080"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a>Wertzusammenfassung oder -aggregation über benutzerdefinierte Ausdrücke (Visual Database Tools)
  Zusätzlich zu den Aggregatfunktionen zum Aggregieren von Daten können Sie benutzerdefinierte Ausdrücke zum Erstellen von Aggregatwerten verwenden. Außerdem können in allen Bereichen einer Aggregatabfrage benutzerdefinierte Ausdrücke an Stelle der Aggregatfunktionen verwendet werden.  
  
 In der Tabelle `titles` kann beispielsweise eine Abfrage erstellt werden, die nicht nur den Durchschnittspreis anzeigt, sondern auch angibt, welcher Durchschnittspreis sich unter Berücksichtigung von Preisnachlässen ergeben würde.  
  
 Ausdrücke auf Grundlage von Berechnungen für einzelne Zeilen in der Tabelle können nicht in die Abfrage aufgenommen werden. Ein Ausdruck muss auf einem Aggregatwert beruhen, da während der Berechnung des Ausdrucks nur Aggregatwerte verfügbar sind.  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a>So geben Sie einen benutzerdefinierten Ausdruck für einen Zusammenfassungswert an  
  
1.  Geben Sie die Gruppen für die Abfrage an. Weitere Informationen finden Sie unter [Gruppieren von Zeilen in Abfrageergebnissen &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
2.  Setzen Sie den Cursor in eine leere Zeile im Kriterienbereich, und geben Sie dann den Ausdruck in die Spalte **Spalten** ein.  
  
     Der [Abfrage- und Sicht-Designer](query-and-view-designer-tools-visual-database-tools.md) weist dem Ausdruck automatisch einen Spaltenalias zu, damit im Abfrageergebnis eine aussagekräftige Spaltenüberschrift erstellt wird. Weitere Informationen finden Sie unter [Erstellen von Spaltenaliasen &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).  
  
3.  Wählen Sie in der Spalte **Gruppieren nach** für den jeweiligen Ausdruck die Option **Ausdruck** aus.  
  
4.  Führen Sie die Abfrage aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Sortieren und gruppieren Abfrageergebnisse &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)  
  
  
