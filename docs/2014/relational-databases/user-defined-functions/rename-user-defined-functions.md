---
title: Umbenennen von benutzerdefinierten Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3419faca26d9d252610c07cb994ab5faa738f937
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52399183"
---
# <a name="rename-user-defined-functions"></a>Umbenennen von benutzerdefinierten Funktionen
  Sie können benutzerdefinierte Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]umbenennen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So benennen Sie benutzerdefinierte Funktionen um mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Funktionsnamen müssen den Regeln für [Bezeichner](../databases/database-identifiers.md)entsprechen.  
  
-   Beim Umbenennen einer benutzerdefinierten Funktion wird der Name des entsprechenden Objektnamens in der Definitionsspalte der **sys.sql_modules** -Katalogsicht nicht geändert. Daher empfiehlt es sich, diesen Objekttyp nicht umzubenennen. Löschen Sie die gespeicherte Prozedur stattdessen, und erstellen Sie sie unter dem neuen Namen neu.  
  
-   Das Ändern des Namens oder der Definition einer benutzerdefinierten Funktion kann dazu führen, dass abhängige Objekte einen Fehler erzeugen, wenn die Objekte nicht so aktualisiert wurden, dass sie die Änderungen an der Funktion widerspiegeln.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Löschen der Funktion ist entweder die ALTER-Berechtigungen für das Schema, zu dem die Funktion gehört, oder die CONTROL-Berechtigung für die Funktion erforderlich. Zum Neuerstellen der Funktion ist die CREATE FUNCTION-Berechtigung in der Datenbank und die ALTER-Berechtigung für das Schema erforderlich, in dem die Funktion erstellt wird.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-rename-user-defined-functions"></a>So benennen Sie benutzerdefinierte Funktionen um  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen neben der Datenbank, in der die Tabelle enthalten ist, die Sie umbenennen möchten.  
  
2.  Klicken Sie neben dem Ordner **Programmierbarkeit** auf das Pluszeichen.  
  
3.  Klicken Sie neben dem Ordner, der die Funktion enthält, die Sie umbenennen möchten, auf das Pluszeichen:  
  
    -   Table-valued Function  
  
    -   Skalarwertfunktion  
  
    -   Aggregatfunktion  
  
4.  Klicken Sie mit der rechten Maustaste auf die Funktion, die Sie umbenennen möchten, und wählen Sie die Option **Umbenennen**.  
  
5.  Geben Sie den neuen Namen der Funktion ein.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So benennen Sie benutzerdefinierte Funktionen um**  
  
 Diese Aufgabe kann nicht mit Transact-SQL-Anweisungen ausgeführt werden. Um eine benutzerdefinierte Funktion mit Transact-SQL umzubenennen, müssen Sie zuerst die vorhandene Funktion löschen und dann unter dem neuen Namen neu erstellen. Stellen Sie sicher, dass für den Code und alle Anwendungen, die den alten Namen der Funktion verwendet haben, jetzt der neue Name verwendet wird.  
  
 Weitere Informationen finden Sie unter [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) und [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)   
 [Anzeigen benutzerdefinierter Funktionen](user-defined-functions.md)  
  
  
