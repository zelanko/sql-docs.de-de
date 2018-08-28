---
title: CEILING (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CEILING_TSQL
- CEILING
dev_langs:
- TSQL
helpviewer_keywords:
- smallest integer great than or equal to expression
- integers [SQL Server]
- CEILING function [Transact-SQL]
ms.assetid: e736b43a-9457-4781-95a4-4bcf9d4fc46a
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9457f0b8fe7895871cd1ea8b8896eab763792a39
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43087627"
---
# <a name="ceiling-transact-sql"></a>CEILING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt die kleinste ganze Zahl zurück, die größer oder gleich dem angegebenen numerischen Ausdruck ist.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
CEILING ( numeric_expression )  
```  
  
## <a name="arguments"></a>Argumente  
*numeric_expression*  
Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) der genauen numerischen oder ungefähren numerischen Datentypkategorie. Für diese Funktion ist der Datentyp **bit** ungültig.
  
## <a name="return-types"></a>Rückgabetypen
Rückgabewerte weisen den gleichen Typ wie *numeric_expression* auf.
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel werden positive und negative numerische Eingaben sowie Eingaben mit Nullwerten für die CEILING-Funktion dargestellt.
  
```sql
SELECT CEILING($123.45), CEILING($-123.45), CEILING($0.0);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
--------- --------- -------------------------   
124.00    -123.00    0.00                       
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Siehe auch
[Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  
