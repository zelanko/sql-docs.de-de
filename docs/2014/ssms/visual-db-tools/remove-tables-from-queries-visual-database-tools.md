---
title: Entfernen von Tabellen aus Abfragen (Visual Database Tools)|Microsoft-Dokumente
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bda582c7b9171e89a43b6870b3b6c2df139b7b11
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62670463"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a>Entfernen von Tabellen aus Abfragen (Visual Database Tools)
  Sie können eine Tabelle oder ein Tabellenwertobjekt aus der Abfrage entfernen.  
  
> [!NOTE]  
>  Beim Entfernen einer Tabelle oder eines Tabellenwertobjekts wird das entsprechende Objekt nur aus der Abfrage entfernt und nicht aus der Datenbank selbst. Weitere Informationen zum Entfernen von Tabellen aus einer Datenbank finden Sie unter [Löschen von Tabellen &#40;Datenbank-Engine&#41;](../../relational-databases/tables/delete-tables-database-engine.md).  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>So entfernen Sie eine Tabelle oder ein Objekt mit Tabellenstruktur  
  
-   Wählen Sie im **Diagrammbereich**die Tabelle, die Sicht, die benutzerdefinierte Funktion, das Synonym oder die Abfrage aus, und drücken Sie anschließend ENTF, oder klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie im daraufhin angezeigten Dialogfeld den Befehl **Entfernen** aus. Sie können mehrere Objekte auswählen und gleichzeitig entfernen.  
  
     -oder-  
  
-   Entfernen Sie im **SQL-Bereich**alle Verweise auf das Objekt.  
  
 Wenn Sie eine Tabelle oder ein Tabellenwertobjekt entfernen, werden vom Abfrage- und Sicht-Designer Verknüpfungen mit dieser Tabelle oder diesem Tabellenwertobjekt automatisch entfernt. Außerdem werden Verweise auf die Spalten des Objekts aus dem **SQL-Bereich** und dem **Kriterienbereich**entfernt. Wenn die Abfrage jedoch komplexe, auf das Objekt bezogene Ausdrücke enthält, wird das Objekt erst nach dem Entfernen aller zugehörigen Verweise entfernt.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Tabellen zu Abfragen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Erstellen von Tabellenaliasen &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md)   
 [Angeben von Suchkriterien &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
