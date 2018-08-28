---
title: CURRENT_TIMESTAMP (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CURRENT_TIMESTAMP
- CURRENT_TIMESTAMP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- niladic functions
- current date and time [SQL Server]
- time [SQL Server], current
- date and time [SQL Server], CURRENT_TIMESTAMP
- functions [SQL Server], time
- system date and time [SQL Server]
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- dates [SQL Server], system date and time
- CURRENT_TIMESTAMP function [SQL Server]
- time [SQL Server], system
ms.assetid: c724d9cc-7b1f-4c71-bdf5-08bc52b33afc
caps.latest.revision: 48
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f306833bc3940bd75b825c7b5d80a3df0ac7976e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43100112"
---
# <a name="currenttimestamp-transact-sql"></a>CURRENT_TIMESTAMP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt den aktuellen Zeitstempel des Datenbanksystems ohne den Zeitzonenoffset der Datenbank als **datetime**-Wert zurück. `CURRENT_TIMESTAMP` leitet diesen Wert aus dem Betriebssystem des Computers ab, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.
  
> [!NOTE]  
>  `SYSDATETIME` und `SYSUTCDATE` haben, weil sie in Sekundenbruchteilen gemessen werden, eine höhere Genauigkeit als `GETDATE` und `GETUTCDATE`. Die `SYSDATETIMEOFFSET`-Funktion berücksichtigt den Zeitzonenoffset des Systems. Sie können `SYSDATETIME`, `SYSUTCDATE` und `SYSDATETIMEOFFSET` einer Variablen zuweisen, die einen der Datums- und Uhrzeittypen hat.  
  
Diese Funktion ist die ANSI SQL-Entsprechung zu [GETDATE](../../t-sql/functions/getdate-transact-sql.md).
  
Unter [Datums- und Uhrzeitdatentypen und Funktionen ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md) finden Sie eine Übersicht über alle Datums- und Uhrzeitdatentypen und -funktionen für [!INCLUDE[tsql](../../includes/tsql-md.md)].
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
CURRENT_TIMESTAMP  
```  
  
## <a name="arguments"></a>Argumente  
Diese Funktion akzeptiert keine Argumente.
  
## <a name="return-type"></a>Rückgabetyp  
**datetime**
  
## <a name="remarks"></a>Remarks  
[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen können an jeder Stelle auf `CURRENT_TIMESTAMP` verweisen, an der sie auf einen **datetime**-Ausdruck verweisen können.
  
`CURRENT_TIMESTAMP` ist eine nicht deterministische Funktion. Sichten und Ausdrücke, die auf diese Spalte verweisen, können nicht indiziert werden.
  
## <a name="examples"></a>Beispiele  
In diesen Beispielen werden die sechs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemfunktionen, die aktuelle Datums- und Uhrzeitwerte zurückgeben, dazu verwendet, das Datum, die Uhrzeit oder beides zurückzugeben. In den Beispielen werden die Werte der Reihe nach zurückgegeben, sodass sich deren Sekundenbruchteile unterscheiden können. Beachten Sie, dass die tatsächlich zurückgegebenen Werte dem tatsächlichen Zeitpunkt (Tag und Uhrzeit) der Ausführung entsprechen.
  
### <a name="a-get-the-current-system-date-and-time"></a>A. Abrufen des aktuellen Systemdatums und der aktuellen Systemzeit  
  
```sql
SELECT SYSDATETIME()  
    ,SYSDATETIMEOFFSET()  
    ,SYSUTCDATETIME()  
    ,CURRENT_TIMESTAMP  
    ,GETDATE()  
    ,GETUTCDATE();  
/* Returned:  
SYSDATETIME()      2007-04-30 13:10:02.0474381  
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00  
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381  
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047  
GETDATE()          2007-04-30 13:10:02.047  
GETUTCDATE()       2007-04-30 20:10:02.047  
*/
```  
  
### <a name="b-get-the-current-system-date"></a>B. Abrufen des aktuellen Systemdatums  
  
```sql
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
  
/* Returned   
SYSDATETIME()      2007-05-03  
SYSDATETIMEOFFSET()2007-05-03  
SYSUTCDATETIME()   2007-05-04  
CURRENT_TIMESTAMP  2007-05-03  
GETDATE()          2007-05-03  
GETUTCDATE()       2007-05-04  
*/  
```  
  
### <a name="c-get-the-current-system-time"></a>C. Abrufen der aktuellen Systemzeit  
  
```sql
SELECT CONVERT (time, SYSDATETIME())  
    ,CONVERT (time, SYSDATETIMEOFFSET())  
    ,CONVERT (time, SYSUTCDATETIME())  
    ,CONVERT (time, CURRENT_TIMESTAMP)  
    ,CONVERT (time, GETDATE())  
    ,CONVERT (time, GETUTCDATE());  
  
/* Returned  
SYSDATETIME()      13:18:45.3490361  
SYSDATETIMEOFFSET()13:18:45.3490361  
SYSUTCDATETIME()   20:18:45.3490361  
CURRENT_TIMESTAMP  13:18:45.3470000  
GETDATE()          13:18:45.3470000  
GETUTCDATE()       20:18:45.3470000  
*/  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
```sql
SELECT CURRENT_TIMESTAMP;  
```  
  
## <a name="see-also"></a>Siehe auch
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

