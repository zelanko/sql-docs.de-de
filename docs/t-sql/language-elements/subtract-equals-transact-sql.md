---
title: -= (Subtraktionszuweisung) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- -=
- -=_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, -=
- assignment operators, -=
- augmented operators, -=
- -= (subtract equals)
- -= (subtraction assignment)
ms.assetid: 2a2056b5-1dfa-4ea8-8cfc-6331a2f94da9
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5a1cac3121a5ff1142dc08e84ac3962044f1ce0
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43068310"
---
# <a name="--subtraction-assignment-transact-sql"></a>-= (Subtraktionszuweisung) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Subtrahiert zwei Zahlen und legt einen Wert auf das Ergebnis des Vorgangs fest. Beispiel: Wenn eine Variable @x gleich 35 ist, dann übernimmt @x –= 2 den ursprünglichen Wert von @x, subtrahiert 2 und legt @x auf diesen neuen Wert (33) fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
expression -= expression  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Bezeichnet jeden gültigen [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines beliebigen Datentyps aus der numerischen Kategorie, mit Ausnahme des **bit**-Datentyps.  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt einen Wert vom Datentyp des Arguments zurück, das in der Rangfolge höher steht. Weitere Informationen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Weitere Informationen finden Sie unter [- &#40;Subtraktion&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/subtract-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verbundoperatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
