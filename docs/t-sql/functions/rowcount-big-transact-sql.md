---
title: ROWCOUNT_BIG (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ROWCOUNT_BIG
- ROWCOUNT_BIG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ROWCOUNT_BIG function
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 6e18a0eb-bb36-4348-90d9-8b1ecf095064
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f485d550a122ede18b3faea9d1d490a449ab8d54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65942789"
---
# <a name="rowcountbig-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die Anzahl von Zeilen zurück, auf die sich die zuletzt ausgeführte Anweisung ausgewirkt hat. Diese Funktion wird wie [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md) verwendet, allerdings mit dem Unterschied, dass die Rückgabe von ROWCOUNT_BIG den Datentyp **bigint** aufweist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **bigint**  
  
## <a name="remarks"></a>Remarks  
 Wenn diese Funktion auf eine SELECT-Anweisung folgt, gibt sie die Anzahl von Zeilen zurück, die von der SELECT-Anweisung zurückgegeben wurden.  
  
 Wenn diese Funktion auf eine INSERT-, UPDATE- oder DELETE-Anweisung folgt, gibt sie die Anzahl von Zeilen zurück, auf die sich die Datenänderungsanweisung ausgewirkt hat.  
  
 Wenn diese Funktion auf eine Anweisung folgt, die keine Zeilen zurückgibt, wie z. B. eine IF-Anweisung, gibt sie Null (0) zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [COUNT_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
