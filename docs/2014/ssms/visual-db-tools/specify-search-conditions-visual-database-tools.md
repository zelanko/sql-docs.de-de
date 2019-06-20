---
title: Angeben von Suchbedingungen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 75b29477c7ead402f06c9df2505a84636b906978
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63163959"
---
# <a name="specify-search-conditions-visual-database-tools"></a>Angeben von Suchbedingungen (Visual Database Tools)
  Sie können die Datenzeilen festlegen, die in die Abfrage aufgenommen werden sollen, indem Sie Suchbedingungen angeben. Wenn Sie beispielsweise die Tabelle `employee` abfragen, können Sie angeben, dass Sie nur diejenigen Mitarbeiter suchen, die in einem bestimmten Gebiet arbeiten.  
  
 Suchbedingungen werden mithilfe eines Ausdrucks angegeben. In der Regel besteht der Ausdruck aus einem Operator und einem Suchwert. Um beispielsweise Mitarbeiter in einem bestimmten Absatzgebiet zu suchen, können Sie für die Spalte `region` das folgende Suchkriterium angeben:  
  
```  
='UK'  
```  
  
> [!NOTE]  
>  Wenn Sie mit mehreren Tabellen arbeiten, überprüft der Abfrage- und Sicht-Designer jede Bedingung daraufhin, ob der durchgeführte Vergleich zu einem Join führt. Wenn dies der Fall ist, konvertiert der Abfrage- und Sicht-Designer die Suchbedingung automatisch in einen Join. Weitere Informationen finden Sie unter [Automatisches Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
### <a name="to-specify-search-conditions"></a>So geben Sie Suchbedingungen an  
  
1.  Fügen Sie im Kriterienbereich die Spalten oder Ausdrücke hinzu, die in der Suchbedingung verwendet werden sollen, falls dies nicht bereits geschehen ist.  
  
     Wenn Sie eine Select-Abfrage erstellen, für die in der Abfrageausgabe keine Suchspalten bzw. Suchausdrücke angezeigt werden sollen, löschen Sie für jede Suchspalte und jeden Suchausdruck die Spalte **Ausgabe** , um sie als Ausgabespalten zu entfernen.  
  
2.  Wechseln Sie zu der Zeile, die die Datenspalte oder den Ausdruck für die Suche enthält, und geben Sie in der Spalte **Filter** eine Suchbedingung an.  
  
    > [!NOTE]  
    >  Wenn Sie keinen Operator eingeben, fügt der Abfrage- und Sicht-Designer automatisch den Gleichheitsoperator "=" ein.  
  
 Der Abfrage- und Sicht-Designer aktualisiert die SQL-Anweisung im [SQL-Bereich](sql-pane-visual-database-tools.md) durch Hinzufügen oder Ändern der WHERE-Klausel.  
  
## <a name="see-also"></a>Siehe auch  
 [Regeln für das Eingeben von Suchwerten &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Angeben von Suchkriterien &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
