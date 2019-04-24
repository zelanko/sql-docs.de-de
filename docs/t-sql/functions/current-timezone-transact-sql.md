---
title: CURRENT_TIMEZONE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/09/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_TIMEZONE
- CURRENT_TIMEZONE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- current time zone [SQL Server]
- current timezone [SQL Server]
- system time zone [SQL Server]
- system timezone [SQL Server]
- functions [SQL Server], time zone
- functions [SQL Server], timezone
- timezone [SQL Server], functions
- time zone [SQL Server], functions
- CURRENT_TIMEZONE function [SQL Server]
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: dcdae3ff107ad1e1e3a7bc58fde4248bb5330223
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59367386"
---
# <a name="currenttimezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Diese Funktion gibt den Namen der von einem Server oder einer Instanz verwendeten Zeitzone zurück. Bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`CURRENT_TIMEZONE` wird der Rückgabewert aus dem Betriebssystem des Computers abgeleitet, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Bei einer verwalteten Azure SQL-Datenbank-Instanz basiert der Rückgabewert auf der Zeitzone der Instanz selbst, die während der Instanzenerstellung zugewiesen wurde, und nicht auf der Zeitzone des zugrunde liegenden Betriebssystems.
  
> [!NOTE]  
> Bei einzelnen SQL-Datenbanken und SQL-Pooldatenbanken wird die Zeitzone immer auf UTC festgelegt. Daher gibt `CURRENT_TIMEZONE` den Namen der UTC-Zeitzone zurück.
  
## <a name="syntax"></a>Syntax  
  
```sql
CURRENT_TIMEZONE ( )  
```
  
## <a name="arguments"></a>Argumente

Diese Funktion akzeptiert keine Argumente.
  
## <a name="return-type"></a>Rückgabetyp  

**varchar**
  
## <a name="remarks"></a>Remarks  

`CURRENT_TIMEZONE` ist eine nicht deterministische Funktion. Sichten und Ausdrücke, die auf diese Spalte verweisen, können nicht indiziert werden.
  
## <a name="example"></a>Beispiel

Beachten Sie, dass der zurückgegebene Wert die tatsächliche Zeitzone und die Spracheinstellungen des Servers oder der Instanz widerspiegelt.

```sql
SELECT CURRENT_TIMEZONE();  
/* Returned:  
(UTC+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna 
*/
```  
  
## <a name="see-also"></a>Siehe auch

[Zeitzone für die verwaltete SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-timezone)
