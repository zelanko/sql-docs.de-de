---
title: sp_describe_cursor_tables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor_tables_TSQL
- sp_describe_cursor_tables
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor_tables
ms.assetid: 02c0f81a-54ed-4ca4-aa4f-bb7463a9ab9a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 68c8cd21de793dc34c2f601a9918db2224d3df03
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85861360"
---
# <a name="sp_describe_cursor_tables-transact-sql"></a>sp_describe_cursor_tables (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Meldet die Objekte oder Basistabellen, auf die ein Servercursor verweist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_describe_cursor_tables   
     [ @cursor_return = ] output_cursor_variable OUTPUT   
     { [ , [ @cursor_source = ] N'local'  
     , [ @cursor_identity = ] N'local_cursor_name' ]   
   | [ , [ @cursor_source = ] N'global'  
     , [ @cursor_identity = ] N'global_cursor_name' ]   
   | [ , [ @cursor_source = ] N'variable'  
     , [ @cursor_identity = ] N'input_cursor_variable' ]   
     }   
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @cursor_return =] *output_cursor_variable*Ausgabe  
 Der Name einer deklarierten Cursorvariablen zum Empfangen der Cursorausgabe. *output_cursor_variable* ist vom Typ **Cursor**und hat keinen Standardwert und darf zum Zeitpunkt, an dem sp_describe_cursor_tables aufgerufen wird, keinen Cursorn zugeordnet werden. Bei dem zurückgegebenen Cursor handelt es sich um einen scrollfähigen, dynamischen, schreibgeschützten Cursor.  
  
 [ @cursor_source =] {N ' local ' | N ' Global ' | N '}  
 Gibt an, ob der Cursor, für den der Bericht erstellt wird, mithilfe des Namens eines lokalen Cursors, eines globalen Cursors oder einer Cursorvariablen angegeben wird. Der Parameter ist vom Datentyp **nvarchar (30)**.  
  
 [ @cursor_identity =] N '*local_cursor_name*'  
 Name eines mit einer DECLARE CURSOR-Anweisung erstellten Cursors, der entweder das LOCAL-Schlüsselwort aufweist oder standardmäßig auf LOCAL festgelegt ist. *local_cursor_name* ist vom Datentyp **nvarchar (128)**.  
  
 [ @cursor_identity =] N '*global_cursor_name*'  
 Name eines mit einer DECLARE CURSOR-Anweisung erstellten Cursors, der entweder das GLOBAL-Schlüsselwort aufweist oder standardmäßig auf GLOBAL festgelegt ist. *global_cursor_name* kann auch der Name eines API-Server Cursors sein, der von einer ODBC-Anwendung geöffnet wurde, die den Cursor dann durch Aufrufen von SQLSetCursorName benannt hat. *global_cursor_name* ist vom Datentyp **nvarchar (128)**.  
  
 [ @cursor_identity =] N '*input_cursor_variable*'  
 Der Name einer Cursorvariablen, die mit einem geöffneten Cursor verknüpft ist. *input_cursor_variable* ist vom Datentyp **nvarchar (128)**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="cursors-returned"></a>Zurückgegebene Cursor  
 sp_describe_cursor_tables kapselt den Bericht als [!INCLUDE[tsql](../../includes/tsql-md.md)] **Cursor** Ausgabeparameter. Dies ermöglicht, dass [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batches, gespeicherte Prozeduren und Trigger die Ausgabe zeilenweise verwenden können. Dies bedeutet außerdem, dass es nicht möglich ist, die Prozedur direkt über API-Funktionen aufzurufen. Der **Cursor** Ausgabeparameter muss an eine Programm Variable gebunden sein, aber die APIs unterstützen die Bindung von **Cursor** -Parametern oder-Variablen nicht.  
  
 In der folgenden Tabelle wird das Format des Cursors dargestellt, der von sp_describe_cursor_tables zurückgegeben wird.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|table owner|**sysname**|Die Benutzer-ID des Tabellenbesitzers.|  
|Table_name|**sysname**|Name des Objekts oder der Basistabelle. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geben Servercursor immer das vom Benutzer angegebene Objekt und nicht die Basistabellen zurück.|  
|Optimizer_hints|**smallint**|Bitmapmuster, das sich aus einer oder mehreren der folgenden Optionen zusammensetzt:<br /><br /> 1 = Sperre auf Zeilenebene (ROWLOCK)<br /><br /> 4 = Sperre auf Seitenebene (PAGELOCK)<br /><br /> 8 = Tabellensperre (TABLOCK)<br /><br /> 16 = Exklusive Tabellensperre (TABLOCKX)<br /><br /> 32 = Updatesperre (UPDLOCK)<br /><br /> 64 = Keine Sperre (NOLOCK)<br /><br /> 128 = Schnelle erste Zeilenoption (FASTFIRST)<br /><br /> 4096 = Wiederholbarer Lesevorgang bei Verwendung mit DECLARE CURSOR (HOLDLOCK)<br /><br /> Bei Angabe mehrerer Optionen wird vom System die restriktivste Option verwendet. sp_describe_cursor_tables zeigt jedoch die Flags an, die in der Abfrage angegeben sind.|  
|lock_type|**smallint**|Explizit oder implizit für die diesem Cursor zugrunde liegenden Basistabellen angeforderter Scrollsperrentyp. Der Wert kann in folgenden Formen vorliegen:<br /><br /> 0 = Keine<br /><br /> 1 = Freigegeben<br /><br /> 3 = Update|  
|server_name|**sysname, Werte zulässt**|Der Name des Verbindungsservers, auf dem sich die Tabelle befindet. NULL, wenn OPENQUERY oder OPENROWSET verwendet wird.|  
|Objectid|**int**|Objekt-ID der Tabelle. 0, wenn OPENQUERY oder OPENROWSET verwendet wird.|  
|dbid|**int**|ID der Datenbank, in der sich die Tabelle befindet. 0, wenn OPENQUERY oder OPENROWSET verwendet wird.|  
|dbname|**vom Datentyp sysname**, **Werte zulässt**|Name der Datenbank, in der sich die Tabelle befindet. NULL, wenn OPENQUERY oder OPENROWSET verwendet wird.|  
  
## <a name="remarks"></a>Hinweise  
 sp_describe_cursor_tables beschreibt die Basistabellen, auf die ein Servercursor verweist. Mit sp_describe_cursor_columns zeigen Sie eine Beschreibung der Attribute des vom Cursor zurückgegebenen Resultsets an. Verwenden Sie sp_describe_cursor für eine Beschreibung der globalen Cursormerkmale, wie z. B. die Scrolloptionen und die Aktualisierbarkeit. Wenn Sie einen Bericht der in der Verbindung sichtbaren [!INCLUDE[tsql](../../includes/tsql-md.md)]-Servercursor benötigen, verwenden Sie sp_cursor_list.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird ein globaler Cursor geöffnet und mithilfe von `sp_describe_cursor_tables` gemeldet, auf welche Tabellen dieser Cursor verweist.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person  
WHERE LastName LIKE 'S%';  
  
OPEN abc;  
GO  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor_tables.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor_tables into the cursor variable.  
EXEC master.dbo.sp_describe_cursor_tables  
      @cursor_return = @Report OUTPUT,  
      @cursor_source = N'global', @cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor_tables output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor_tables.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cursor](../../relational-databases/cursors.md)   
 [CURSOR_STATUS &#40;Transact-SQL-&#41;](../../t-sql/functions/cursor-status-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL-&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [sp_cursor_list &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [sp_describe_cursor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-transact-sql.md)   
 [sp_describe_cursor_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-columns-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
