---
title: 'Lektion 1: Konvertieren einer Tabelle in eine hierarchische Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/22/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 83871be7e8de5976eee684788d7a1a852aaa7c8a
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582147"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Lektion 1: Konvertieren einer Tabelle in eine hierarchische Struktur
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Kunden mit Tabellen, die hierarchische Beziehungen mithilfe von Selbstjoins darstellen, können diese Tabellen in eine hierarchische Struktur konvertieren, indem Sie diese Lektion als Richtlinie verwenden. Es ist relativ leicht, von dieser Darstellung zu einer mit **hierarchyid**zu migrieren. Nach der Migration verfügen die Benutzer über ein grundlegendes Verständnis hierarchischer Darstellungen, die für effizientere Abfragen auf verschiedene Weise indiziert werden können.  
  
In dieser Lektion wird eine vorhandene Tabelle untersucht und eine neue Tabelle mit einer **hierarchyid** -Spalte erstellt. Daraufhin wird diese Tabelle mit den Daten der Quelltabelle gefüllt, und schließlich werden drei Indizierungsstrategien dargestellt. Diese Lektion enthält die folgenden Themen:  
 
  
## <a name="prerequisites"></a>Voraussetzungen  
Zur Durchführung dieses Tutorials benötigen Sie SQL Server Management Studio, Zugriff auf einen Server, auf dem SQL-Server ausgeführt wird, und eine AdventureWorks-Datenbank.

- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installieren Sie die [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Laden Sie die [AdventureWorks 2017-Beispieldatenbank](https://docs.microsoft.com/sql/samples/adventureworks-install-configure) herunter.

Anweisungen zum Wiederherstellen von Datenbanken in SSMS finden Sie hier: [Wiederherstellen einer Datenbank](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).  

## <a name="examine-the-current-structure-of-the-employee-table"></a>Untersuchen der aktuellen Struktur der Mitarbeitertabelle
Die Beispieldatenbank Adventureworks2017 (oder höher) enthält im Schema **HumanResources** die Tabelle **Employee**. Um Änderungen an der ursprünglichen Tabelle zu vermeiden, wird in diesem Schritt eine Kopie der Tabelle **Employee** mit dem Namen **EmployeeDemo**erstellt. Um das Beispiel zu vereinfachen, kopieren Sie nur fünf Spalten aus der ursprünglichen Tabelle. Dann fragen Sie die Tabelle **HumanResources.EmployeeDemo** ab, um zu sehen, wie die Daten in einer Tabelle strukturiert werden, wenn der **hierarchyid** -Datentyp nicht verwendet wird.  
  
### <a name="copy-the-employee-table"></a>Kopieren der Mitarbeitertabelle  
  
1.  Führen Sie in einem Abfrage-Editorfenster den folgenden Code aus, um die Tabellenstruktur und die Daten der Tabelle **Employee** in eine neue Tabelle namens **EmployeeDemo**zu kopieren. Da die ursprüngliche Tabelle bereits HierarchyID verwendet, vereinfacht diese Abfrage die Hierarchie, um den Manager des Mitarbeiters abzurufen. Im weiteren Verlauf dieser Lektion rekonstruieren Sie diese Hierarchie.

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    ```sql  
    USE AdventureWorks2017;  
    GO  
      if OBJECT_ID('HumanResources.EmployeeDemo') is not null
     drop table HumanResources.EmployeeDemo 

    SELECT emp.BusinessEntityID AS EmployeeID, emp.LoginID, 
      (SELECT  man.BusinessEntityID FROM HumanResources.Employee man 
            WHERE emp.OrganizationNode.GetAncestor(1)=man.OrganizationNode OR 
                (emp.OrganizationNode.GetAncestor(1) = 0x AND man.OrganizationNode IS NULL)) AS ManagerID,
           emp.JobTitle, emp.HireDate
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee emp ;
    GO
    ```  
  
### <a name="examine-the-structure-and-data-of-the-employeedemo-table"></a>Untersuchen der Struktur und Daten der Tabelle „EmployeeDemo“  
  
-   Die neue Tabelle **EmployeeDemo** stellt eine typische Tabelle einer vorhandenen Datenbank dar, die in eine neue Struktur migriert werden soll. Führen Sie in einem Abfrage-Editorfenster den folgenden Code aus, um zu zeigen, wie die Mitarbeiter-Manager-Beziehungen mithilfe eines Selbstjoins dargestellt werden:  
  
    ```sql  
    SELECT   
        Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
        Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.JobTitle  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  JobTitle  
    NULL    NULL                    1   adventure-works\ken0        Chief Executive Officer
    1   adventure-works\ken0        2   adventure-works\terri0      Vice President of Engineering
    1   adventure-works\ken0       16   adventure-works\david0    Marketing Manager
    1   adventure-works\ken0       25   adventure-works\james1    Vice President of Production
    1   adventure-works\ken0      234   adventure-works\laura1    Chief Financial Officer
    1   adventure-works\ken0    263 adventure-works\jean0       Information Services Manager
    1   adventure-works\ken0      273   adventure-works\brian3    Vice President of Sales
    2   adventure-works\terri0    3 adventure-works\roberto0    Engineering Manager
    3   adventure-works\roberto0    4   adventure-works\rob0        Senior Tool Designer
    ...  
    ```  
  
    Die Ausgabe umfasst insgesamt 290 Zeilen.  
  
Beachten Sie, dass die **ORDER BY** -Klausel bewirkt, dass die Mitarbeiter, die einer Managementebene direkt unterstellt sind, jeweils zusammen aufgelistet werden. So werden beispielsweise die sieben Mitarbeiter, die **MgrID** 1 (ken0) direkt unterstellt sind, nebeneinander aufgeführt. Es ist zwar nicht unmöglich, aber sehr viel schwieriger, alle Mitarbeiter zu gruppieren, die **MgrID** 1 auch indirekt unterstellt sind.  


## <a name="populate-a-table-with-existing-hierarchical-data"></a>Auffüllen einer Tabelle mit vorhandenen hierarchischen Daten
In dieser Aufgabe wird eine neue Tabelle erstellt und mit den Daten aus der Tabelle **EmployeeDemo** aufgefüllt. Diese Aufgabe umfasst die folgenden Schritte:  
  
-   Erstellen Sie eine neue Tabelle, die eine **hierarchyid** -Spalte enthält. Diese Spalte könnte die vorhandenen Spalten **EmployeeID** und **ManagerID** ersetzen. Sie behalten diese Spalten jedoch bei, weil bestehende Anwendungen möglicherweise auf diese Spalten verweisen und weil dann die Daten nach der Übertragung leichter verständlich sind. Gemäß der Tabellendefinition ist **OrgNode** der Primärschlüssel, so dass diese Spalte eindeutige Werte enthalten muss. Der gruppierte Index der Spalte **OrgNode** speichert das Datum in **OrgNode** -Sequenz.    
-   Erstellen Sie eine temporäre Tabelle, mit deren Hilfe verfolgt wird, wie viele Mitarbeiter jedem Manager direkt unterstellt sind. 
-   Füllen Sie die neue Tabelle mit Daten aus der Tabelle **EmployeeDemo** auf.  
  
### <a name="to-create-a-new-table-named-neworg"></a>So erstellen Sie eine neue Tabelle namens NewOrg  
  
-   Führen Sie in einem Abfrage-Editorfenster den folgenden Code aus, um eine einfache Tabelle namens **HumanResources.NewOrg**zu erstellen.  
  
    ```sql   
    CREATE TABLE HumanResources.NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="create-a-temporary-table-named-children"></a>Erstellen einer temporären Tabelle namens „#Children“  
  
1.  Erstellen Sie eine temporäre Tabelle namens **#Children** mit einer Spalte namens **Num** , in der für jeden Knoten die Anzahl der untergeordneten Elemente verzeichnet wird:  
  
    ```sql  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  Fügen Sie einen Index hinzu, der die Abfrage, mit der die Tabelle **NewOrg** aufgefüllt wird, erheblich beschleunigt:  
  
    ```sql  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="populate-the-neworg-table"></a>Auffüllen der Tabelle „NewOrg“  
  
1.  In rekursiven Abfragen sind Unterabfragen mit Aggregaten nicht zulässig. Füllen Sie die Tabelle **#Children** stattdessen mit folgendem Code auf, in dem die [ROW_NUMBER()](../../t-sql/functions/row-number-transact-sql.md) -Methode zum Auffüllen der Spalte **Num** verwendet wird:  
  
    ```sql 
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM HumanResources.EmployeeDemo  
    GO 
    ```  
  
2.  Überprüfen Sie die Tabelle **#Children** . Die Spalte **Num** enthält fortlaufende Nummern für die einzelnen Manager.  
  
    ```sql  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

    ```
    EmployeeID  ManagerID   Num
    1   NULL    1
    2        1    1
    16     1      2
    25     1      3
    234    1      4
    263    1      5
    273    1      6
    3        2    1
    4        3    1
    5        3    2
    6        3    3
    7        3    4
    ```


3.  Füllen Sie die Tabelle **NewOrg** auf. Verwenden Sie die Methoden GetRoot und ToString, um die Werte der Spalte **Num** zu verketten, so dass sie dem **hierarchyid** -Format entsprechen, und aktualisieren Sie anschließend die Spalte **OrgNode** mit den resultierenden hierarchischen Werten:  
  
    ```sql  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   

    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT HumanResources.NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM HumanResources.EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO 
    ```  
  
4.  Eine **hierarchyid** -Spalte ist verständlicher, wenn sie in das Zeichenformat konvertiert wird. Überprüfen Sie die Daten der Tabelle **NewOrg** , indem Sie den folgenden Code ausführen, der zwei Darstellungen der Spalte **OrgNode** enthält:  
  
    ```sql  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM HumanResources.NewOrg   
    ORDER BY LogicalNode;  
    GO  
    ```  
  
    Die Spalte **LogicalNode** konvertiert die **hierarchyid** -Spalte in ein lesbareres Textformat, das die Hierarchie darstellt. In den restlichen Aufgaben werden Sie die `ToString()` -Methode verwenden, um die **hierarchyid** -Spalten im logischen Format anzuzeigen.  
  
5.  Löschen Sie die temporäre Tabelle, die nicht mehr benötigt wird:  
  
    ```sql  
    DROP TABLE #Children  
    GO  
    ```  
  
## <a name="optimizing-the-neworg-table"></a>Optimieren der NewOrg-Tabelle
Die **NewOrd** -Tabelle, die Sie in der Aufgabe [Populating a Table with Existing Hierarchical Data](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) erstellt haben, enthält alle Angestellteninformationen und stellt die hierarchische Struktur mithilfe des **hierarchyid** -Datentyps dar. In dieser Aufgabe werden neue Indizes hinzugefügt, die das Suchen in der **hierarchyid** -Spalte unterstützen.  
  

Die Spalte **hierarchyid** (**OrgNode**) ist der Primärschlüssel für die **NewOrg** -Tabelle. Als die Tabelle erstellt wurde, enthielt sie den gruppierten Index **PK_NewOrg_OrgNode** , der die Eindeutigkeit der **OrgNode** -Spalte erzwingen sollte. Dieser gruppierte Index unterstützt auch eine Tiefensuche in der Tabelle.  
  
  
### <a name="create-index-on-neworg-table-for-efficient-searches"></a>Erstellen eines Index für die Tabelle „NewOrg“ für effiziente Suchvorgänge  
  
1.  Verwenden Sie zur Unterstützung von Abfragen der gleichen Ebene in der Hierarchie die [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) -Methode, um eine berechnete Spalte zu erstellen, welche die Ebene in der Hierarchie enthält. Erstellen Sie dann für diese und die **Hierarchyid**-Spalte einen zusammengesetzten Index. Führen Sie den folgenden Code aus, um die berechnete Spalte und den Breitensuchindex zu erstellen:  
  
    ```sql  
    ALTER TABLE HumanResources.NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON HumanResources.NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  Erstellen Sie für die Spalte **EmployeeID** einen eindeutigen Index. Dies ist der übliche Singleton-Suchvorgang nach einem einzelnen Mitarbeiter entsprechend der **EmployeeID** -Nummer. Führen Sie den folgenden Code aus, um für **EmployeeID**einen Index zu erstellen:  
  
    ```sql  
    CREATE UNIQUE INDEX EmpIDs_unq ON HumanResources.NewOrg(EmployeeID) ;  
    GO
    ```  
  
3.  Fügen Sie folgenden Code aus, um die Daten der Tabelle in der Reihenfolge jedes der drei Indizes abzurufen.  
  
    ```sql  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM HumanResources.NewOrg   
    ORDER BY OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY H_Level, OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  Vergleichen Sie die Resultsets, um zu sehen, wie die Reihenfolge in jedem Indextyp gespeichert wird. Im Folgenden werden nur die ersten vier Zeilen jeder Ausgabe gezeigt.  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    Tiefensuchindex: Mitarbeiterdatensätze sind angrenzend an den ihres Managers gespeichert.  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    ```

    Index sortiert nach **EmployeeID**: Die Zeilen werden in der Reihenfolge der **EmployeeID** gespeichert.  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    /1/1/5/1/   0x5AE358    4   12  adventure-works\thierry0
    ```
  
> [!NOTE]  
> Diagramme, die den Unterschied zwischen einem Tiefensuchindex und einem Breitensuchindex zeigen, finden Sie unter [Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md).  
  
### <a name="drop-the-unnecessary-columns"></a>Löschen der unnötigen Spalten  
  
1.  Die Spalte **ManagerID** stellt die Mitarbeiter-/Managerbeziehung dar, die jetzt von der Spalte **OrgNode** dargestellt wird. Wenn andere Anwendungen die Spalte **ManagerID** nicht benötigen, könnten Sie diese Spalte löschen, indem Sie die folgende Anweisung verwenden:  
  
    ```sql  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  Die Spalte **EmployeeID** ist ebenfalls überflüssig. Jeder Mitarbeiter wird bereits durch die Spalte **OrgNode** eindeutig identifiziert. Wenn andere Anwendungen die Spalte **EmployeeID** nicht benötigen, könnten Sie den Index und dann die Spalte löschen, indem Sie folgenden Code verwenden:  
  
    ```sql  
    DROP INDEX EmpIDs_unq ON HumanResources.NewOrg ;  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
### <a name="replace-the-original-table-with-the-new-table"></a>Ersetzen der ursprünglichen durch die neue Tabelle  
  
1.  Wenn die ursprüngliche Tabelle irgendwelche zusätzlichen Indizes oder Einschränkungen enthält, dann fügen Sie diese der Tabelle **NewOrg** hinzu.  
  
2.  So ersetzen Sie die alte **EmployeeDemo** -Tabelle durch die neue Tabelle. Führen Sie folgenden Code aus, um die alte Tabelle zu löschen und dann die neue Tabelle mit dem Namen der alten Tabelle zu benennen:  
  
    ```sql  
    DROP TABLE HumanResources.EmployeeDemo ;  
    GO  
    sp_rename 'HumanResources.NewOrg', 'EmployeeDemo' ;  
    GO  
    ```  
  
3.  Führen Sie den folgenden Code aus, um die neue Tabelle zu untersuchen:  
  
    ```sql  
    SELECT * FROM HumanResources.EmployeeDemo ;  
    ```  
  
## <a name="next-steps"></a>Nächste Schritte
Im nächsten Artikel lernen Sie, Daten in einer hierarchischen Tabelle zu erstellen und zu verwalten. 

Zum nächsten Artikel wechseln, um mehr zu erfahren:
> [!div class="nextstepaction"]
> [Nächste Schritte](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)
