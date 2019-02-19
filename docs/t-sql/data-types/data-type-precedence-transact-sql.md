---
title: Rangfolge der Datentypen (Transact-SQL) | Transact-SQL
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- precedence [SQL Server]
- data types [SQL Server], converting
- data types [SQL Server], precedence
- converting data types [SQL Server], precedence
- precedence [SQL Server], data types
ms.assetid: f4c804ab-ed3f-43b1-a024-c9ac6944b66b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e29b874a84001dcd3d25a46bb07f48dd287ab547
ms.sourcegitcommit: ca9b5cb6bccfdba4cdbe1697adf5c673b4713d6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "56407560"
---
# <a name="data-type-precedence-transact-sql"></a>Rangfolge der Datentypen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Wenn durch einen Operator Ausdrücke verschiedener Datentypen kombiniert werden, wird der Datentyp mit der niedrigeren Rangfolge in den Datentyp mit der höheren Rangfolge konvertiert. Wenn es sich bei der Konvertierung nicht um eine unterstützte implizite Konvertierung handelt, gibt das System einen Fehler zurück. Wenn ein Operator Operandenausdrücke vom gleichen Datentyp kombiniert, hat das Ergebnis der Operation diesen Datentyp.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet die folgende Rangfolge für Datentypen:
  
1.  benutzerdefinierte Datentypen (höchster)  
1.  **sql_variant**  
1.  **xml**  
1.  **datetimeoffset**  
1.  **datetime2**  
1.  **datetime**  
1.  **smalldatetime**  
1.  **Datum**  
1. **Uhrzeit**  
1. **float**  
1. **real**  
1. **decimal**  
1. **money**  
1. **smallmoney**  
1. **bigint**  
1. **int**  
1. **smallint**  
1. **tinyint**  
1. **bit**  
1. **ntext**  
1. **text**  
1. **image**  
1. **timestamp**  
1. **uniqueidentifier**  
1. **nvarchar** (einschließlich **nvarchar(max)**)  
1. **nchar**  
1. **varchar** (einschließlich **varchar(max)**)  
1. **char**  
1. **varbinary** (einschließlich **varbinary(max)**)  
1. **binary** (niedrigster)  
  
## <a name="see-also"></a>Siehe auch
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  