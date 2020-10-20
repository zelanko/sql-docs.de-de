---
description: CURRENT_TIMEZONE (Transact-SQL)
title: CURRENT_TIMEZONE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/28/2020
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
ms.openlocfilehash: 647ba1436995028580b6c1ed7ed40a8cd7849ab5
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036843"
---
# <a name="current_timezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

Diese Funktion gibt den Namen der von einem Server oder einer Instanz verwendeten Zeitzone zurück. Bei SQL Managed Instance basiert der Rückgabewert auf der Zeitzone der Instanz selbst, die während der Erstellung der Instanz zugewiesen wurde, und nicht auf der Zeitzone des zugrunde liegenden Betriebssystems.
  
> [!NOTE]  
> Bei SQL-Datenbank wird die Zeitzone immer auf UTC festgelegt, und `CURRENT_TIMEZONE` gibt den Namen der UTC-Zeitzone zurück.
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
CURRENT_TIMEZONE ( )  
```
  
## <a name="arguments"></a>Argumente

Diese Funktion akzeptiert keine Argumente.
  
## <a name="return-type"></a>Rückgabetyp  

**varchar**
  
## <a name="remarks"></a>Bemerkungen  

`CURRENT_TIMEZONE` ist eine nicht deterministische Funktion. Sichten und Ausdrücke, die auf diese Spalte verweisen, können nicht indiziert werden.
  
## <a name="example"></a>Beispiel

Beachten Sie, dass der zurückgegebene Wert die tatsächliche Zeitzone und die Spracheinstellungen des Servers oder der Instanz widerspiegelt.

```sql
SELECT CURRENT_TIMEZONE();  
/* Returned:  
(UTC+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna 
*/
```  
  
## <a name="see-also"></a>Weitere Informationen

[SQL Managed Instance: Zeitzone](/azure/sql-database/sql-database-managed-instance-timezone)

[CURRENT_TIMEZONE_ID()](./current-timezone-id-transact-sql.md)