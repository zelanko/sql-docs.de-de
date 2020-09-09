---
description: sys.xml_schema_namespaces (Transact-SQL)
title: sys.xml_schema_namespaces (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_namespaces_TSQL
- sys.xml_schema_namespaces
- xml_schema_namespaces
- xml_schema_namespaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_namespaces catalog view
ms.assetid: 3ed42dd6-929a-41de-80e8-d3a0a488bc7a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8709142f4ff0e1db417cb67fdb5ea516400ead82
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545366"
---
# <a name="sysxml_schema_namespaces-transact-sql"></a>sys.xml_schema_namespaces (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile pro XSD-definierten XML-Namespace zurück. Die folgenden Tupel sind eindeutig: " **collection_id**", " **namespace_id**" und " **collection_id**" und " **Name**".  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**xml_collection_id**|**int**|ID der XML-Schemaauflistung, die diesen Namespace enthält.|  
|**name**|**nvarchar(4000)**|Name des XML-Namespaces. Der leere **Name** gibt keinen Ziel Namespace an.|  
|**xml_namespace_id**|**int**|1-basierte Ordnungszahl, die den XML-Namespace in der Datenbank eindeutig identifiziert.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-Schemas &#40;XML-Typsystem&#41; Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
