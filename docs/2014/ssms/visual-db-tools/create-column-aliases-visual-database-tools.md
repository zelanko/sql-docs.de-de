---
title: Erstellen von Spaltenaliasen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: febe7ed27ed10a283cab549bc65299577d69761c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067167"
---
# <a name="create-column-aliases-visual-database-tools"></a>Erstellen von Spaltenaliasen (Visual Database Tools)
  Zur Arbeitserleichterung können Sie Aliase für Spaltennamen, Berechnungen und zusammengefasste Werte erstellen. Beispielsweise können Sie einen Spaltenalias mit folgenden Funktionen erstellen:  
  
-   Erstellen eines Spaltennamens, z. B. "Total Amount" für einen Ausdruck wie `(quantity * unit_price)` oder für eine Aggregatfunktion.  
  
-   Erstellen einer Kurzform für einen Spaltennamen, z. B. `"d_id"` für `"discounts.stor_id."`  
  
 Wenn Sie einen Spaltenalias definiert haben, können Sie den Alias in einer SELECT-Abfrage zum Angeben der Ausgabe der Abfrageergebnisse verwenden.  
  
### <a name="to-create-a-column-alias"></a>So erstellen Sie einen Spaltenalias  
  
1.  Suchen Sie im Bereich **Kriterien**die Zeile mit der Datenspalte, für die Sie einen Alias erstellen möchten, und markieren Sie diese ggf. für die Ausgabe. Wenn die Datenspalte noch nicht im Datenblatt vorhanden ist, fügen Sie sie hinzu.  
  
2.  Geben Sie in der zu dieser Zeile gehörigen Spalte **Alias** den Alias ein. Der Alias muss allen Namenskonventionen für SQL entsprechen. Wenn der eingegebene Aliasname Leerzeichen enthält, wird er vom Abfrage- und Sicht-Designer automatisch in Trennzeichen eingeschlossen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Spalten zu Abfragen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Sortieren und Gruppieren von Abfrage Ergebnissen &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Zusammenfassen von Abfrage Ergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
