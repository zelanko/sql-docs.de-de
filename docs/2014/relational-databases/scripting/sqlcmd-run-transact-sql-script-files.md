---
title: Ausführen von Transact-SQL-Skriptdateien mithilfe von „sqlcmd“
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0a55800ff1d707ce191d373a7348bf744ce5886
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66063665"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a>Ausführen von Transact-SQL-Skriptdateien mithilfe von sqlcmd
  Sie können `sqlcmd` verwenden, um eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skriptdatei auszuführen. Eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skriptdatei ist eine Textdatei, die eine Kombination aus [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen, `sqlcmd`-Befehlen und Skriptvariablen enthalten kann.  
  
 Führen Sie die folgenden Schritte aus, um eine einfache [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei mithilfe des Editors zu erstellen:  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf **Zubehör**, und klicken Sie dann auf **Editor**.  
  
2.  Kopieren Sie den folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code, und fügen Sie ihn im Editor ein:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  Speichern Sie die Datei auf dem Laufwerk C unter dem Namen **myScript.sql** .  
  
### <a name="to-run-the-script-file"></a>So führen Sie die Skriptdatei aus  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Geben Sie im Fenster "Eingabeaufforderung" Folgendes ein: `sqlcmd -S myServer\instanceName -i C:\myScript.sql`  
  
3.  Drücken Sie die EINGABETASTE.  
  
 Eine Liste mit Namen und Adressen von Mitarbeitern aus [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] wird in das Eingabeaufforderungsfenster geschrieben.  
  
### <a name="to-save-this-output-to-a-text-file"></a>So speichern Sie diese Ausgabe in einer Textdatei  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Geben Sie im Fenster "Eingabeaufforderung" Folgendes ein: `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`  
  
3.  Drücken Sie die EINGABETASTE.  
  
 In diesem Fall erfolgt keine Ausgabe im Eingabeaufforderungsfenster. Stattdessen erfolgt die Ausgabe in die Datei EmpAdds.txt. Sie können diese Ausgabe prüfen, indem Sie die Datei EmpAdds.txt öffnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Hilfsprogramms "sqlcmd"](sqlcmd-start-the-utility.md)   
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)  
  
  
