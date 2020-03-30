---
title: ATN2 (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ATN2
- ATN2_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- arctangent
- tangent
- ATN2 function
ms.assetid: 014b291e-7cd7-4c39-b20d-5db3a9f0505d
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 993020892a992800a8fb8fab2c7801fe7caf9493
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68040196"
---
# <a name="atn2-transact-sql"></a>ATN2 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Gibt den Winkel im Bogenmaß (Radiant) zwischen der positiven X-Achse und dem Strahl vom Ursprung zum Punkt (x, y) zurück, wobei "x" und "y" die Werte der beiden angegebenen float-Ausdrücke sind.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
ATN2 ( float_expression , float_expression )  
```  
  
## <a name="arguments"></a>Argumente  
*float_expression*  
Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) vom Datentyp **float**.
  
## <a name="return-types"></a>Rückgabetypen
**float**
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird `ATN2` für die angegebenen Komponenten `x` und `y` berechnet.
  
```sql
DECLARE @x float = 35.175643, @y float = 129.44;  
SELECT 'The ATN2 of the angle is: ' + CONVERT(varchar, ATN2(@y, @x));  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
The ATN2 of the angle is: 1.30545                         
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[float und real &#40;Transact-SQL&#41;](../../t-sql/data-types/float-and-real-transact-sql.md)  
[Mathematische Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)
  
  

