---
description: += (Additionszuweisung) (Transact-SQL)
title: += (Additionszuweisung) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- +=
- +=_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- += (add equals)
- compound operators, +=
- assignment operators, +=
- augmented operators, +=
ms.assetid: 9ea52519-80d1-473f-b988-0572f0e2c92f
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0edc7b32bb14ba9ccfba424d1265dbbee4a45aa9
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92189275"
---
# <a name="-addition-assignment-transact-sql"></a>+= (Additionszuweisung) (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Addiert zwei Zahlen und legt einen Wert auf das Ergebnis des Vorgangs fest. Beispiel: Wenn eine Variable @x gleich 35 ist, übernimmt @x += 2 den ursprünglichen Wert von @x, addiert 2 und legt @x auf diesen neuen Wert (37) fest.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
expression += expression  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *expression*  
 Bezeichnet jeden gültigen [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines beliebigen Datentyps aus der numerischen Kategorie, mit Ausnahme des **bit**-Datentyps.  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt einen Wert vom Datentyp des Arguments zurück, das in der Rangfolge höher steht. Weitere Informationen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen finden Sie unter [+ &#40;Addition&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/add-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbundoperatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [+= &#40;Zeichenfolgenverkettungszuweisung&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/string-concatenation-equal-transact-sql.md)  
  
  
