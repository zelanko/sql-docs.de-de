---
title: Hinzufügen von Spalten zu Abfragen (Visual Database Tools)| Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- queries [SQL Server], columns
- adding columns
ms.assetid: 82f3ba72-3d72-4fb1-8179-2a953a782787
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aef64ed8031664dcbefa7d0e30bf9f63435b292c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63015701"
---
# <a name="add-columns-to-queries-visual-database-tools"></a>Hinzufügen von Spalten zu Abfragen (Visual Database Tools)
  Wenn Sie in einer Abfrage eine Spalte verwenden möchten, müssen Sie diese der Abfrage hinzufügen. Sie haben die Möglichkeit, eine hinzugefügte Spalte im Abfrageergebnis anzeigen zu lassen und sie zum Sortieren, Durchsuchen oder Zusammenfassen des Spalteninhalts zu verwenden. Sie können festlegen, welche der in der Abfrage verwendeten Spalten beim Ausführen der Abfrage im Ergebnisbereich angezeigt werden. Weitere Informationen finden Sie unter [Entfernen von Spalten aus Abfrageergebnissen &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
> [!NOTE]  
>  Wählen Sie zum Anzeigen des Datentyps einer Spalte im Abfrage- und Sicht-Designer die Tabelle oder das Tabellenwertobjekt im **Diagrammbereich** aus, und klicken Sie im Eigenschaftenfenster auf „Spaltenliste“. Klicken Sie dann auf die **Auslassungspunkte (...)** , um das Dialogfeld **Spaltenliste** zu öffnen.  
  
 Für alle Zwecke, für die Sie eine Spalte in einer Abfrage verwenden, können Sie auch einen Ausdruck verwenden, der aus einer beliebigen Kombination von Spalten, Zeichen, Operatoren und Funktionen bestehen kann.  
  
### <a name="to-add-an-individual-column"></a>So fügen Sie eine einzelne Spalte hinzu  
  
-   Aktivieren Sie im **Diagrammbereich**das Kontrollkästchen neben der einzufügenden Spalte.  
  
     Oder  
  
-   Gehen Sie im **Kriterienbereich**zur ersten leeren Zeile des Datenblatts, klicken Sie in das Feld in der Spalte mit dem Namen **Spalte** , und wählen Sie in der Dropdownliste einen Spaltennamen aus.  
  
### <a name="to-add-all-columns-for-one-table-or-table-valued-object"></a>So fügen Sie alle Spalten einer Tabelle oder eines Tabellenwertobjekts hinzu  
  
-   Aktivieren Sie im **Diagramm**Bereich das Kontrollkästchen neben ** \*(alle Spalten)**.  
  
### <a name="to-add-all-columns-for-all-tables-and-table-structured-objects"></a>So fügen Sie alle Spalten sämtlicher Tabellen und Objekte mit Tabellenstruktur hinzu  
  
1.  Vergewissern Sie sich, dass im Bereich **Tabellenvorgänge** keine Joinlinien markiert sind.  
  
2.  Klicken Sie mit der rechten Maustaste auf einen leeren Bereich im Entwurfsfenster, und wählen Sie im Kontextmenü die Option **Eigenschaften** aus.  
  
3.  Klicken Sie im Eigenschaftenfenster auf **Alle Spalten ausgeben** , und wählen Sie in der Dropdownliste die Option **Ja** oder **Nein** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entfernen von Spalten aus Abfrage Ergebnissen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Entfernen von Spalten aus Abfragen &#40;Visual Database Tools&#41;](remove-columns-from-queries-visual-database-tools.md)   
 [Angeben von Suchkriterien &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [Zusammenfassen von Abfrage Ergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
