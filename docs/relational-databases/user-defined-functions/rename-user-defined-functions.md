---
title: Umbenennen von benutzerdefinierten Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c80d1d948f24c212c547c9367f05802c8570fe01
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768311"
---
# <a name="rename-user-defined-functions"></a>Umbenennen von benutzerdefinierten Funktionen
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Sie können benutzerdefinierte Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]umbenennen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So benennen Sie benutzerdefinierte Funktionen um mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Funktionsnamen müssen den Regeln für [Bezeichner](../../relational-databases/databases/database-identifiers.md)entsprechen.  
  
-   Beim Umbenennen einer benutzerdefinierten Funktion wird der Name des entsprechenden Objektnamens in der Definitionsspalte der **sys.sql_modules** -Katalogsicht nicht geändert. Daher empfiehlt es sich, diesen Objekttyp nicht umzubenennen. Löschen Sie die gespeicherte Prozedur stattdessen, und erstellen Sie sie unter dem neuen Namen neu.  
  
-   Das Ändern des Namens oder der Definition einer benutzerdefinierten Funktion kann dazu führen, dass abhängige Objekte einen Fehler erzeugen, wenn die Objekte nicht so aktualisiert wurden, dass sie die Änderungen an der Funktion widerspiegeln.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Zum Löschen der Funktion ist entweder die ALTER-Berechtigungen für das Schema, zu dem die Funktion gehört, oder die CONTROL-Berechtigung für die Funktion erforderlich. Zum Neuerstellen der Funktion ist die CREATE FUNCTION-Berechtigung in der Datenbank und die ALTER-Berechtigung für das Schema erforderlich, in dem die Funktion erstellt wird.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-rename-user-defined-functions"></a>So benennen Sie benutzerdefinierte Funktionen um  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen neben der Datenbank, in der die Tabelle enthalten ist, die Sie umbenennen möchten.  
  
2.  Klicken Sie neben dem Ordner **Programmierbarkeit** auf das Pluszeichen.  
  
3.  Klicken Sie neben dem Ordner, der die Funktion enthält, die Sie umbenennen möchten, auf das Pluszeichen:  
  
    -   Table-valued Function  
  
    -   Skalarwertfunktion  
  
    -   Aggregatfunktion  
  
4.  Klicken Sie mit der rechten Maustaste auf die Funktion, die Sie umbenennen möchten, und wählen Sie die Option **Umbenennen**.  
  
5.  Geben Sie den neuen Namen der Funktion ein.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So benennen Sie benutzerdefinierte Funktionen um**  
  
 Diese Aufgabe kann nicht mit Transact-SQL-Anweisungen ausgeführt werden. Um eine benutzerdefinierte Funktion mit Transact-SQL umzubenennen, müssen Sie zuerst die vorhandene Funktion löschen und dann unter dem neuen Namen neu erstellen. Stellen Sie sicher, dass für den Code und alle Anwendungen, die den alten Namen der Funktion verwendet haben, jetzt der neue Name verwendet wird.  
  
 Weitere Informationen finden Sie unter [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md) und [DROP FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-function-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [Anzeigen benutzerdefinierter Funktionen](../../relational-databases/user-defined-functions/view-user-defined-functions.md)  
  
  
