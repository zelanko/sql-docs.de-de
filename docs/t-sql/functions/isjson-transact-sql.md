---
title: ISJSON (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: genemi
ms.technology: t-sql
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
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: 0d3060af2114f62c1c21b25e79abf4714acfbe4b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68109439"
---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Testet, ob eine Zeichenfolge gültiges JSON enthält.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
  
## <a name="remarks"></a>Bemerkungen  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [JSON-Daten &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
