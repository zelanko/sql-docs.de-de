---
title: CHECKSUM_AGG (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CHECKSUM_AGG
- CHECKSUM_AGG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- checksum values
- CHECKSUM_AGG function
- groups [SQL Server], checksum values
ms.assetid: cdede70c-4eb5-4c92-98ab-b07787ab7222
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6fa6d6c5736f57338474c17ac41eee55411c865b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68105023"
---
# <a name="checksum_agg-transact-sql"></a>CHECKSUM_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt die Prüfsumme der Werte in einer Gruppe zurück. `CHECKSUM_AGG` ignoriert NULL-Werte. Die [OVER-Klausel](../../t-sql/queries/select-over-clause-transact-sql.md) kann `CHECKSUM_AGG` folgen.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
CHECKSUM_AGG ( [ ALL | DISTINCT ] expression )  
```  
  
## <a name="arguments"></a>Argumente  
**ALL**  
Wendet die Aggregatfunktion auf alle Werte an. ALL ist das Standardargument.
  
DISTINCT  
Gibt an, dass `CHECKSUM_AGG` die Prüfsumme von eindeutigen Werten zurückgeben soll.
  
*expression*  
Ein [Integerausdruck](../../t-sql/language-elements/expressions-transact-sql.md). `CHECKSUM_AGG` lässt das Verwenden von Aggregatfunktionen und Unterabfragen nicht zu.
  
## <a name="return-types"></a>Rückgabetypen
Gibt die Prüfsumme aller *Ausdruckswerte* als **int** zurück.
  
## <a name="remarks"></a>Bemerkungen  
`CHECKSUM_AGG` kann Änderungen in einer Tabelle erkennen.
  
Das `CHECKSUM_AGG`-Ergebnis hängt nicht von der Reihenfolge der Zeilen in der Tabelle ab. Zudem lassen `CHECKSUM_AGG`-Funktionen das Verwenden des Schlüsselworts `DISTINCT` und der Klausel `GROUP BY` zu.
  
Wenn der Listenwert eines Ausdrucks geändert wird, ist es wahrscheinlich, dass sich auch die Werteliste der Listenprüfsumme verändert. Es besteht jedoch auch die Möglichkeit, dass sich die berechnete Prüfsumme nicht ändert.
  
`CHECKSUM_AGG` verfügt über Funktionen, die denen von Aggregatfunktionen ähneln. Weitere Informationen finden Sie unter [Aggregatfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/aggregate-functions-transact-sql.md).
  
## <a name="examples"></a>Beispiele  
In den folgenden Beispielen wird `CHECKSUM_AGG` verwendet, um Änderungen in der `Quantity`-Spalte der `ProductInventory`-Tabelle in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank zu erkennen.
  
```sql
--Get the checksum value before the column value is changed.  

SELECT CHECKSUM_AGG(CAST(Quantity AS int))  
FROM Production.ProductInventory;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
------------------------  
262  
```  
  
```sql
UPDATE Production.ProductInventory   
SET Quantity=125  
WHERE Quantity=100;  
GO  

--Get the checksum of the modified column.  
SELECT CHECKSUM_AGG(CAST(Quantity AS int))  
FROM Production.ProductInventory;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
------------------------  
287  
```  
  
## <a name="see-also"></a>Siehe auch
[CHECKSUM &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-transact-sql.md)  
[HASHBYTES &#40;Transact-SQL&#41;](../../t-sql/functions/hashbytes-transact-sql.md)  
[BINARY_CHECKSUM  &#40;Transact-SQL&#41;](../../t-sql/functions/binary-checksum-transact-sql.md)
[OVER-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
