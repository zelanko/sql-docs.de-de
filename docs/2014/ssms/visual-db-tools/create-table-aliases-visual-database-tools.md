---
title: Erstellen von Tabellenaliasen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88b3bf7552d40fb914150b8cdc5cf6d53d22ab22
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227310"
---
# <a name="create-table-aliases-visual-database-tools"></a>Erstellen von Tabellenaliasen (Visual Database Tools)
  Aliase können das Arbeiten mit Tabellennamen erleichtern. Das Verwenden von Aliasen ist in folgenden Fällen hilfreich:  
  
-   Sie möchten die Anweisung im [SQL-Bereich](visual-database-tools.md) kürzen und lesbarer machen.  
  
-   Sie verweisen in der Abfrage häufig auf den Tabellennamen, z. B. in qualifizierenden Spaltennamen, und möchten sicherstellen, dass in der Abfrage eine bestimmte Anzahl von Zeichen nicht überschritten wird. (In einigen Datenbanken ist eine maximale Länge für Abfragen festgelegt.)  
  
-   Sie verwenden mehrere Instanzen derselben Tabelle (z. B. in einem Selbstjoin) und suchen nach einer Möglichkeit, um auf die eine oder andere Instanz zu verweisen.  
  
 Sie können z. B. einen Alias `"e"` für einen Tabellennamen `employee`_`information`erstellen und in der restlichen Abfrage mit `"e"` auf die Tabelle verweisen.  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>So erstellen Sie einen Alias für eine Tabelle oder ein Tabellenwertobjekt  
  
1.  Fügen Sie der Abfrage die Tabelle oder das Tabellenwertobjekt hinzu.  
  
2.  Klicken Sie im **Diagrammbereich**mit der rechten Maustaste auf das Objekt, für das Sie einen Alias erstellen möchten, und wählen Sie anschließend im Kontextmenü **Eigenschaften** aus.  
  
3.  Geben Sie im **Eigenschaftenfenster** den Alias in das Feld **Alias** ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Tabellen zu Abfragen &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md)   
 [Sortieren und gruppieren Abfrageergebnisse &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
