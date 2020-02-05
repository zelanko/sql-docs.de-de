---
title: SET ARITHIGNORE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET ARITHIGNORE
- SET_ARITHIGNORE_TSQL
- ARITHIGNORE
- ARITHIGNORE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ARITHIGNORE statement
- overflow errors [SQL Server]
- ARITHIGNORE option
- divide-by-zero errors
ms.assetid: 71b2c2a5-c83a-4dfe-8469-237987a6e503
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6d2cfda829d014f85f933aaa476507252ca056e5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "67929111"
---
# <a name="set-arithignore-transact-sql"></a>SET ARITHIGNORE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Steuert die Rückgabe von Fehlermeldungen, die wegen Überlauffehlern oder Fehlern aufgrund einer Division durch Null während einer Abfrage auftreten.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server and Azure SQL Database

SET ARITHIGNORE { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

SET ARITHIGNORE OFF
```

## <a name="remarks"></a>Bemerkungen  
 Die SET ARITHIGNORE-Einstellung steuert lediglich, ob eine Fehlermeldung zurückgegeben wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt unabhängig von dieser Einstellung in einer Berechnung NULL zurück, wenn ein Überlauf- oder Division-durch-0-Fehler auftritt. Mithilfe der SET ARITHABORT-Einstellung kann bestimmt werden, ob die Abfrage beendet wird. Diese Einstellung wirkt sich nicht auf Fehler aus, die im Verlauf von INSERT-, UPDATE- und DELETE-Anweisungen auftreten.  
  
 Auch wenn SET ARITHABORT oder SET ARITHIGNORE auf OFF und SET ANSI_WARNINGS auf ON festgelegt sind, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Fehlermeldung zurück, wenn ein Fehler aufgrund einer Division durch Null oder ein Überlauffehler auftritt.  
  
 Die Einstellung von SET ARITHIGNORE wird zur Ausführungszeit und nicht zur Analysezeit festgelegt.  
  
 Um die aktuelle Einstellung anzuzeigen, führen Sie die folgende Abfrage aus.  
  
```  
DECLARE @ARITHIGNORE VARCHAR(3) = 'OFF';  
IF ( (128 & @@OPTIONS) = 128 ) SET @ARITHIGNORE = 'ON';  
SELECT @ARITHIGNORE AS ARITHIGNORE;  
  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Verwendung beider `SET ARITHIGNORE`-Einstellungen mit beiden Typen von Abfragefehlern veranschaulicht.  
  
```  
SET ARITHABORT OFF;  
SET ANSI_WARNINGS OFF  
GO  
  
PRINT 'Setting ARITHIGNORE ON';  
GO  
-- SET ARITHIGNORE ON and testing.  
SET ARITHIGNORE ON;  
GO  
SELECT 1 / 0 AS DivideByZero;  
GO  
SELECT CAST(256 AS TINYINT) AS Overflow;  
GO  
  
PRINT 'Setting ARITHIGNORE OFF';  
GO  
-- SET ARITHIGNORE OFF and testing.  
SET ARITHIGNORE OFF;  
GO  
SELECT 1 / 0 AS DivideByZero;  
GO  
SELECT CAST(256 AS TINYINT) AS Overflow;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel werden die Fehler aufgrund einer Division durch 0 (null) und Überlauffehler veranschaulicht. Dieses Beispiel gibt keine Fehlermeldung für diese Fehler zurück, da ARITHIGNORE auf OFF festgelegt ist.  
  
```  
-- SET ARITHIGNORE OFF and testing.  
SET ARITHIGNORE OFF;  
SELECT 1 / 0 AS DivideByZero;  
SELECT CAST(256 AS TINYINT) AS Overflow;  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SET-Anweisungen (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ARITHABORT &#40;Transact-SQL&#41;](../../t-sql/statements/set-arithabort-transact-sql.md)  
  
  

