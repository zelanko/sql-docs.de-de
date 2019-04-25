---
title: Optimieren der NewOrg-Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a031466e35fef90104ab81fec17010725f8f5c0c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62761733"
---
# <a name="optimizing-the-neworg-table"></a>Optimieren der NewOrg-Tabelle
  Die **NewOrd** in erstellten Tabelle der [Auffüllen einer Tabelle mit vorhandenen hierarchischen Daten](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) Aufgabe enthält alle Angestellteninformationen und stellt die hierarchische Struktur mithilfe einer `hierarchyid`-Datentyp. In dieser Aufgabe werden neue Indizes hinzugefügt, die das Suchen in der `hierarchyid`-Spalte unterstützen.  
  
## <a name="clustered-index"></a>Gruppierter Index  
 Die `hierarchyid` Spalte (**OrgNode**) ist der Primärschlüssel für die **NewOrg** Tabelle. Als die Tabelle erstellt wurde, enthielt sie den gruppierten Index **PK_NewOrg_OrgNode** , der die Eindeutigkeit der **OrgNode** -Spalte erzwingen sollte. Dieser gruppierte Index unterstützt auch eine Tiefensuche in der Tabelle.  
  
## <a name="nonclustered-index"></a>Nicht gruppierter Index  
 Dieser Schritt erstellt zwei nicht gruppierte Indizes, um typische Suchoperationen zu unterstützen.  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a>So indizieren Sie die Tabelle 'NewOrg' für effiziente Suchoperationen  
  
1.  Verwenden Sie zur Unterstützung von Abfragen der gleichen Ebene in der Hierarchie die [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) -Methode, um eine berechnete Spalte zu erstellen, welche die Ebene in der Hierarchie enthält. Erstellen Sie dann für diese und die `Hierarchyid`-Spalte einen zusammengesetzten Index. Führen Sie den folgenden Code aus, um die berechnete Spalte und den Breitensuchindex zu erstellen:  
  
    ```  
    ALTER TABLE NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  Erstellen Sie für die Spalte **EmployeeID** einen eindeutigen Index. Dies ist der übliche Singleton-Suchvorgang nach einem einzelnen Mitarbeiter entsprechend der **EmployeeID** -Nummer. Führen Sie den folgenden Code aus, um für **EmployeeID**einen Index zu erstellen:  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON NewOrg(EmployeeID) ;  
    GO  
    ```  
  
3.  Fügen Sie folgenden Code aus, um die Daten der Tabelle in der Reihenfolge jedes der drei Indizes abzurufen.  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM NewOrg   
    ORDER BY OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY H_Level, OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  Vergleichen Sie die Resultsets, um zu sehen, wie die Reihenfolge in jedem Indextyp gespeichert wird. Im Folgenden werden nur die ersten vier Zeilen jeder Ausgabe gezeigt.  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     Tiefensuchindex: Mitarbeiterdatensätze sind angrenzend an ihren Vorgesetzten gespeichert.  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     **EmployeeID**-index: Zeilen werden gespeichert, **EmployeeID** Sequenz.  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
> [!NOTE]  
>  Diagramme, die den Unterschied zwischen einem Tiefensuchindex und einem Breitensuchindex zeigen, finden Sie unter [Hierarchische Daten &#40;SQL Server&#41;](../hierarchical-data-sql-server.md).  
  
#### <a name="to-drop-the-unnecessary-columns"></a>So löschen Sie die unnötigen Spalten  
  
1.  Die Spalte **ManagerID** stellt die Mitarbeiter-/Managerbeziehung dar, die jetzt von der Spalte **OrgNode** dargestellt wird. Wenn andere Anwendungen die Spalte **ManagerID** nicht benötigen, könnten Sie diese Spalte löschen, indem Sie die folgende Anweisung verwenden:  
  
    ```  
    ALTER TABLE NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  Die Spalte **EmployeeID** ist ebenfalls überflüssig. Jeder Mitarbeiter wird bereits durch die Spalte **OrgNode** eindeutig identifiziert. Wenn andere Anwendungen die Spalte **EmployeeID** nicht benötigen, könnten Sie den Index und dann die Spalte löschen, indem Sie folgenden Code verwenden:  
  
    ```  
    DROP INDEX EmpIDs_unq ON NewOrg ;  
    ALTER TABLE NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a>So ersetzen Sie die ursprüngliche durch die neue Tabelle  
  
1.  Wenn die ursprüngliche Tabelle irgendwelche zusätzlichen Indizes oder Einschränkungen enthält, dann fügen Sie diese der Tabelle **NewOrg** hinzu.  
  
2.  So ersetzen Sie die alte **EmployeeDemo** -Tabelle durch die neue Tabelle. Führen Sie folgenden Code aus, um die alte Tabelle zu löschen und dann die neue Tabelle mit dem Namen der alten Tabelle zu benennen:  
  
    ```  
    DROP TABLE EmployeeDemo ;  
    GO  
    sp_rename 'NewOrg', EmployeeDemo ;  
    GO  
    ```  
  
3.  Führen Sie den folgenden Code aus, um die neue Tabelle zu untersuchen:  
  
    ```  
    SELECT * FROM EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Zusammenfassung: Konvertieren einer Tabelle in eine hierarchische Struktur](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
