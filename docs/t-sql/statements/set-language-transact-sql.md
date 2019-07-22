---
title: SET LANGUAGE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/05/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_LANGUAGE_TSQL
- SET LANGUAGE
dev_langs:
- TSQL
helpviewer_keywords:
- LANGUAGE option
- languages [SQL Server], setting language
- SET LANGUAGE statement
- options [SQL Server], date
- default languages
ms.assetid: 0ec0e5cf-e115-4be9-a0db-e65837d6fa45
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ac79430a87cccb7b67ce81a3cb6ca9b05d0a04db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928933"
---
# <a name="set-language-transact-sql"></a>SET LANGUAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Gibt die Sprachumgebung für die Sitzung an. Die Sitzungssprache bestimmt die **datetime**-Formate sowie Systemmeldungen.  
  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET LANGUAGE { [ N ] 'language' | @language_var }   
```  
  
## <a name="arguments"></a>Argumente  
 [**N**] **'** _language_ **'**  |  **@** _language\_var_  
 Der Name der in [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) gespeicherten Sprache. Dieses Argument kann in Unicode oder in DBCS, das in Unicode konvertiert wurde, dargestellt sein. Um eine Sprache in Unicode anzugeben, verwenden Sie **N'** _language_ **'** . Wenn die Sprache als Variable angegeben wird, muss die Variable vom Typ **sysname** sein.  
  
## <a name="remarks"></a>Remarks  
 Die Einstellung von SET LANGUAGE wird zur Ausführungszeit und nicht zur Analysezeit festgelegt.  
  
 SET LANGUAGE legt implizit die Einstellung von [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) fest.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Standardsprache auf `Italian` festgelegt, der Monatsname angezeigt, zurück zu `us_english` gewechselt und der Monatsname erneut angezeigt.  
  
```  
DECLARE @Today DATETIME;  
SET @Today = '12/5/2007';  
  
SET LANGUAGE Italian;  
SELECT DATENAME(month, @Today) AS 'Month Name';  
  
SET LANGUAGE us_english;  
SELECT DATENAME(month, @Today) AS 'Month Name' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [sp_helplanguage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)   
 [SET-Anweisungen &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
