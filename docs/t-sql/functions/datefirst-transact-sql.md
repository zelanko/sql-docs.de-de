---
title: '@@DATEFIRST (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATE_FORMAT_TSQL
- DATE FORMAT
- '@@DATEFIRST_TSQL'
- '@@DATEFIRST'
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], SET DATEFIRST
- first day of week [SQL Server]
- dates [SQL Server], first day of week
- day of week [SQL Server]
- SET DATEFIRST option [SQL Server]
- date and time [SQL Server], DATEFIRST
- DATEFIRST option [SQL Server]
- date and time [SQL Server], @@DATEFIRST
- weekdays [SQL Server]
- '@@DATEFIRST function [SQL Server]'
- functions [SQL Server], date and time
- options [SQL Server], date
ms.assetid: a178868e-49d5-4bd5-a5e2-1283409c8ce6
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0a20ed911424aea248cf5c9fad61075f34d07e1a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795508"
---
# <a name="x40x40datefirst-transact-sql"></a>&#x40;&#x40;DATEFIRST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt den aktuellen Wert von [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md) für eine bestimmte Sitzung zurück.
  
Unter [Datums- und Uhrzeitdatentypen und zugehörige Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md) finden Sie eine Übersicht über alle [!INCLUDE[tsql](../../includes/tsql-md.md)] Datums- und Uhrzeitdatentypen und zugehörige Funktionen.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```
@@DATEFIRST  
```  
  
## <a name="return-type"></a>Rückgabetyp  
**tinyint**
  
## <a name="remarks"></a>Remarks  
SET DATEFIRST *n* gibt den ersten Tag der Woche an (Sonntag, Montag, Dienstag usw.). Der Wert *n* liegt zwischen 1 und 7.

```sql
SET DATEFIRST 3;
GO  
SELECT @@DATEFIRST; -- 3 (Wednesday)
GO
```  

Bei einer US-englischen Umgebung ist der Wert @@DATEFIRST standardmäßig 7 (Sonntag).
  
Diese Spracheinstellung beeinflusst die Interpretierung von Zeichenfolgen, da SQL Server diese Zeichenfolgen in Datumswerte zum Speichern in der Datenbank konvertiert. Diese Einstellung beeinflusst außerdem die Anzeige von Datumswerten in der Datenbank. Diese Einstellung beeinflusst nicht das Speicherformat der Datumsdaten.

In diesem Beispiel wird die Sprache zunächst auf `Italian` festgelegt. Die `SELECT @@DATEFIRST;`-Anweisung gibt `1` zurück. Die nächste Anweisung legt die Sprache auf `us_english` fest. Die letzte Anweisung, `SELECT @@DATEFIRST;`, gibt `7` zurück.
  
```sql
SET LANGUAGE Italian;  
GO  
SELECT @@DATEFIRST;  
GO  
SET LANGUAGE us_english;  
GO  
SELECT @@DATEFIRST;  
```  
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird der erste Tag der Woche auf `5` (Freitag) festgelegt und davon ausgegangen, dass der aktuelle Tag (`Today`) Samstag ist. Die `SELECT`-Anweisung gibt den `DATEFIRST`-Wert und die Zahl des aktuellen Tages der Woche zurück.
  
```sql
SET DATEFIRST 5;  
SELECT @@DATEFIRST AS 'First Day'  
    ,DATEPART(dw, SYSDATETIME()) AS 'Today';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
First Day         Today  
----------------  --------------  
5                 2  
```  
  
## <a name="example"></a>Beispiel
 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT @@DATEFIRST;  
```  
  
## <a name="see-also"></a>Siehe auch
[Configuration Functions &#40;Transact-SQL&#41; (Konfigurationsfunktionen (Transact-SQL))](../../t-sql/functions/configuration-functions-transact-sql.md)
  
  

