---
title: Untersuchen der aktuellen Struktur der Mitarbeitertabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b88c78a1a7f4244afe220585919a50ed06cd0ad9
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66110140"
---
# <a name="examining-the-current-structure-of-the-employee-table"></a>Untersuchen der aktuellen Struktur der Mitarbeitertabelle
  Die Beispieldatenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] enthält im Schema **HumanResources** die Tabelle **Employee** . Um Änderungen an der ursprünglichen Tabelle zu vermeiden, wird in diesem Schritt eine Kopie der Tabelle **Employee** mit dem Namen **EmployeeDemo**erstellt. Um das Beispiel zu vereinfachen, kopieren Sie nur fünf Spalten aus der ursprünglichen Tabelle. Dann Fragen Sie die **HumanResources.EmployeeDemo** Tabelle überprüfen, wie die Daten in einer Tabelle strukturiert ist die `hierarchyid` -Datentyp.  
  
### <a name="to-copy-the-employee-table"></a>So kopieren Sie die Mitarbeitertabelle  
  
1.  Führen Sie in einem Abfrage-Editorfenster den folgenden Code aus, um die Tabellenstruktur und die Daten der Tabelle **Employee** in eine neue Tabelle namens **EmployeeDemo**zu kopieren.  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a>So untersuchen Sie die Struktur und die Daten der Tabelle EmployeeDemo  
  
-   Die neue Tabelle **EmployeeDemo** stellt eine typische Tabelle einer vorhandenen Datenbank dar, die in eine neue Struktur migriert werden soll. Führen Sie in einem Abfrage-Editorfenster den folgenden Code aus, um zu zeigen, wie die Mitarbeiter-Manager-Beziehungen mithilfe eines Selbstjoins dargestellt werden:  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
     Die Ausgabe umfasst insgesamt 290 Zeilen.  
  
 Beachten Sie, dass die `ORDER BY`-Klausel bewirkt, dass die Mitarbeiter, die einer Managementebene direkt unterstellt sind, jeweils zusammen aufgelistet werden. So werden beispielsweise die sieben Mitarbeiter, die **MgrID** 3 (roberto0) direkt unterstellt sind, nebeneinander aufgeführt. Es ist zwar nicht unmöglich, aber sehr viel schwieriger, alle Mitarbeiter zu gruppieren, die **MgrID** 3 auch indirekt unterstellt sind.  
  
 In der nächsten Aufgabe erstellen Sie eine neue Tabelle mit dem `hierarchyid`-Datentyp und verschieben die Daten in diese neue Tabelle.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Auffüllen einer Tabelle mit vorhandenen hierarchischen Daten](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
