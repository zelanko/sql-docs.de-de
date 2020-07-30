---
title: ISJSON (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/03/2020
ms.prod: sql
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
ms.reviewer: jroth
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: cdf9f8c9f79ec7bf286eb1d29a9274baf9a1887f
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395365"
---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Testet, ob eine Zeichenfolge gültiges JSON enthält.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
ISJSON ( expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

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
  
  
