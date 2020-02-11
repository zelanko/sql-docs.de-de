---
title: sys. selective_xml_index_paths (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xml_schema_attributes_TSQL
- xml_schema_attributes
- sys.xml_schema_attributes_TSQL
- sys.xml_schema_attributes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_attributes catalog view
ms.assetid: 07a73d71-ec3e-4894-947a-5859ca62c606
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 9ff85273a1e970b3bb891d1816a96019dd4f3ae5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135192"
---
# <a name="sysselective_xml_index_paths-transact-sql"></a>sys.selective_xml_index_paths (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 stellt jede Zeile in sys.selective_xml_index_paths einen höher gestuften Pfad für den jeweiligen selektiven XML-Index dar.  
  
 Wenn Sie einen selektiven XML-Index für xmlcol der Tabelle T anhand der Anweisung  
  
```  
CREATE SELECTIVE XML INDEX sxi1 ON T(xmlcol)   
FOR ( path1 = '/a/b/c' AS XQUERY 'xs:string',  
      path2 = '/a/b/d' AS XQUERY 'xs:double'  
    )  
```  
  
 erstellen, enthält sys.selective_xml_index_paths zwei neue Zeilen, die dem Index sxi1 entsprechen.  

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID der Tabelle mit der XML-Spalte.|  
|**index_id**|**int**|Die eindeutige ID des selektiven XML-Indexes.|  
|**path_id**|**int**|Die ID des höher gestuften XML-Pfads.|  
|**ADS**|**nvarchar(4000)**|Der höher gestufte Pfad. Beispiel: '/a/b/c/d/e'.|  
|**name**|**sysname**|Der Pfadname.|  
|**path_type**|**tinyint**|0 = XQUERY<br /><br /> 1 = SQL|  
|**path_type_desc**|**sysname**|Basierend auf **path_type** Wert ' XQuery ' oder ' SQL '.|  
|**xml_component_id**|**int**|Eindeutige ID der XML-Schemakomponente in der Datenbank.|  
|**xquery_type_description**|**nvarchar(4000)**|Der Name des angegebenen XSD-Typs.|  
|**is_xquery_type_inferred**|**bit**|1 = Der Typ wird abgeleitet.|  
|**xquery_max_length**|**smallint**|Die maximale Länge (in Zeichen des XSD-Typs).|  
|**is_xquery_max_length_inferred**|**bit**|1 = Die maximale Länge wird abgeleitet.|  
|**is_node**|**bit**|0 = Der node()-Hinweis ist nicht vorhanden.<br /><br /> 1 = Der node()-Optimierungshinweis wurde angewendet.|  
|**system_type_id**|**tinyint**|ID des System Typs der Spalte.|  
|**user_type_id**|**tinyint**|Die ID des Benutzertyps der Spalte.|  
|**max_length**|**smallint**|Die maximale Länge (in Bytes) des Typs.<br /><br /> -1 = Der Spaltendatentyp ist varchar(max), nvarchar(max), varbinary(max) oder xml.|  
|**precision**|**tinyint**|Die maximale Genauigkeit des Typs, wenn es sich um einen zahlenbasierten Typ handelt, andernfalls 0.|  
|**scale**|**tinyint**|Die maximalen Dezimalstellen des Typs, wenn es sich um einen zahlenbasierten Typ handelt. Andernfalls ist es 0.|  
|**collation_name**|**sysname**|Der Name der Sortierung des Typs, wenn es sich um einen zeichenbasierten Typ handelt. Andernfalls wird NULL verwendet.|  
|**is_singleton**|**bit**|0 = Der SINGLETON-Hinweis ist nicht vorhanden.<br /><br /> 1 = Der SINGLETON-Optimierungshinweis wurde angewendet.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-Schemas &#40;XML-Typsystem&#41; Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
