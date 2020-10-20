---
description: CURRENT_TIMEZONE_ID (Transact-SQL)
title: CURRENT_TIMEZONE_ID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/18/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_TIMEZONE)ID
- CURRENT_TIMEZONE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- current time zone id [SQL Server]
- current timezoneid [SQL Server]
- system time zone id[SQL Server]
- system timezone id[SQL Server]
- functions [SQL Server], time zone id
- functions [SQL Server], timezoneid
- timezoneid [SQL Server], functions
- time zone id [SQL Server], functions
- CURRENT_TIMEZONE_ID function [SQL Server]
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 936b4f0ea8353b71b26808f1911890149057b234
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036857"
---
# <a name="current_timezone_id-transact-sql"></a>CURRENT_TIMEZONE_ID (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

Diese Funktion gibt die ID der von einem Server oder einer Instanz verwendeten Zeitzone zurück. Bei einer verwalteten Instanz von Azure SQL Managed Instance basiert der Rückgabewert auf der Zeitzone der Instanz selbst, die während der Erstellung der Instanz zugewiesen wurde, und nicht auf der Zeitzone des zugrunde liegenden Betriebssystems.
  
> [!NOTE]  
> Bei SQL-Datenbank wird die Zeitzone immer auf UTC festgelegt. Daher gibt `CURRENT_TIMEZONE_ID` die ID der UTC-Zeitzone zurück.
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
CURRENT_TIMEZONE_ID ( )  
```
  
## <a name="arguments"></a>Argumente

Diese Funktion akzeptiert keine Argumente.
  
## <a name="return-type"></a>Rückgabetyp  

**varchar**
  
## <a name="remarks"></a>Bemerkungen  

`CURRENT_TIMEZONE_ID` ist eine nicht deterministische Funktion. Sichten und Ausdrücke, die auf diese Spalte verweisen, können nicht indiziert werden.
  
## <a name="example"></a>Beispiel

Der zurückgegebene Wert spiegelt die tatsächliche Zeitzone und die Spracheinstellungen des Servers oder der Instanz wider.

```sql
SELECT CURRENT_TIMEZONE_ID();  
/* Returned:  
W. Europe Standard Time
*/
```  
  
## <a name="see-also"></a>Weitere Informationen

[SQL Managed Instance: Zeitzone](/azure/sql-database/sql-database-managed-instance-timezone)

[CURRENT_TIMEZONE()](./current-timezone-transact-sql.md)