---
description: (Multiplikationszuweisung) (Transact-SQL)
title: '*= (Multiplikationszuweisung) (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '*=_TSQL'
- '*='
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, *=
- assignment operators, *=
- augmented operators, *=
- '*= (multiply equals)'
- '*= (multiplication assignment)'
ms.assetid: 816ff5dc-9a40-4c07-8351-39c194dbc079
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 96b003987e52dbb6bf20f3606833f9d33355e727
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96128222"
---
# <a name="-multiplication-assignment-transact-sql"></a>(Multiplikationszuweisung) (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Multipliziert zwei Zahlen und legt einen Wert auf das Ergebnis des Vorgangs fest. Beispiel: Wenn eine Variable @x gleich 35 ist, dann übernimmt @x *= 2 den ursprünglichen Wert von @x, multipliziert diesen mit 2 und legt @x auf diesen neuen Wert (70) fest.  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
expression *= expression  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
_expression_  
Bezeichnet mit Ausnahme des **bit**-Datentyps einen gültigen [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines Datentyps aus der numerischen Kategorie.  
  
## <a name="result-types"></a>Ergebnistypen  
Gibt einen Wert vom Datentyp des Arguments zurück, das in der Rangfolge höher steht. Weitere Informationen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Hinweise  
Weitere Informationen finden Sie unter [&#42; &#40;Multiplication&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/multiply-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Verbundoperatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
[Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
[Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
