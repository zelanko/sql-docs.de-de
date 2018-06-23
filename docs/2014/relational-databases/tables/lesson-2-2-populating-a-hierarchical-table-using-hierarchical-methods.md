---
title: Auffüllen einer hierarchischen Tabelle mit hierarchischen Methoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID
ms.assetid: 2c95fa60-5b8e-4a05-ac09-cffe2b05900a
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c513aa5fb2c1f42b0eb2fa6c82deaac96c49d3ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059770"
---
# <a name="populating-a-hierarchical-table-using-hierarchical-methods"></a>Auffüllen einer hierarchischen Tabelle mit hierarchischen Methoden
  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] hat 8 Mitarbeiter, die in der Marketingabteilung arbeiten. Die Angestelltenhierarchie sieht ungefähr wie folgt aus:  
  
 **David**, **EmployeeID** 6, ist der Marketing-Manager. Drei Marketingspezialisten berichten **David**:  
  
-   **Sariya**, **EmployeeID** 46  
  
-   **John**, **EmployeeID** 271  
  
-   **Jill**, **EmployeeID** 119  
  
 Marketingassistent **Wanida** (**EmployeeID** 269) berichtet **Sariya**, und Marketingassistent **Mary** (**EmployeeID** 272) berichtet **John**.  
  
### <a name="to-insert-the-root-of-the-hierarchy-tree"></a>So fügen Sie den Stamm in die Hierarchiestruktur ein  
  
1.  Das folgende Beispiel fügt den Marketing-Manager **David** als Stamm der Hierarchie in die Tabelle ein. Die Spalte **OrdLevel** ist eine berechnete Spalte. Sie ist daher kein Teil der INSERT-Anweisung. Der erste Datensatz verwendet die Methode [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) , um diesem ersten Datensatz als Stamm der Hierarchie zu füllen.  
  
    ```  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  Führen Sie den folgenden Code aus, um die Anfangszeile in der Tabelle zu untersuchen:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
 Wie in der vorherigen Lektion verwenden wir die `ToString()` -Methode zum Konvertieren der `hierarchyid` -Datentyp in ein Format, die leichter verstanden wird.  
  
### <a name="to-insert-a-subordinate-employee"></a>So fügen Sie einen unterstellten Mitarbeiter ein  
  
1.  **Sariya** berichtet **David**. Einzufügende **Sariyas** Knoten müssen Sie erstellen eine entsprechende **OrgNode** Wert des Datentyps `hierarchyid`. Der folgende Code erstellt eine Variable vom Datentyp `hierarchyid` und füllt sie mit dem OrgNode-Stammwert der Tabelle. Diese Variable wird zusammen mit der Methode [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) verwendet, um eine Zeile einzufügen, die den untergeordneten Knoten darstellt. `GetDescendant` übernimmt zwei Argumente. Für die Argumentwerte gelten die folgenden Optionen:  
  
    -   Ist parent NULL, gibt `GetDescendant` NULL zurück.  
  
    -   Ist parent nicht NULL und sind sowohl child1 als auch child2 NULL, dann gibt `GetDescendant` einen parent untergeordneten Knoten zurück.  
  
    -   Sind parent und child1 nicht NULL und ist child2 NULL, dann gibt `GetDescendant` einen parent untergeordneten Knoten zurück, der größer als child1 ist.  
  
    -   Sind parent und child2 nicht NULL und ist child1 NULL, dann gibt `GetDescendant` einen parent untergeordneten Knoten zurück, der kleiner als child2 ist.  
  
    -   Sind parent, child1 und child2 alle nicht NULL, dann gibt `GetDescendant` einen parent untergeordneten Knoten zurück, der größer als child1 und kleiner als child2 ist.  
  
     Der folgende Code verwendet die Argumente `(NULL, NULL)` des Stammknotens, da außer diesem Stammknoten noch keine Zeilen in der Tabelle vorhanden sind. Führen Sie den folgenden Code aus, um **Sariya**einzufügen:  
  
    ```  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  Wiederholen Sie die Abfrage der ersten Prozedur, um die Tabelle abzufragen und zu sehen, wie die Einträge angezeigt werden:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="to-create-a-procedure-for-entering-new-nodes"></a>So erstellen Sie ein Verfahren dafür, neue Knoten einzufügen  
  
1.  Um die Eingabe der Daten zu vereinfachen, erstellen Sie die folgende gespeicherte Prozedur, um Mitarbeiterdaten in die Tabelle **EmployeeOrg** einzufügen. Die Prozedur akzeptiert Eingabewerte über den Mitarbeiter, der hinzugefügt wird. Diese Daten bestehen aus der **EmployeeID** des Vorgesetzten des neuen Mitarbeiters, der **EmployeeID** des neuen Mitarbeiters, seinem Vornamen und seinem Titel. Die Prozedur verwendet `GetDescendant()` und auch die [GetAncestor ()](/sql/t-sql/data-types/getancestor-database-engine) -Methode. Führen Sie den folgenden Code aus, um die Prozedur zu erstellen:  
  
    ```  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  Im folgenden Beispiel werden die verbliebenen 4 Mitarbeiter, die **David**direkt oder indirekt berichten, hinzugefügt.  
  
    ```  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  Führen Sie auch hier wieder die folgende Abfrage aus, um die Zeilen in der Tabelle **EmployeeOrg** zu untersuchen:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    /1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
 Die Tabelle ist jetzt vollständig mit den Daten der Marketingabteilung aufgefüllt.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Abfragen einer hierarchischen Tabelle mit hierarchischen Methoden](lesson-2-3-querying-a-hierarchical-table-using-hierarchy-methods.md)  
  
  
