---
description: DROP SENSITIVITY CLASSIFICATION (Transact-SQL)
title: DROP SENSITIVITY CLASSIFICATION (Transact-SQL) | Microsoft-Dokumentation
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: giladm
author: giladmit
f1_keywords:
- DROP SENSITIVITY CLASSIFICATION
- DROP_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SENSITIVITY CLASSIFICATION statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
monikerRange: " >= sql-server-ver15 || = azuresqldb-current || = sqlallproducts-allversions"
ms.openlocfilehash: 6b09e5e60bd7ac1d02f46d191fccd0e2142f8d75
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96131100"
---
# <a name="drop-sensitivity-classification-transact-sql"></a>DROP SENSITIVITY CLASSIFICATION (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

Diese Anweisung löscht Metadaten zu Vertraulichkeitsklassifizierungen aus einer oder mehreren Datenbankspalten.

## <a name="syntax"></a>Syntax

```syntaxsql
DROP SENSITIVITY CLASSIFICATION FROM
    <object_name> [, ...n ]

<object_name> ::=
{
    [schema_name.]table_name.column_name
}
```  

## <a name="arguments"></a>Argumente  

*object_name* ([schema_name.]table_name.column_name)

Der Name der Datenbankspalte, aus der die Klassifizierung entfernt werden soll. Derzeit wird ausschließlich die Spaltenklassifizierung unterstützt.
    - *schema_name* (optional): Der Name des Schemas, zu dem die klassifizierte Spalte gehört.
    - *table_name* (optional): Der Name der Tabelle, zu der die klassifizierte Spalte gehört.
    - *column_name*: Der Name der Spalte, aus der die Klassifizierung gelöscht werden soll.

## <a name="remarks"></a>Hinweise  

- Mit einer einzelnen DROP SENSITIVITY CLASSIFICATION-Anweisung können mehrere Objektklassifizierungen gelöscht werden.

## <a name="permissions"></a>Berechtigungen  

Erfordert die Berechtigung ALTER ANY SENSITIVITY CLASSIFICATION. Die Berechtigung ALTER ANY SENSITIVITY CLASSIFICATION wird von der Datenbankberechtigung ALTER oder der Serverberechtigung CONTROL SERVER impliziert.


## <a name="examples"></a>Beispiele  


### <a name="a-dropping-classification-from-a-single-column"></a>A. Löschen einer Klassifizierung aus einer einzelnen Spalte

Im folgenden Beispiel wird die Klassifizierung aus der Spalte `dbo.sales.price` entfernt.  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price
```

### <a name="b-dropping-classification-from-multiple-columns"></a>B. Löschen einer Klassifizierung aus mehreren Spalten

Im folgenden Beispiel wird die Klassifizierung aus den Spalten `dbo.sales.price`, `dbo.sales.discount` und `SalesLT.Customer.Phone` entfernt.  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price, dbo.sales.discount, SalesLT.Customer.Phone  
```

## <a name="see-also"></a>Weitere Informationen  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[Azure SQL-Datenbank – Datenermittlung und -klassifizierung](https://aka.ms/sqlip)
