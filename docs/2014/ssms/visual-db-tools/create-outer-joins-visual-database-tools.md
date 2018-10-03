---
title: Erstellen von äußeren Joins (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- joins [SQL Server], outer
ms.assetid: 18de47b1-f936-427d-b852-fe6d20334f71
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 276c377b6963c2c58be26187079bc60bf619a90a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141650"
---
# <a name="create-outer-joins-visual-database-tools"></a>Erstellen von äußeren Joins (Visual Database Tools)
  In der Standardeinstellung wird vom [Abfrage- und Sicht-Designer](visual-database-tools.md) ein innerer Join zwischen Tabellen erstellt. Innere Joins entfernen die Zeilen, die nicht mit einer Zeile aus der anderen Tabelle übereinstimmen. Äußere Joins dagegen geben alle Zeilen aus mindestens einer der in der FROM-Klausel genannten Tabellen oder Sichten zurück, sofern diese Zeilen ggf. die WHERE- oder HAVING-Suchbedingungen erfüllen. Wenn Sie Datenzeilen in das Resultset einschließen möchten, die keine Übereinstimmung in der verknüpften Tabelle aufweisen, können Sie einen äußeren Join erstellen.  
  
 Beim Erstellen eines äußeren Join ist die Reihenfolge relevant, in der Tabellen in der SQL-Anweisung angezeigt werden (wie im SQL-Bereich widergespiegelt). Die zuerst hinzugefügte Tabelle wird als "linke" Tabelle und die zweite hinzugefügte Tabelle als "rechte" Tabelle betrachtet. (Die tatsächliche Reihenfolge, in der die Tabellen im [Diagrammbereich](diagram-pane-visual-database-tools.md) angezeigt werden, spielt keine Rolle.) Durch das Angeben eines linken oder rechten äußeren Joins verweisen Sie auf die Reihenfolge, in der Tabellen zur Abfrage hinzugefügt wurden, sowie auf die Reihenfolge, in der sie in der SQL-Anweisung im [SQL-Bereich](sql-pane-visual-database-tools.md) angezeigt werden.  
  
### <a name="to-create-an-outer-join"></a>So erstellen Sie einen äußeren Joins  
  
1.  Erstellen Sie den Joins automatisch oder manuell. Weitere Informationen finden Sie unter [Automatisches Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) oder [Manuelles Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).  
  
2.  Wählen Sie die Joinlinie im Diagrammbereich und dann aus der **Abfrage-Designer** Menü wählen **wählen alle Zeilen aus \<Tablename >**, wählen Sie den Befehl, der die Tabelle enthält, deren zusätzliche Zeilen, die Sie einschließen möchten.  
  
    -   Wählen Sie die erste Tabelle aus, um eine linken äußeren Joins zu erstellen.  
  
    -   Wählen Sie die zweite Tabelle aus, um eine rechten äußeren Joins zu erstellen.  
  
    -   Wählen Sie beide Tabellen aus, um eine vollständigen äußeren Joins zu erstellen.  
  
 Wenn Sie angeben, ändert der Abfrage- und Sicht-Designer die Joinlinie zum Anzeigen eines äußeren Joins.  
  
 Außerdem ändert der Abfrage- und Sicht-Designer die SQL-Anweisung im SQL-Bereich, um die Änderung des Jointyps widerzuspiegeln, wie in der folgenden Anweisung dargestellt:  
  
```  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
```  
  
 Da ein äußerer Join Zeilen ohne Übereinstimmungen einschließt, kann diese zum Suchen von Zeilen verwendet werden, die Fremdschlüsseleinschränkungen verletzen. Erstellen Sie hierzu einen äußeren Join, und fügen Sie anschließend eine Suchbedingung zum Suchen von Zeilen hinzu, in denen die Primärschlüsselspalte der äußersten rechten Tabelle Null ist. Mit dem folgenden äußeren Join werden z. B. Zeilen in der Tabelle `employee` gesucht, für die keine übereinstimmenden Zeilen in der Tabelle `jobs` vorhanden sind:  
  
```  
SELECT employee.emp_id, employee.job_id  
FROM employee LEFT OUTER JOIN jobs   
   ON employee.job_id = jobs.job_id  
WHERE (jobs.job_id IS NULL)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Abfragen mit Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)   
 [Verknüpfen (Dialogfeld) &#40;Visual Database Tools&#41;](join-dialog-box-visual-database-tools.md)  
  
  
