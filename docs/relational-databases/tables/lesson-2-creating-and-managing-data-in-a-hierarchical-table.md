---
title: 'Lektion 2: Erstellen und Verwalten von Daten in einer hierarchischen Tabelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 95f55cff-4abb-4c08-97b3-e3ae5e8b24e2
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 02cfeec26e7970440af931f554e90789defdcb23
ms.sourcegitcommit: e8e013b4d4fbd3b25f85fd6318d3ca8ddf73f31e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42783011"
---
# <a name="lesson-2-create-and-manage-data-in-a-hierarchical-table"></a>Lektion 2: Erstellen und Verwalten von Daten in einer hierarchischen Tabelle
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
In Lektion 1 haben Sie eine vorhandene Tabelle so geändert, dass sie den **hierarchyid** -Datentyp verwendet. Dann haben Sie die **hierarchyid** -Spalte entsprechend der in den vorhandenen Daten gegebenen hierarchischen Darstellung gefüllt. In dieser Lektion erstellen Sie eine neue Tabelle und verwenden hierarchische Methoden, um Daten in sie einzufügen. Dann fragen Sie Daten ab und bearbeiten sie, indem Sie hierarchische Methoden verwenden. 

## <a name="prerequisites"></a>Voraussetzungen  
Zur Durchführung dieses Tutorials benötigen Sie SQL Server Management Studio, Zugriff auf einen Server, auf dem SQL-Server ausgeführt wird, und eine AdventureWorks-Datenbank.

- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installieren Sie die [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Laden Sie die [AdventureWorks 2017-Beispieldatenbank](https://docs.microsoft.com/sql/samples/adventureworks-install-configure) herunter.

Anweisungen zum Wiederherstellen von Datenbanken in SSMS finden Sie hier: [Restore a Database (Wiederherstellen einer Datenbank)](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).   
  
## <a name="create-a-table-using-the-hierarchyid-data-type"></a>Erstellen einer Tabelle mit dem Datentyp „hierarchyid“
Im folgenden Beispiel wird eine Tabelle namens EmployeeOrg erstellt, die Mitarbeiterdaten zusammen mit ihrer Berichtshierarchie aufnimmt. Das Beispiel erstellt die neue Tabelle in der Datenbank AdventureWorks2017, was jedoch optional ist. Um das Beispiel einfach zu halten, enthält die Tabelle nur fünf Spalten:  
  
-   OrgNode ist eine **hierarchyid** -Spalte, die die hierarchische Beziehung speichert.   
-   OrgLevel ist eine auf der Spalte OrgNode basierende berechnete Spalte, die die Ebene in der Hierarchie speichert. Sie wird für einen Breitensuchindex verwendet.  
-   EmployeeID enthält die typische Mitarbeiter-ID, die für Anwendungen wie beispielsweise die Gehaltsdaten verwendet wird. Bei der Entwicklung neuer Anwendungen können diese die Spalte OrgNode verwenden, und die eigene Spalte EmployeeID wird nicht benötigt.   
-   EmpName enthält den Namen des Angestellten.    
-   Title enthält den Titel des Angestellten.  

## <a name="create-the-employeeorg-table"></a>Erstellen der Tabelle „EmployeeOrg“  
  
1.  Führen Sie in einem Abfrage-Editorfenster den folgenden Code aus, um die Tabelle `EmployeeOrg` zu erstellen. Wenn Sie die Spalte `OrgNode` als Primärschlüssel mit einem gruppierten Index angeben, wird ein Tiefensuchindex erstellt:  
  
    ```sql  
    USE AdventureWorks2017 ;  
    GO  
    
    if OBJECT_ID('HumanResources.EmployeeOrg') is not null
     drop table HumanResources.EmployeeOrg 
         
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  Führen Sie den folgenden Code aus, um einen zusammengesetzten Index für die Spalten `OrgLevel` und `OrgNode` zu erstellen, der effiziente Breitensuchoperationen unterstützt:  
  
    ```sql  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
Die Tabelle ist jetzt bereit, Daten zu speichern. Die nächste Aufgabe besteht darin, die Tabelle mithilfe hierarchischer Methoden aufzufüllen.   

## <a name="populate-a-hierarchical-table-using-hierarchical-methods"></a>Auffüllen einer hierarchischen Tabelle mit hierarchischen Methoden
AdventureWorks2017 enthält 8 Mitarbeiter, die in der Marketingabteilung tätig sind. Die Angestelltenhierarchie sieht ungefähr wie folgt aus:  
  
**David**, **EmployeeID** 6, ist der Marketing-Manager. Drei Marketingspezialisten berichten **David**:  
  
-   **Sariya**, **EmployeeID** 46  
  
-   **John**, **EmployeeID** 271  
  
-   **Jill**, **EmployeeID** 119  
  
Marketingassistent **Wanida** (**EmployeeID** 269) berichtet **Sariya**, und Marketingassistent **Mary** (**EmployeeID** 272) berichtet **John**.  
  
### <a name="insert-the-root-of-the-hierarchy-tree"></a>Einfügen des Stamms in die Hierarchiestruktur  
  
1.  Das folgende Beispiel fügt den Marketing-Manager **David** als Stamm der Hierarchie in die Tabelle ein. Die Spalte **OrdLevel** ist eine berechnete Spalte. Sie ist daher kein Teil der INSERT-Anweisung. Der erste Datensatz verwendet die Methode [GetRoot()](../../t-sql/data-types/getroot-database-engine.md) , um diesem ersten Datensatz als Stamm der Hierarchie zu füllen.  
  
    ```sql  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  Führen Sie den folgenden Code aus, um die Anfangszeile in der Tabelle zu untersuchen:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```sql  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
Wie in der vorigen Lektion verwenden wir die Methode `ToString()` , um den **hierarchyid** -Datentyp in ein leichter verständliches Format zu konvertieren.  
  
### <a name="insert-a-subordinate-employee"></a>Einfügen eines unterstellten Mitarbeiters  
  
1.  **Sariya** berichtet **David**. Um **Sariyas** Knoten einzufügen, müssen Sie einen entsprechenden **OrgNode** -Wert vom Datentyp **hierarchyid**erstellen. Das folgende Beispiel erstellt eine Variable des Datentyps **hierarchyid** und füllt sie mit dem OrgNode-Stammwert der Tabelle. Diese Variable wird zusammen mit der Methode [GetDescendant()](../../t-sql/data-types/getdescendant-database-engine.md) verwendet, um eine Zeile einzufügen, die den untergeordneten Knoten darstellt. `GetDescendant` übernimmt zwei Argumente. Für die Argumentwerte gelten die folgenden Optionen:  
  
    -   Ist parent NULL, gibt `GetDescendant` NULL zurück.  
    -   Ist parent nicht NULL und sind sowohl child1 als auch child2 NULL, dann gibt `GetDescendant` einen parent untergeordneten Knoten zurück.  
    -   Sind parent und child1 nicht NULL und ist child2 NULL, dann gibt `GetDescendant` einen parent untergeordneten Knoten zurück, der größer als child1 ist.   
    -   Sind parent und child2 nicht NULL und ist child1 NULL, dann gibt `GetDescendant` einen parent untergeordneten Knoten zurück, der kleiner als child2 ist.   
    -   Sind parent, child1 und child2 alle nicht NULL, dann gibt `GetDescendant` einen parent untergeordneten Knoten zurück, der größer als child1 und kleiner als child2 ist.  
  
    Der folgende Code verwendet die Argumente `(NULL, NULL)` des Stammknotens, da außer diesem Stammknoten noch keine Zeilen in der Tabelle vorhanden sind. Führen Sie den folgenden Code aus, um **Sariya**einzufügen:  
  
    ```sql  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  Wiederholen Sie die Abfrage der ersten Prozedur, um die Tabelle abzufragen und zu sehen, wie die Einträge angezeigt werden:  
  
    ```sql  
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
  
### <a name="create-a-procedure-for-entering-new-nodes"></a>Erstellen eines Verfahrens zum Einfügen neuer Knoten  
  
1.  Um die Eingabe der Daten zu vereinfachen, erstellen Sie die folgende gespeicherte Prozedur, um Mitarbeiterdaten in die Tabelle **EmployeeOrg** einzufügen. Die Prozedur akzeptiert Eingabewerte über den Mitarbeiter, der hinzugefügt wird. Diese Daten bestehen aus der **EmployeeID** des Vorgesetzten des neuen Mitarbeiters, der **EmployeeID** des neuen Mitarbeiters, seinem Vornamen und seinem Titel. Die Prozedur verwendet `GetDescendant()` und auch die [GetAncestor ()](../../t-sql/data-types/getancestor-database-engine.md) -Methode. Führen Sie den folgenden Code aus, um die Prozedur zu erstellen:  
  
    ```sql  
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
  
    ```sql  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  Führen Sie auch hier wieder die folgende Abfrage aus, um die Zeilen in der Tabelle **EmployeeOrg** zu untersuchen:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```sql  
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

## <a name="query-a-hierarchical-table-using-hierarchy-methods"></a>Abfragen einer hierarchischen Tabelle mit hierarchischen Methoden
Nachdem die Tabelle HumanResources.EmployeeOrg nun vollständig gefüllt ist, zeigt Ihnen diese Aufgabe, wie Sie die Hierarchie mithilfe einiger der hierarchischen Methoden abfragen können.  
  
### <a name="find-subordinate-nodes"></a>Suchen untergeordneter Knoten  
  
1.  Sariya ist ein Mitarbeiter unterstellt. Um den unterstellten Mitarbeiter abzufragen, führen Sie die folgende Abfrage aus, die die [IsDescendantOf](../../t-sql/data-types/isdescendantof-database-engine.md) -Methode verwendet:  
  
    ```sql  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
    Das Ergebnis listet sowohl Sariya als auch Wanida auf. Sariya wird aufgelistet, weil sie Nachfolger auf Ebene 0 ist. Wanida ist Nachfolger auf Ebene 1.  
  
2.  Sie können diese Informationen auch mit der [GetAncestor](../../t-sql/data-types/getancestor-database-engine.md) -Methode abfragen. `GetAncestor` übernimmt ein Argument für die Ebene, die zurückgegeben werden soll. Da Wanida eine Ebene unter Sariya angesiedelt ist, können Sie `GetAncestor(1)` verwenden, wie der folgende Code veranschaulicht:  
  
    ```sql  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
    Dieses Mal listet das Ergebnis nur Wanida auf.  
  
3.  Ändern Sie jetzt `@CurrentEmployee` in David (EmployeeID 6) und die Ebene in 2. Führen Sie folgenden Code aus, um auch Wanida zurückzugeben:  
  
    ```sql  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
    Dieses Mal erhalten Sie auch Mary, die, zwei Ebenen darunter, ebenfalls David unterstellt ist.  
  
## <a name="use-getroot-and-getlevel"></a>Verwenden von „GetRoot“ und „GetLevel“  
  
1.  Mit dem Anwachsen der Hierarchie wird es schwieriger zu ermitteln, wo innerhalb der Hierarchie sich die Elemente befinden. Verwenden Sie die [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) -Methode, um zu ermitteln, auf welcher Ebene der Hierarchie sich eine Zeile befindet. Führen Sie den folgenden Code aus, um die Ebenen aller Zeilen anzuzeigen:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  Verwenden Sie die [GetRoot](../../t-sql/data-types/getroot-database-engine.md) -Methode, um den Stammknoten in der Hierarchie zu ermitteln. Im folgenden Code wird die einzelne Zeile, die der Stamm ist, zurückgegeben:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
   
  
## <a name="reorder-data-in-a-hierarchical-table-using-hierarchical-methods"></a>Neuanordnen von Daten in einer hierarchischen Tabelle mit hierarchischen Methoden
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Eine Hierarchie neu zu ordnen, ist eine allgemeine Wartungsaufgabe. In dieser Aufgabe werden wir eine UPDATE-Anweisung mit der [GetReparentedValue](../../t-sql/data-types/getreparentedvalue-database-engine.md) -Methode verwenden, um zunächst eine einzelne Zeile an eine neue Position in der Hierarchie zu verschieben. Dann verschieben wir eine ganze Teilstruktur an eine neue Position.  
  
Die `GetReparentedValue` -Methode benötigt zwei Argumente. Das erste Argument beschreibt den Teil der Hierarchie, der geändert werden soll. Möchten Sie zum Beispiel in der Hierarchie **/1/4/2/3/** den Abschnitt **/1/4/** so ändern, dass die Hierarchie zu **/2/1/2/3/** wird, wobei die beiden letzten Knoten (**2/3/**) unverändert bleiben, müssen Sie die zu ändernden Knoten (**/1/4/**) als erstes Argument angeben. Das zweite Argument gibt die neue Hierarchieebene an, in unserem Beispiel **/2/1/**. Die zwei Argumente dürfen nicht die gleichen Ebenennummern enthalten.  
  
### <a name="move-a-single-row-to-a-new-location-in-the-hierarchy"></a>Verschieben einer einzelnen Zeile an eine neue Position in der Hierarchie  
  
1.  Wanida berichtet aktuell Sariya. In dieser Prozedur verschieben Sie Wanida von ihrem aktuellen Knoten **/1/1/** so, dass sie Jill berichtet. Ihr neuer Knoten wird **/3/1/** , daher ist **/1/** das erste Argument und **/3/** das zweite. Diese Werte entsprechen den **OrgNode** -Werten von Sariya und Jill. Führen Sie den folgenden Code aus, um Wanida von Sariyas Organisation in die Jills zu verschieben:  
  
    ```sql  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  Führen Sie den folgenden Code aus, um die Ergebnisse sehen zu können:  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    Wanida ist jetzt dem Knoten **/3/1/** zugeordnet.  
  
### <a name="reorganize-a-section-of-a-hierarchy"></a>Reorganisieren eines Abschnitts einer Hierarchie  
  
1.  Um zu veranschaulichen, wie eine größere Anzahl von Leuten gleichzeitig verschoben werden kann, führen Sie zunächst den folgenden Code aus, um einen neuen Mitarbeiter einzufügen, der Wanida berichtet:  
  
    ```sql  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  Jetzt berichtet Kevin Wanida, der Jill berichtet, die ihrerseits David berichtet. Das bedeutet, dass sich Kevin auf Ebene **/3/1/1/** befindet. Um alle Untergebenen von Jill zu einem neuen Manager zu verschieben, aktualisieren wir alle Knoten mit dem Wert **/3/** für **OrgNode** mit einem neuen Wert. Führen Sie den folgenden Code aus, um Wanida so zu aktualisieren, dass sie Sariya unterstellt ist; Kevin hingegen soll weiterhin Wanida unterstellt sein:  
  
    ```sql  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  Führen Sie den folgenden Code aus, um die Ergebnisse sehen zu können:  
  
    ```sql  
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
/1/1/1/      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
Die gesamte Organisationsstruktur, die Jill (sowohl Wanida als auch Kevin) berichtet hatte, berichtet jetzt Sariya.  
  
Eine gespeicherte Prozedur für die Neuorganisation eines Bereichs einer Hierarchie finden Sie im Abschnitt „Verschieben von Teilstrukturen“ unter [Hierarchische Daten (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md#BKMK_MovingSubtrees).  
  
