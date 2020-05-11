---
title: SCHEMA_NAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SCHEMA_NAME
- SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SCHEMA_NAME function
- schemas [SQL Server], names
ms.assetid: 20071b77-2b6e-4ce7-a8e3-fa71480baf73
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e74bc65cde6d88b1329a4fea8c4ea650963c8816
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828587"
---
# <a name="schema_name-transact-sql"></a>SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt den einer Schema-ID zugeordneten Schemanamen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
SCHEMA_NAME ( [ schema_id ] )  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|----------|----------------|  
|*schema_id*|Die ID des Schemas. *schema_id* ist vom Datentyp **int**. Ist *schema_id* nicht definiert, gibt SCHEMA_NAME den Namen des Standardschemas des Aufrufers zurück.|  
  
## <a name="return-types"></a>Rückgabetypen  
 **sysname**  
  
 Gibt NULL zurück, wenn *schema_id* keine gültige ID ist.  
  
## <a name="remarks"></a>Bemerkungen  
 SCHEMA_NAME gibt Namen von Systemschemas und benutzerdefinierten Schemas zurück. SCHEMA_NAME kann in einer SELECT-Liste, in einer WHERE-Klausel und überall dort aufgerufen werden, wo ein Ausdruck zulässig ist.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-name-of-the-default-schema-of-the-caller"></a>A. Zurückgeben des Namens des Standardschemas des Aufrufers  
  
```  
SELECT SCHEMA_NAME();  
```  
  
### <a name="b-returning-the-name-of-a-schema-by-using-an-id"></a>B. Zurückgeben des Namens eines Schemas mithilfe einer ID  
  
```  
SELECT SCHEMA_NAME(1);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SCHEMA_ID &#40;Transact-SQL&#41;](../../t-sql/functions/schema-id-transact-sql.md)   
 [sys.schemas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

