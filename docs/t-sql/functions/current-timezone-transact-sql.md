---
title: CURRENT_TIMEZONE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/10/2019
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
ms.openlocfilehash: e659ae78b81cb6888e749bd40546efe16b4c542d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "72261327"
---
# <a name="current_timezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt den Namen der von einem Server oder einer Instanz verwendeten Zeitzone zurück. Bei einer verwalteten Azure SQL-Datenbank-Instanz basiert der Rückgabewert auf der Zeitzone der Instanz selbst, die während der Erstellung der Instanz zugewiesen wurde, und nicht auf der Zeitzone des zugrunde liegenden Betriebssystems.
  
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

[Zeitzone für die verwaltete SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-timezone)
