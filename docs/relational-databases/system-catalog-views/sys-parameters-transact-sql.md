---
title: Sys.Parameters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.parameters_TSQL
- sys.parameters
- parameters
- parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.parameters catalog view
- table-valued parameters,sys.parameters
ms.assetid: 24e2764b-c8e5-4322-97a4-7407d8b8a92b
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: da8d3e66ed1d6e835c6b4702fc7bbab31dd186f2
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39535170"
---
# <a name="sysparameters-transact-sql"></a>sys.parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jeden Parameter eines Objekts, das Parameter annimmt. Wenn es sich bei dem Objekt um eine skalare Funktion handelt, gibt es auch eine einzelne Zeile, die den Rückgabewert beschreibt. Diese Zeile hat ein **Parameter_id** Wert 0.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID des Objekts, zu dem dieser Parameter gehört.|  
|**name**|**sysname**|Der Name des Parameters. Ist eindeutig innerhalb des Objekts.<br /><br /> Wenn es sich bei dem Objekt um eine skalare Funktion handelt, ist der Parametername eine leere Zeichenfolge in der Zeile, die den zurückgegebenen Wert darstellt.|  
|**parameter_id**|**int**|ID des Parameters. Ist eindeutig innerhalb des Objekts.<br /><br /> Handelt es sich bei dem Objekt um eine Skalarfunktion, stellt **parameter_id** = 0 den Rückgabewert dar.|  
|**system_type_id**|**tinyint**|ID des Systemtyps des Parameters.|  
|**user_type_id**|**int**|Die ID des vom Benutzer definierten Typs des Parameters.<br /><br /> Um den Namen des Typs zurückzugeben, fügen Sie der [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) -Katalogsicht für diese Spalte.|  
|**max_length**|**smallint**|Die maximale Länge des Parameters (in Byte).<br /><br /> Wert =-1 Wenn der Spaltendatentyp ist **varchar(max)**, **nvarchar(max)**, **'varbinary(max)'**, oder **Xml**.|  
|**Mit einfacher Genauigkeit**|**tinyint**|Genauigkeit des Parameters, wenn dieser numerisch ist. Andernfalls ist der Wert 0.|  
|**Skalieren**|**tinyint**|Dezimalstellen des Parameters, wenn dieser numerisch ist. Andernfalls ist der Wert 0.|  
|**is_output**|**bit**|1 = Parameter ist OUTPUT oder RETURN; andernfalls 0.|  
|**is_cursor_ref**|**bit**|1 = Der Parameter ist ein Cursorverweis.|  
|**has_default_value**|**bit**|1 = Der Parameter hat einen Standardwert.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwaltet nur Standardwerte für CLR-Objekte in dieser Katalogsicht. Daher weist diese Spalte für [!INCLUDE[tsql](../../includes/tsql-md.md)]-Objekte immer den Wert 0 auf. An den Standardwert eines Parameters in einer [!INCLUDE[tsql](../../includes/tsql-md.md)] Objekt, das Abfragen der **Definition** Spalte die [Sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) -Katalogsicht angezeigt werden soll, oder verwenden Sie die [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)-Systemfunktion.|  
|**is_xml_document**|**bit**|1 = Der Inhalt ist ein vollständiges XML-Dokument.<br /><br /> 0 = Inhalt ist ein Dokumentfragment, oder der Datentyp der Spalte nicht **Xml**.|  
|**default_value**|**sql_variant**|Wenn **Has_default_value** ist 1. der Wert dieser Spalte der Standardwert für den Parameter ist, andernfalls NULL.|  
|**xml_collection_id**|**int**|Ungleich 0, wenn der Datentyp des Parameters **xml** ist, und XML typisiert ist. Der Wert ist die ID der Auflistung, die den überprüfenden XML-Schemanamespace des Parameters enthält.<br /><br /> 0 = Keine XML-Schemaauflistung|  
|**is_readonly**|**bit**|1 = Parameter ist READONLY. Andernfalls 0.|  
|**is_nullable**|**bit**|1 = Parameter lässt NULL-Werte zu. (Standard).<br /><br /> 0 = Parameter lässt keine NULL-Werte zu, dies dient der effizienteren Ausführung von systemintern kompilierten gespeicherten Prozeduren.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Sys. all_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-parameters-transact-sql.md)   
 [Sys. system_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-parameters-transact-sql.md)  
  
  
