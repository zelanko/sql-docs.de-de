---
title: MDSCHEMA_LEVELS-Rowset | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_LEVELS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_LEVELS rowset
ms.assetid: 4313e268-33f4-4e99-96d7-2ec26775c580
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 51aced8c191943330b6df9f08fc65292b1a77d81
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059006"
---
# <a name="mdschemalevels-rowset"></a>MDSCHEMA_LEVELS-Rowset
  Beschreibt jede Ebene innerhalb einer bestimmten Hierarchie.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_LEVELS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name des Katalogs, zu dem diese Ebene gehört. `NULL`, wenn der Anbieter keine Kataloge unterstützt.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Der Name des Schemas, zu dem diese Ebene gehört. `NULL`, wenn der Anbieter keine Schemas unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes, zu dem diese Ebene gehört.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Dimension, zu der diese Ebene gehört. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Hierarchie. Wenn die Ebene zu mehreren Hierarchien gehört, gibt es eine Zeile für jede Hierarchie, zu der die Ebene gehört. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`LEVEL_NAME`|`DBTYPE_WSTR`||Der Name der Ebene.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Der ordnungsgemäß mit Escapezeichen versehene eindeutige Name der Ebene.|  
|`LEVEL_GUID`|`DBTYPE_GUID`||Wird nicht unterstützt.|  
|`LEVEL_CAPTION`|`DBTYPE_WSTR`||Eine Bezeichnung oder Beschriftung, die der Hierarchie zugeordnet ist. Wird hauptsächlich für Anzeigezwecke verwendet. Wenn keine Beschriftung vorhanden ist, wird `LEVEL_NAME` zurückgegeben.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||Der Abstand der Ebene vom Stamm der Hierarchie. Die Stammebene entspricht null (`0)`.|  
|`LEVEL_CARDINALITY`|`DBTYPE_UI4`||Die Anzahl der Elemente in der Ebene.|  
|`LEVEL_TYPE`|`DBTYPE_I4`||Der Typ der Ebene:<br /><br /> -   `MDLEVEL_TYPE_GEO_CONTINENT` (`0x2001`)<br />-   `MDLEVEL_TYPE_GEO_REGION` (`0x2002`)<br />-   `MDLEVEL_TYPE_GEO_COUNTRY` (`0x2003`)<br />-   `MDLEVEL_TYPE_GEO_STATE_OR_PROVINCE` (`0x2004`)<br />-   `MDLEVEL_TYPE_GEO_COUNTY` (`0x2005`)<br />-   `MDLEVEL_TYPE_GEO_CITY` (`0x2006`)<br />-   `MDLEVEL_TYPE_GEO_POSTALCODE` (`0x2007`)<br />-   `MDLEVEL_TYPE_GEO_POINT` (`0x2008`)<br />-   `MDLEVEL_TYPE_ORG_UNIT` (`0x1011`)<br />-   `MDLEVEL_TYPE_BOM_RESOURCE` (`0x1012`)<br />-   **MDLEVEL_TYPE_QUANTITATIVE** (`0x1013`)<br />-   `MDLEVEL_TYPE_ACCOUNT` (`0x1014`)<br />-   `MDLEVEL_TYPE_CUSTOMER` (`0x1021`)<br />-   `MDLEVEL_TYPE_CUSTOMER_GROUP` (`0x1022`)<br />-   `MDLEVEL_TYPE_CUSTOMER_HOUSEHOLD` (`0x1023`)<br />-   `MDLEVEL_TYPE_PRODUCT` (`0x1031`)<br />-   `MDLEVEL_TYPE_PRODUCT_GROUP` (`0x1032`)<br />-   `MDLEVEL_TYPE_SCENARIO` (`0x1015`)<br />-   `MDLEVEL_TYPE_UTILITY` (`0x1016`)<br />-   `MDLEVEL_TYPE_PERSON` (`0x1041`)<br />-   `MDLEVEL_TYPE_COMPANY` (`0x1042`)<br />-   `MDLEVEL_TYPE_CURRENCY_SOURCE` (`0x1051`)<br />-   `MDLEVEL_TYPE_CURRENCY_DESTINATION` (`0x1052`)<br />-   `MDLEVEL_TYPE_CHANNEL` (`0x1061`)<br />-   `MDLEVEL_TYPE_REPRESENTATIVE` (`0x1062`)<br />-   `MDLEVEL_TYPE_PROMOTION` (`0x1071`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung der Ebene. NULL, wenn keine Beschreibung vorhanden ist.|  
|`CUSTOM_ROLLUP_SETTINGS`|`DBTYPE_I4`||Eine Bitmap, die die benutzerdefinierten Rollupoptionen angibt:<br /><br /> -   `MDLEVELS_CUSTOM_ROLLUP_EXPRESSION` (`0x01`) gibt an, ein Ausdruck für diese Ebene vorhanden ist. (Veraltet)<br />-   `MDLEVELS_CUSTOM_ROLLUP_COLUMN` (`0x02`) gibt an, dass eine benutzerdefinierte Rollupspalte für diese Ebene vorhanden ist.<br />-   `MDLEVELS_SKIPPED_LEVELS` (`0x04`) gibt an, dass eine übersprungene Ebene, die Elementen dieser Ebene zugeordnet.<br />-   `MDLEVELS_CUSTOM_MEMBER_PROPERTIES` (`0x08`) gibt an, dass die Elemente der Ebene über benutzerdefinierte Elementeigenschaften verfügen.<br />-   `MDLEVELS_UNARY_OPERATOR` (`0x10`) gibt an, dass Elemente auf der Ebene über unäre Operatoren verfügen.|  
|`LEVEL_UNIQUE_SETTINGS`|`DBTYPE_I4`||Eine Bitmap, die angibt, welche Spalten eindeutige Werte enthalten, wenn die Ebene nur Elemente mit eindeutigen Namen oder Schlüsseln enthält. Die Datei Msmd.h definiert die folgenden Bitwertkonstanten für diese Bitmap:<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`)<br />-   `MDDIMENSIONS_MEMBER_NAME_UNIQUE` (`2`)<br /><br /> Der Schlüssel ist immer eindeutig in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Der Name ist eindeutig, wenn die Einstellung für das Attribut `UniqueInDimension` oder `UniqueInAttribute` lautet.|  
|`LEVEL_IS_VISIBLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Ebene sichtbar ist.<br /><br /> Es wird immer True zurückgegeben. Wenn die Ebene nicht sichtbar ist, wird sie nicht im Schemarowset angezeigt.|  
|`LEVEL_ORDERING_PROPERTY`|`DBTYPE_WSTR`||Die ID des Attributs, anhand dessen die Ebene sortiert wird.|  
|`LEVEL_DBTYPE`|`DBTYPE_I4`||Die `DBTYPE`-Enumeration der Elementschlüsselspalte, die für das Ebenenattribut verwendet wird.<br /><br /> NULL, wenn verkettete Schlüssel als Elementschlüsselspalte verwendet werden.|  
|`LEVEL_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Gibt immer NULL zurück.|  
|`LEVEL_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Die SQL-Darstellung der Ebenenelementnamen.|  
|`LEVEL_KEY_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Die SQL-Darstellung der Ebenenelement-Schlüsselwerte.|  
|`LEVEL_UNIQUE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Die SQL-Darstellung der eindeutigen Ebenennamen.|  
|`LEVEL_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||Der Name der Attributhierarchie, die die Quelle der Ebene bereitstellt.|  
|`LEVEL_KEY_CARDINALITY`|`DBTYPE_UI2`||Die Anzahl der Spalten im Ebenenschlüssel.|  
|`LEVEL_ORIGIN`|`DBTYPE_UI2`||Eine Bitmap, die definiert, wie die Quelle der Ebene bestimmt wird:<br /><br /> -   `MD_ORIGIN_USER_DEFINED` Gibt Ebenen in einer benutzerdefinierten Hierarchie.<br />-   `MD_ORIGIN_ATTRIBUTE` Gibt Ebenen in einer Attributhierarchie an.<br />-   `MD_ORIGIN_KEY_ATTRIBUTE` Gibt Ebenen in einer schlüsselattributhierarchie an.<br />-   `MD_ORIGIN_INTERNAL` Gibt Ebenen in Attributhierarchien, die nicht aktiviert sind.|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_UNIQUE_NAME` und `LEVEL_NUMBER`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_LEVELS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`LEVEL_NAME`|`DBTYPE_WSTR`|Optional.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`LEVEL_ORIGIN`|`DBTYPE_UI2`|(Optional) Eine Standardeinschränkung ist für `MD_USER_DEFINED` und `MD_SYSTEM_ENABLED` gültig.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-CUBE<br />-2-DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
|`LEVEL_VISIBILITY`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden Werte:<br /><br /> -Visible 1<br />-2 nicht sichtbar<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  