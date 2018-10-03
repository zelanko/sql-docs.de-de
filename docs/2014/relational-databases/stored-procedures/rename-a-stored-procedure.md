---
title: Umbenennen einer gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], renaming
- renaming stored procedures
ms.assetid: 5d2e4c68-7e0b-4405-8919-f5b203e46770
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a6cc6f8ca0c5bb6657cd26350267f557edd014be
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092430"
---
# <a name="rename-a-stored-procedure"></a>Umbenennen einer gespeicherten Prozedur
  In diesem Thema wird beschrieben, wie Sie eine gespeicherte Prozedur in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]umbenennen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **Umbenennen einer gespeicherten Prozedur mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Prozedurnamen müssen den Regeln für [Bezeichner](../databases/database-identifiers.md)entsprechen.  
  
-   Beim Umbenennen einer gespeicherten Prozedur wird der Name des entsprechenden Objekts in der Definitionsspalte der **sys.sql_modules** -Katalogsicht nicht geändert. Daher empfiehlt es sich, diesen Objekttyp nicht umzubenennen. Löschen Sie die gespeicherte Prozedur stattdessen, und erstellen Sie sie unter dem neuen Namen neu.  
  
-   Das Ändern des Namens oder der Definition einer Prozedur kann dazu führen, dass abhängige Objekte fehlschlagen, wenn sie nicht entsprechend den Änderungen an der Prozedur aktualisiert werden. Weitere Informationen finden Sie unter [Anzeigen der Abhängigkeiten einer gespeicherten Prozedur](view-the-dependencies-of-a-stored-procedure.md).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 CREATE PROCEDURE  
 Erfordert die CREATE PROCEDURE-Berechtigung für die Datenbank und die ALTER-Berechtigung für das Schema, in dem die Prozedur erstellt wird, oder die Mitgliedschaft in der festen Datenbankrolle **db_ddladmin** .  
  
 ALTER PROCEDURE  
 Erfordert die ALTER-Berechtigung für die Prozedur oder die Mitgliedschaft in der festen Datenbankrolle **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-rename-a-stored-procedure"></a>So benennen Sie eine gespeicherte Prozedur um  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, erweitern Sie die Datenbank, zu der die Prozedur gehört, und erweitern Sie dann **Programmierbarkeit**.  
  
3.  [Anzeigen der Abhängigkeiten einer gespeicherten Prozedur](view-the-dependencies-of-a-stored-procedure.md).  
  
4.  Erweitern Sie **Gespeicherte Prozeduren**, klicken Sie mit der rechten Maustaste auf die umzubenennende Prozedur, und klicken Sie dann auf **Umbenennen**.  
  
5.  Ändern Sie den Namen der Prozedur.  
  
6.  Ändern Sie den Namen der Prozedur in abhängigen Objekten oder Skripts, in denen auf den Namen verwiesen wird.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-rename-a-stored-procedure"></a>So benennen Sie eine gespeicherte Prozedur um  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie eine Prozedur umbenannt wird, indem sie gelöscht und mit einem neuen Namen neu erstellt wird. Im ersten Beispiel wird die gespeicherte Prozedur `'HumanResources.uspGetAllEmployeesTest`erstellt. Im zweiten Beispiel wird die gespeicherte Prozedur in `HumanResources.uspEveryEmployeeTest`umbenannt.  
  
```tsql  
--Create the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspGetAllEmployeesTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
  
--Rename the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspEveryEmployeeTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)   
 [Erstellen einer gespeicherten Prozedur](../stored-procedures/create-a-stored-procedure.md)   
 [Ändern einer gespeicherten Prozedur](../stored-procedures/modify-a-stored-procedure.md)   
 [Löschen einer gespeicherten Prozedur](../stored-procedures/delete-a-stored-procedure.md)   
 [Anzeigen der Definition einer gespeicherten Prozedur](view-the-definition-of-a-stored-procedure.md)   
 [Anzeigen der Abhängigkeiten einer gespeicherten Prozedur](view-the-dependencies-of-a-stored-procedure.md)  
  
  
