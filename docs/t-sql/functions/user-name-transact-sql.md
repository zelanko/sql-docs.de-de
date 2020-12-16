---
description: USER_NAME (Transact-SQL)
title: USER_NAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- USER_NAME
- USER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- IDs [SQL Server], databases
- USER_NAME function
- users [SQL Server], database username
- names [SQL Server], database users
- identification numbers [SQL Server], databases
- database usernames [SQL Server]
ms.assetid: ab32d644-4228-449a-9ef0-5a975c305775
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5062097a2500cd3cb5c5321a71265ea3ab3e14ee
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97462371"
---
# <a name="user_name-transact-sql"></a>USER_NAME (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt einen Datenbank-Benutzernamen über eine angegebene ID zurück.  
  
 ![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Artikellinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
USER_NAME ( [ id ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *id*  
 Die ID, die einem Datenbankbenutzer zugeordnet ist. *id* ist vom Datentyp **int**. Die Klammern sind erforderlich.  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Hinweise  
 Wenn *id* nicht angegeben ist, wird der aktuelle Benutzer im aktuellen Kontext vermutet. Wenn der Parameter das Wort NULL enthalten ist, wird NULL zurückgegeben. Wenn USER_NAME aufgerufen wird, ohne nach einer EXECUTE AS-Anweisung eine *d* anzugeben, gibt USER_NAME den Namen des Benutzers zurück, dessen Identität angenommen wurde. Falls ein Windows-Prinzipal über eine Mitgliedschaft in einer Gruppe auf die Datenbank zugreift, gibt USER_NAME den Namen des Windows-Prinzipals anstelle der Gruppe zurück.  
 
> [!NOTE]
> Obwohl die USER_NAME-Funktion in Azure SQL-Datenbank unterstützt wird, wird die Verwendung von *Ausführen als* mit USER_NAME nicht in Azure SQL-Datenbank unterstützt. 
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-user_name"></a>A. Verwenden von USER_NAME  
 Im folgenden Beispiel wird der Benutzername für die Benutzer-ID `13` zurückgegeben.  
  
```sql  
SELECT USER_NAME(13);  
GO  
```  
  
### <a name="b-using-user_name-without-an-id"></a>B. Verwenden von USER_NAME ohne ID  
 Das folgende Beispiel sucht nach dem Namen des aktuellen Benutzers, ohne eine ID anzugeben.  
  
```sql  
SELECT USER_NAME();  
GO  
```  
  
 Im Folgenden wird das Resultset für einen Benutzer aufgeführt, der Mitglied der festen sysadmin-Serverrolle ist:  
  
 ```
------------------------------  
dbo  
  
(1 row(s) affected)
```  
  
### <a name="c-using-user_name-in-the-where-clause"></a>C. Verwenden von USER_NAME in der WHERE-Klausel  
 Das folgende Beispiel findet in der `sysusers`-Tabelle diejenige Zeile, in der der Name mit dem Ergebnis der `USER_NAME`-Systemfunktion (angewendet auf Benutzer-ID `1`) übereinstimmt.  
  
```sql  
SELECT name FROM sysusers WHERE name = USER_NAME(1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
name  
------------------------------  
dbo  
  
(1 row(s) affected)
```  
  
### <a name="d-calling-user_name-during-impersonation-with-execute-as"></a>D: Aufrufen von USER_NAME während des Identitätswechsels mit EXECUTE AS  
 Das folgende Beispiel zeigt, wie sich `USER_NAME` während des Identitätswechsels verhält.  
  
```sql  
SELECT USER_NAME();  
GO  
EXECUTE AS USER = 'Zelig';  
GO  
SELECT USER_NAME();  
GO  
REVERT;  
GO  
SELECT USER_NAME();  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
DBO  
Zelig  
DBO
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-user_name-without-an-id"></a>E. Verwenden von USER_NAME ohne ID  
 Das folgende Beispiel sucht nach dem Namen des aktuellen Benutzers, ohne eine ID anzugeben.  
  
```sql  
SELECT USER_NAME();  
```  
  
 Nachfolgend finden Sie das Resultset für einen zum aktuellen Zeitpunkt angemeldeten Benutzer.  
  
```  
------------------------------   
User7                              
```  
  
### <a name="f-using-user_name-in-the-where-clause"></a>F. Verwenden von USER_NAME in der WHERE-Klausel  
 Das folgende Beispiel findet in der `sysusers`-Tabelle diejenige Zeile, in der der Name mit dem Ergebnis der `USER_NAME`-Systemfunktion (angewendet auf Benutzer-ID `1`) übereinstimmt.  
  
```sql  
SELECT name FROM sysusers WHERE name = USER_NAME(1);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
name                             
------------------------------   
User7                              
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40;Transact-SQL&#41;](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER &#40;Transact-SQL&#41;](../../t-sql/functions/current-user-transact-sql.md)   
 [SESSION_USER &#40;Transact-SQL&#41;](../../t-sql/functions/session-user-transact-sql.md)   
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [SYSTEM_USER &#40;Transact-SQL&#41;](../../t-sql/functions/system-user-transact-sql.md)  
  
