---
title: TRIM (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- TRIM
- TRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
caps.latest.revision: 4
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 82a4fcce1764cf8bdb07db18366847fbe8e1cd57
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39451144"
---
# <a name="trim-transact-sql"></a>TRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Entfernt das Leerzeichen `char(32)` oder andere am Beginn oder Ende einer Zeichenfolge angegebene Zeichen.  
 
## <a name="syntax"></a>Syntax   
```
TRIM ( [ characters FROM ] string ) 
```
[//]: # "[ BOTH | LEADING | TRAILING ] noch nicht verfügbar."

## <a name="arguments"></a>Argumente   

Buchstaben   
Ein Literal, eine Variable oder ein Funktionsaufruf eines beliebigen Zeichentyps, der sich nicht auf eine Branchenanwendung bezieht (`nvarchar`, `varchar`, `nchar` oder `char`), mit Zeichen, die entfernt werden sollten. Die Typen `nvarchar(max)` und `varchar(max)` sind nicht zulässig.

Zeichenfolge   
Ein Ausdruck eines beliebigen Zeichentyps (`nvarchar`, `varchar`, `nchar` oder `char`), aus dem Zeichen entfernt werden sollten.

## <a name="return-types"></a>Rückgabetypen   
Gibt einen Zeichenausdruck mit einem Zeichenargumenttyp zurück, aus dem das Leerzeichen `char(32)` oder andere angegebene Zeichenfolgen auf beiden Seiten entfernt werden sollen. Gibt `NULL` zurück, wenn die Eingabezeichenfolge `NULL` ist.

## <a name="remarks"></a>Remarks   
Standardmäßig entfernen `TRIM`-Funktionen das Leerzeichen `char(32)` auf beiden Seiten. Dieser entspricht `LTRIM(RTRIM(@string))`. Das Verhalten der `TRIM `-Funktion mit angegebenen Zeichen ist identisch mit dem Verhalten der `REPLACE`-Funktion, in dem Zeichen am Beginn oder Ende durch leere Zeichenfolgen ersetzt werden.


## <a name="examples"></a>Beispiele
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Entfernt die Leerzeichen auf beiden Seiten der Zeichenfolge.   
Das folgende Beispiel entfernt Leerzeichen vor und nach dem Wort `test`.   
```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>B.  Entfernt angegebene Zeichen von beiden Seiten der Zeichenfolge   
Das folgende Beispiel entfernt einen nachgestellten Punkt oder nachgestellte Leerzeichen.
```sql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>Weitere Informationen finden Sie unter
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen (Transact-SQL))](../../t-sql/functions/string-functions-transact-sql.md)   
