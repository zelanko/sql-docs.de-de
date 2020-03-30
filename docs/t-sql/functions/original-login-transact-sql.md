---
title: ORIGINAL_LOGIN (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ORIGINAL_LOGIN_TSQL
- ORIGINAL_LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], context switches
- context switching [SQL Server], login names
- original login names [SQL Server]
- ORIGINAL_LOGIN function
- names [SQL Server], logins
ms.assetid: ddfb0991-cde3-4b97-a5b7-ee450133f160
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ff9f53c6dd3e0029f2627545c7654ded3219abbe
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67914535"
---
# <a name="original_login-transact-sql"></a>ORIGINAL_LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt den Anmeldenamen zurück, der eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt hat. Mit dieser Funktion können Sie die Identität des ursprünglichen Anmeldenamens in Sitzungen zurückgeben, in denen zahlreiche explizite oder implizite Kontextwechsel vorkommen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ORIGINAL_LOGIN( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **sysname**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion kann sich bei der Überwachung der Identität des ursprünglichen Verbindungskontexts als nützlich erweisen. Während Funktionen wie [SESSION_USER](../../t-sql/functions/session-user-transact-sql.md) und [CURRENT_USER](../../t-sql/functions/current-user-transact-sql.md) den aktuellen Ausführungskontext zurückgeben, gibt ORIGINAL_LOGIN die Identität des Anmeldenamens zurück, mit dem die erste Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der Sitzung hergestellt wurde.  
 
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wechselt der Ausführungskontext der aktuellen Sitzung vom Aufrufer der Anweisungen zu `login1`. Die Funktionen `SUSER_SNAME` und `ORIGINAL_LOGIN` werden verwendet, um den aktuellen Sitzungsbenutzer (der Benutzer, zu dem der Kontext gewechselt hat) und das ursprüngliche Anmeldekonto zurückzugeben. 
 
  >[!NOTE]
  > Obwohl die Funktion ORIGINAL_LOGIN in Azure SQL-Datenbank unterstützt wird, schlägt das folgende Skript fehl, da *EXECUTE AS LOGIN* in Azure SQL-Datenbank nicht unterstützt wird. 
  
```  
USE AdventureWorks2012;  
GO  
--Create a temporary login and user.  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE USER user1 FOR LOGIN login1;  
GO  
--Execute a context switch to the temporary login account.  
DECLARE @original_login sysname;  
DECLARE @current_context sysname;  
EXECUTE AS LOGIN = 'login1';  
SET @original_login = ORIGINAL_LOGIN();  
SET @current_context = SUSER_SNAME();  
SELECT 'The current executing context is: '+ @current_context;  
SELECT 'The original login in this session was: '+ @original_login  
GO  
-- Return to the original execution context  
-- and remove the temporary principal.  
REVERT;  
GO  
DROP LOGIN login1;  
DROP USER user1;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-transact-sql.md)   
 [REVERT &#40;Transact-SQL&#41;](../../t-sql/statements/revert-transact-sql.md)  
  
  
