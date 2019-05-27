---
title: Erstellen einer Tabelle mit dem hierarchyid-Datentyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 98ce16a3630032001a1191b09b1b0ade13aacb73
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66110120"
---
# <a name="creating-a-table-using-the-hierarchyid-data-type"></a>Erstellen einer Tabelle mit dem hierarchyid-Datentyp
  Im folgenden Beispiel wird eine Tabelle namens EmployeeOrg erstellt, die Mitarbeiterdaten zusammen mit ihrer Berichtshierarchie aufnimmt. Das Beispiel erstellt die neue Tabelle in der Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ; dies ist jedoch optional. Um das Beispiel einfach zu halten, enthält die Tabelle nur fünf Spalten:  
  
-   OrgNode ist eine `hierarchyid`-Spalte, die die hierarchische Beziehung speichert.  
  
-   OrgLevel ist eine auf der Spalte OrgNode basierende berechnete Spalte, die die Ebene in der Hierarchie speichert. Sie wird für einen Breitensuchindex verwendet.  
  
-   EmployeeID enthält die typische Mitarbeiter-ID, die für Anwendungen wie beispielsweise die Gehaltsdaten verwendet wird. Bei der Entwicklung neuer Anwendungen können diese die Spalte OrgNode verwenden, und die eigene Spalte EmployeeID wird nicht benötigt.  
  
-   EmpName enthält den Namen des Angestellten.  
  
-   Title enthält den Titel des Angestellten.  
  
### <a name="to-create-the-employeeorg-table"></a>So erstellen Sie die Tabelle "EmployeeOrg"  
  
1.  Führen Sie in einem Abfrage-Editorfenster den folgenden Code aus, um die Tabelle `EmployeeOrg` zu erstellen. Wenn Sie die Spalte `OrgNode` als Primärschlüssel mit einem gruppierten Index angeben, wird ein Tiefensuchindex erstellt:  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
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
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
 Die Tabelle ist jetzt bereit, Daten zu speichern. Die nächste Aufgabe besteht darin, die Tabelle mithilfe hierarchischer Methoden aufzufüllen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Auffüllen einer hierarchischen Tabelle mit hierarchischen Methoden](lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
