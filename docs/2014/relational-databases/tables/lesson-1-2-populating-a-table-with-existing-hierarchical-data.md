---
title: Auffüllen einer Tabelle mit vorhandenen hierarchischen Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7b2614d090bce0ecf0c61db5c9a5222ec6b10951
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66110168"
---
# <a name="populating-a-table-with-existing-hierarchical-data"></a>Auffüllen einer Tabelle mit vorhandenen hierarchischen Daten
  In dieser Aufgabe wird eine neue Tabelle erstellt und mit den Daten aus der Tabelle **EmployeeDemo** aufgefüllt. Diese Aufgabe umfasst die folgenden Schritte:  
  
-   Erstellen Sie eine neue Tabelle, die eine `hierarchyid`-Spalte enthält. Diese Spalte könnte die vorhandenen Spalten **EmployeeID** und **ManagerID** ersetzen. Sie behalten diese Spalten jedoch bei, weil bestehende Anwendungen möglicherweise auf diese Spalten verweisen und weil dann die Daten nach der Übertragung leichter verständlich sind. Gemäß der Tabellendefinition ist **OrgNode** der Primärschlüssel, so dass diese Spalte eindeutige Werte enthalten muss. Der gruppierte Index der Spalte **OrgNode** speichert das Datum in **OrgNode** -Sequenz.  
  
-   Erstellen Sie eine temporäre Tabelle, mit deren Hilfe verfolgt wird, wie viele Mitarbeiter jedem Manager direkt unterstellt sind.  
  
-   Füllen Sie die neue Tabelle mit Daten aus der Tabelle **EmployeeDemo** auf.  
  
### <a name="to-create-a-new-table-named-neworg"></a>So erstellen Sie eine neue Tabelle namens NewOrg  
  
-   Führen Sie in einem Abfrage-Editorfenster den folgenden Code aus, um eine einfache Tabelle namens **HumanResources.NewOrg**zu erstellen.  
  
    ```  
    CREATE TABLE NewOrg  
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
  
### <a name="to-create-a-temporary-table-named-children"></a>So erstellen Sie eine temporäre Tabelle namens #Children  
  
1.  Erstellen Sie eine temporäre Tabelle namens **#Children** mit einer Spalte namens **Num** , in der für jeden Knoten die Anzahl der untergeordneten Elemente verzeichnet wird:  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  Fügen Sie einen Index hinzu, der die Abfrage, mit der die Tabelle **NewOrg** aufgefüllt wird, erheblich beschleunigt:  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a>So füllen Sie die Tabelle NewOrg auf  
  
1.  In rekursiven Abfragen sind Unterabfragen mit Aggregaten nicht zulässig. Füllen Sie die Tabelle **#Children** stattdessen mit folgendem Code auf, in dem die [ROW_NUMBER()](/sql/t-sql/functions/row-number-transact-sql) -Methode zum Auffüllen der Spalte **Num** verwendet wird:  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM EmployeeDemo  
    GO  
  
    ```  
  
2.  Überprüfen Sie die Tabelle **#Children** . Die Spalte **Num** enthält fortlaufende Nummern für die einzelnen Manager.  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     `EmployeeID ManagerID Num`  
  
     `---------- --------- ---`  
  
     `1        NULL       1`  
  
     `2         1         1`  
  
     `3         1         2`  
  
     `4         2         1`  
  
     `5         2         2`  
  
     `6         2         3`  
  
     `7         3         1`  
  
     `8         3         2`  
  
     `9         4         1`  
  
     `10        4         2`  
  
3.  Füllen Sie die Tabelle **NewOrg** auf. Verwenden Sie die Methoden GetRoot und ToString, zum Verketten der **Num** von Datumswerten in die `hierarchyid` formatieren, und aktualisieren Sie dann die **OrgNode** Spalte mit den resultierenden hierarchischen Werten:  
  
    ```  
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
    INSERT NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO  
  
    ```  
  
4.  Eine `hierarchyid`-Spalte ist verständlicher, wenn sie in das Zeichenformat konvertiert wird. Überprüfen Sie die Daten der Tabelle **NewOrg** , indem Sie den folgenden Code ausführen, der zwei Darstellungen der Spalte **OrgNode** enthält:  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM NewOrg   
    ORDER BY LogicalNode;  
    GO  
  
    ```  
  
     Die **LogicalNode** Spalte konvertiert die `hierarchyid` Spalte in ein lesbareres Textformat, das die Hierarchie darstellt. In den restlichen Aufgaben werden Sie die `ToString()`-Methode verwenden, um die `hierarchyid`-Spalten im logischen Format anzuzeigen.  
  
5.  Löschen Sie die temporäre Tabelle, die nicht mehr benötigt wird:  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
 In der nächsten Aufgabe werden Indizes erstellt, um die hierarchische Struktur zu unterstützen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Optimieren der NewOrg-Tabelle](lesson-1-3-optimizing-the-neworg-table.md)  
  
  
