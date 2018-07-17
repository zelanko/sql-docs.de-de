---
title: SCHEMA_ID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SCHEMA_ID
- SCHEMA_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], schemas
- schemas [SQL Server], IDs
- SCHEMA_ID function
- IDs [SQL Server], schemas
- default schema IDs
ms.assetid: c8e34df5-3eea-459f-ae40-050909ce9fda
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 12d21a3532d196461d65b3d405918627606c7c43
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792221"
---
# <a name="schemaid-transact-sql"></a>SCHEMA_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt die Schema-ID zurück, die einem Schemanamen zugeordnet ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
SCHEMA_ID ( [ schema_name ] )   
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|----------|----------------|  
|*schema_name*|Der Name des Schemas. *schema_name* ist ein **sysname**. Falls *schema_name* nicht angegeben wird, gibt SCHEMA_ID die ID des Standardschemas des Aufrufers zurück.|  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
 Es wird NULL zurückgegeben, wenn *schema_name* kein gültiges Schema ist.  
  
## <a name="remarks"></a>Remarks  
 SCHEMA_ID gibt IDs von Systemschemas und benutzerdefinierten Schemas zurück. SCHEMA_ID kann in einer Auswahlliste, in einer WHERE-Klausel und überall dort aufgerufen werden, wo ein Ausdruck zulässig ist.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-default-schema-id-of-a-caller"></a>A. Zurückgeben der Standardschema-ID eines Aufrufers  
  
```  
SELECT SCHEMA_ID();  
```  
  
### <a name="b-returning-the-schema-id-of-a-named-schema"></a>B. Zurückgeben der Schema-ID eines benannten Schemas  
  
```  
SELECT SCHEMA_ID('dbo');  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SCHEMA_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/schema-name-transact-sql.md)   
 [sys.schemas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)  
  
  

