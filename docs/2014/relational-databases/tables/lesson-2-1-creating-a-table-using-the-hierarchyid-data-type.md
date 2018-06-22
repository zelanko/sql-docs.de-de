---
title: Erstellen einer Tabelle mit dem hierarchyid-Datentyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ecf8817fb0c153298a53ba1be4c49606c0200a93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048683"
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
  
  