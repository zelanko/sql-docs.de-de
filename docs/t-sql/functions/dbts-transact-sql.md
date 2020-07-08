---
title: '@@DBTS (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@DBTS_TSQL'
- '@@DBTS'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@DBTS function'
- timestamp data type
ms.assetid: 91842ddd-91c0-4445-a03f-116f6bc991d0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5493589b7a87af2ea856a63e81c3b366eb410d9e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85682946"
---
# <a name="x40x40dbts-transact-sql"></a>&#x40;&#x40;DBTS (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Diese Funkion gibt den aktuellen Wert vom Datentyp **timestamp** für die aktuelle Datenbank zurück. Die aktuelle Datenbank hat auf jeden Fall einen eindeutigen timestamp-Wert.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```
@@DBTS  
```  
  
## <a name="return-types"></a>Rückgabetypen
**varbinary**
  
## <a name="remarks"></a>Bemerkungen  
@@DBTS gibt den zuletzt verwendeten Timestampwert der aktuellen Datenbank zurück. Ein neuer Timestampwert wird generiert, wenn eine Zeile mit einer **timestamp**-Spalte eingefügt oder aktualisiert wird.
  
Die Funktion @@DBTS ist nicht von Änderungen der Transaktionsisolationsstufen betroffen.
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird der aktuelle **timestamp**-Wert aus der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank zurückgegeben.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@DBTS;  
```  
  
## <a name="see-also"></a>Weitere Informationen
[Configuration Functions &#40;Transact-SQL&#41; (Konfigurationsfunktionen (Transact-SQL))](../../t-sql/functions/configuration-functions-transact-sql.md)  
[Cursor Concurrency &#40;ODBC&#41; (Cursorparallelität (ODBC))](../../relational-databases/native-client-odbc-cursors/properties/cursor-concurrency-odbc.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40;Transact-SQL&#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)
  
  
