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
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: d1e6123b99308e053a3235d5e9fe8cd22a4daaa8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736438"
---
# <a name="rowcount_big-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Anzahl von Zeilen zurück, auf die sich die zuletzt ausgeführte Anweisung ausgewirkt hat. Diese Funktion wird wie [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md) verwendet, allerdings mit dem Unterschied, dass die Rückgabe von ROWCOUNT_BIG den Datentyp **bigint** aufweist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **bigint**  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn diese Funktion auf eine SELECT-Anweisung folgt, gibt sie die Anzahl von Zeilen zurück, die von der SELECT-Anweisung zurückgegeben wurden.  
  
 Wenn diese Funktion auf eine INSERT-, UPDATE- oder DELETE-Anweisung folgt, gibt sie die Anzahl von Zeilen zurück, auf die sich die Datenänderungsanweisung ausgewirkt hat.  
  
 Wenn diese Funktion auf eine Anweisung folgt, die keine Zeilen zurückgibt, wie z. B. eine IF-Anweisung, gibt sie Null (0) zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [COUNT_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
