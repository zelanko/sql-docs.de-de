---
description: sys.xml_schema_collections (Transact-SQL)
title: sys.xml_schema_collections (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_collections_TSQL
- sys.xml_schema_collections
- xml_schema_collections
- xml_schema_collections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_collections catalog view
ms.assetid: f3f7f3dc-029f-4942-ab3c-75fa9814e40f
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d54502963e0a6464d4a437a46c83db53667bab5a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88400736"
---
# <a name="sysxml_schema_collections-transact-sql"></a>sys.xml_schema_collections (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt eine Zeile pro XML-Schemaauflistung zurück. Eine XML-Schemaauflistung ist eine benannte Menge von XSD-Definitionen. Die XML-Schemaauflistung selbst ist in einem relationalen Schema enthalten und wird durch einen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Namen mit Schemabereich identifiziert. Die folgenden Tupel sind eindeutig: xml_collection_id, schema_id und name.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|xml_collection_id|**int**|ID der XML-Schemaauflistung. Ist innerhalb der Datenbank eindeutig.|  
|schema_id|**int**|ID des relationalen Schemas, das diese XML-Schemaauflistung enthält.|  
|principal_id|**int**|ID des einzelnen Besitzers, falls dieser nicht mit dem Schemabesitzer identisch ist. Standardmäßig gehören Objekte mit Schemabereich dem Schemabesitzer. Es kann jedoch ein alternativer Besitzer mithilfe der ALTER AUTHORIZATION-Anweisung angegeben werden, um den Besitzer zu ändern.<br /><br /> NULL = Kein alternativer einzelner Besitzer.|  
|name|**sysname**|Name der XML-Schemaauflistung.|  
|create_date|**datetime**|Datum, an dem die XML-Schemaauflistung erstellt wurde.|  
|modify_date|**datetime**|Datum, an dem die XML-Schemaauflistung zuletzt geändert wurde.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-Schemas &#40;XML-Typsystem&#41; Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
