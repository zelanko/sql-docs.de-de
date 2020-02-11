---
title: Angeben mehrerer Suchbedingungen für mehrere Spalten (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 06617729-0d0b-4da2-9890-b7e2f5cdbc7b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3580f6365866ce752191e285b14f7d793be0cad0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63204945"
---
# <a name="specify-multiple-search-conditions-for-multiple-columns-visual-database-tools"></a>Angeben mehrerer Suchbedingungen für mehrere Spalten (Visual Database Tools)
  Sie können den Bereich der Abfrage erweitern oder einschränken, indem Sie verschiedene Spalten in die Suchbedingung aufnehmen. Auf diese Weise können Sie beispielsweise folgende Vorgänge durchführen:  
  
-   Sie können nach Mitarbeitern suchen, die entweder seit mehr als fünf Jahren in der Firma arbeiten oder bestimmte Tätigkeiten ausführen.  
  
-   Sie können nach einem Buch suchen, das von einem bestimmten Herausgeber veröffentlicht wurde und gleichzeitig ein Kochbuch ist.  
  
 Für einer Abfrage, die in zwei oder mehr Spalten nach Werten sucht, wird eine OR-Bedingung verwendet. Demgegenüber wird zur Erstellung einer Abfrage, die alle Bedingungen in zwei oder mehr Spalten erfüllen muss, eine AND-Bedingung eingesetzt.  
  
## <a name="specifying-an-or-condition"></a>Angeben einer OR-Bedingung  
 Wenn Sie mehrere mit OR verknüpfte Bedingungen erstellen möchten, setzen Sie jede Bedingung in eine andere Spalte des Kriterienbereichs.  
  
#### <a name="to-specify-an-or-condition-for-two-different-columns"></a>So geben Sie eine OR-Bedingung für zwei verschiedene Spalten an  
  
1.  Fügen Sie dem [Kriterienbereich](visual-database-tools.md)die Spalten hinzu, die durchsucht werden sollen.  
  
2.  Geben Sie in der Spalte **Filter** für die erste zu durchsuchende Spalte die erste Bedingung an.  
  
3.  Geben Sie in der Spalte **Oder** für die zweite zu durchsuchende Datenspalte die zweite Bedingung an, und lassen Sie die Spalte **Filter** leer.  
  
     Der Abfrage- und Sicht-Designer erstellt eine WHERE-Klausel mit einer OR-Bedingung, z. B.:  
  
    ```  
    SELECT job_lvl, hire_date  
    FROM employee  
    WHERE (job_lvl >= 200) OR   
      (hire_date < '01/01/1998')  
    ```  
  
4.  Wiederholen Sie die Schritte 2 und 3 für jede weitere Bedingung, die hinzugefügt werden soll. Verwenden Sie für jede neue Bedingung eine neue Spalte **Oder...** .  
  
## <a name="specifying-an-and-condition"></a>Angeben einer AND-Bedingung  
 Um verschiedene Datenspalten nach Bedingungen zu durchsuchen, die mit AND verknüpft sind, setzen Sie alle Bedingungen in die Datenblattspalte **Filter** .  
  
#### <a name="to-specify-an-and-condition-for-two-different-columns"></a>So geben Sie eine AND-Bedingung für zwei verschiedene Spalten an  
  
1.  Fügen Sie dem [Kriterienbereich](visual-database-tools.md)die Spalten hinzu, die durchsucht werden sollen.  
  
2.  Geben Sie in der Spalte **Filter** für die erste zu durchsuchende Datenspalte die erste Bedingung an.  
  
3.  Geben Sie in der Spalte **Filter** für die zweite Datenspalte die zweite Bedingung an.  
  
     Der Abfrage- und Sicht-Designer erstellt eine WHERE-Klausel mit einer AND-Bedingung, z. B.:  
  
    ```  
    SELECT pub_id, title  
    FROM titles  
    WHERE (pub_id = '0877') AND (title LIKE '%Cook%')  
    ```  
  
4.  Wiederholen Sie die Schritte 2 und 3 für jede weitere Bedingung, die hinzugefügt werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kombinieren von Bedingungen, wenn und Vorrang &#40;Visual Database Tools haben&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md)   
 [Kombinieren von Bedingungen, wenn or Vorrang &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md)   
 [Konventionen für das Kombinieren von Suchbedingungen im Kriterienbereich &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)   
 [Angeben von Suchkriterien &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
