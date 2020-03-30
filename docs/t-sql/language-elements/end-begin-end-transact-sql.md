---
title: END (BEGIN...END) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- END
- END_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- END keyword
- BEGIN...END keyword
- END (BEGIN...END) keyword
ms.assetid: 354c4935-1375-4141-8195-61326662f4d2
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e7aff4c7bdc1ec9edb93f8a207bd2166bcb3b084
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68075304"
---
# <a name="end-beginend-transact-sql"></a>END (BEGIN...END) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Schließt eine Reihe von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen ein, die als Gruppe ausgeführt werden. BEGIN...END-Blöcke können geschachtelt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
BEGIN   
     { sql_statement | statement_block }   
END   
```  
  
## <a name="arguments"></a>Argumente  
 { *sql_statement*| *statement_block*}  
 Eine beliebige gültige [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder -Anweisungsgruppierung, die als Anweisungsblock definiert ist. Um einen Anweisungsblock (Batch) zu definieren, verwenden Sie die Schlüsselwörter BEGIN und END aus den Sprachkonstrukten zur Ablaufsteuerung. Obwohl sämtliche [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen in einem BEGIN...END-Block gültig sind, sollten bestimmte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen nicht in demselben Batch (Anweisungsblock) gruppiert werden.  
  
## <a name="result-types"></a>Ergebnistypen  
 **Boolescher Wert**  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird durch `BEGIN` und `END` eine Reihe von [!INCLUDE[DWsql](../../includes/dwsql-md.md)]-Anweisungen definiert, die gemeinsam ausgeführt werden. Wenn der `BEGIN...END`-Block nicht vorhanden wäre, würde das folgende Beispiel in einer Endlosschleife ausgeführt werden.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @Iteration Integer = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams';  
SET @Iteration += 1  
END;  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [BEGIN...END &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [Control-of-Flow Language &#40;Transact-SQL&#41; (Sprachkonstrukte zur Ablaufsteuerung (Transact-SQL))](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ELSE &#40;IF...ELSE&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/else-if-else-transact-sql.md)   
 [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  


