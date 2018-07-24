---
title: ISJSON (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: douglasl
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ISJSON
- ISJSON_TSQL
helpviewer_keywords:
- ISJSON function
- JSON, validating
ms.assetid: c836f3d3-3e17-44ae-92bf-f341918896c3
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.openlocfilehash: b9abfcd7fe78420f1a67b96fdedfd50e8a6f058a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38055138"
---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Testet, ob eine Zeichenfolge gültiges JSON enthält.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
ISJSON ( expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Die zu testende Zeichenfolge.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt 1 zurück, wenn die Zeichenfolge gültiges JSON enthält. Andernfalls wird 0 zurückgegeben. Gibt NULL zurück, wenn der *Ausdruck* NULL ist.  
  
 Gibt keine Fehler zurück.  
  
## <a name="remarks"></a>Remarks  
 **ISJSON** überprüft nicht die Eindeutigkeit der Schlüssel auf derselben Ebene.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="example-1"></a>Beispiel 1  
Im folgenden Beispiel wird ein Anweisungsblock bedingt ausgeführt, wenn der Parameterwert `@param` gültiges JSON enthält.  
  
```sql  
DECLARE @param <data type>
SET @param = <value>

IF (ISJSON(@param) > 0)  
BEGIN  
     -- Do something with the valid JSON value of @param.  
END
 
```  
  
### <a name="example-2"></a>Beispiel 2  
Im folgenden Beispiel werden die Spalten zurückgegeben, falls die Spalte `json_col` ein gültiges JSON enthält.  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [JSON-Daten &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
