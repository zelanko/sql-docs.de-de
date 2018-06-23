---
title: MDSCHEMA_MEMBERS-Rowset | Microsoft Docs
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
- MDSCHEMA_MEMBERS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEMBERS rowset
ms.assetid: 0b1aada0-67f8-4ef6-81b2-0100b65e0c2f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2473797ef34c0fd204c878da8c6044a307cc1ee3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161233"
---
# <a name="mdschemamembers-rowset"></a>MDSCHEMA_MEMBERS-Rowset
  Beschreibt die Elemente innerhalb einer Datenbank.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_MEMBERS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name der Datenbank, zu der dieses Element gehört.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Der Name des Schemas, zu dem dieses Element gehört.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes, zu dem dieses Element gehört.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Dimension, zu der dieses Element gehört.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Hierarchie, zu der dieses Element gehört.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Ebene, zu der dieses Element gehört.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||Der Abstand des Elements vom Stamm der Hierarchie. Die Stammebene entspricht null (0).|  
|`MEMBER_ORDINAL`|`DBTYPE_UI4`||(Als veraltet markiert) Gibt immer `0` zurück.|  
|`MEMBER_NAME`|`DBTYPE_WSTR`||Der Name des Elements.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name des Elements.|  
|`MEMBER_TYPE`|`DBTYPE_I4`||Der Typ des Elements:<br /><br /> -   `MDMEMBER_TYPE_REGULAR` (`1`)<br />-   `MDMEMBER_TYPE_ALL` (`2`)<br />-   `MDMEMBER_TYPE_MEASURE` (`3`)<br />-   `MDMEMBER_TYPE_FORMULA` (`4`)<br />-   `MDMEMBER_TYPE_UNKNOWN` (`0`)<br />-   `MDMEMBER_TYPE_FORMULA` hat Vorrang vor `MDMEMBER_TYPE_MEASURE`. Wenn beispielsweise ein Formelelement (berechnetes Element) in der Measures-Dimension vorhanden ist, wird dieses als `MDMEMBER_TYPE_FORMULA` aufgeführt.|  
|`MEMBER_GUID`|`DBTYPE_GUID`||Die GUID des Elements. `NULL`, wenn keine GUID vorhanden ist.|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`||Eine Bezeichnung oder Beschriftung, die dem Element zugeordnet ist. Wird hauptsächlich für Anzeigezwecke verwendet. Wenn keine Beschriftung vorhanden ist, wird `MEMBER_NAME` zurückgegeben.|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||Die Anzahl der untergeordneten Elemente des Elements. Dies kann eine Schätzung sein, daher sollten sich Consumer nicht darauf verlassen, dass es sich um die exakte Anzahl handelt. Anbieter sollten die bestmögliche Schätzung zurückgeben.|  
|`PARENT_LEVEL`|`DBTYPE_UI4`||Der Abstand des dem Element übergeordneten Elements von der Stammebene der Hierarchie. Die Stammebene entspricht null (0).|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name des dem Element übergeordneten Elements. Für sämtliche Elemente auf der Stammebene wird `NULL` zurückgegeben.|  
|`PARENT_COUNT`|`DBTYPE_UI4`||Die Anzahl der übergeordneten Elemente des Elements.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Diese Spalte gibt immer einen `NULL`-Wert zurück.<br /><br /> Diese Spalte ist aus Gründen der Abwärtskompatibilität vorhanden.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Der Ausdruck für Berechnungen, wenn das Element vom Typ `MDMEMBER_TYPE_FORMULA` ist|  
|`MEMBER_KEY`|`DBTYPE_WSTR`||Der Wert der Schlüsselspalte des Elements. Gibt `NULL` zurück, wenn das Element einen zusammengesetzten Schlüssel besitzt.|  
|`IS_PLACEHOLDERMEMBER`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob ein Element ein Platzhalterelement für eine leere Position in einer Dimensionshierarchie ist.<br /><br /> Dieser ist nur gültig, wenn die `MDX Compatibility`-Eigenschaft auf 2 festgelegt ist.|  
|`IS_DATAMEMBER`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob das Element ein Datenelement ist.<br /><br /> Gibt "True" zurück, wenn das Element ein Datenelement ist.|  
|`SCOPE`|`DBTYPE_I4`||Der Gültigkeitsbereich des Elements. Das Element kann ein in der Sitzung berechnetes Element oder ein global berechnetes Element sein. Die Spalte gibt `NULL` für nicht berechnete Elemente zurück.<br /><br /> Diese Spalte kann einen der folgenden Werte besitzen:<br /><br /> -MDMEMBER_SCOPE_GLOBAL = 1<br />-MDMEMBER_SCOPE_SESSION = 2|  
|`Zero or more additional columns`|`DBTYPE_UI2`||Es werden keine Eigenschaften zurückgegeben, wenn das Element von mehreren Ebenen zurückgegeben werden könnte. Wenn der Tree-Operator beispielsweise `PARENT` ist und für andere als Über-/Unterordnungshierarchien `SELF` ist, werden keine Elementeigenschaften zurückgegeben.<br /><br /> Dies gilt für unregelmäßige Hierarchien, in denen Tree-Operatoren Elemente von unterschiedlichen Ebenen zurückgeben könnten (beispielsweise wenn die vorherige Ebene Lücken enthält und übergeordnete Elemente für Elemente angefordert werden).|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_UNIQUE_NAME`, `LEVEL_UNIQUE_NAME`, `LEVEL_NUMBER`, `MEMBER_ORDINAL`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_MEMBERS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`|Optional.|  
|`MEMBER_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`|Optional.|  
|`MEMBER_TYPE`|`DBTYPE_I4`|Optional.|  
|`TREE_OP`|`DBTYPE_I4`|(Optional) Gilt nur für ein einzelnes Element:<br /><br /> -   `MDTREEOP_ANCESTORS` (`0x20`) gibt alle Vorgänger zurück.<br />-   `MDTREEOP_CHILDREN` (`0x01`) nur die unmittelbar untergeordneten Elemente zurückgegeben.<br />-   `MDTREEOP_SIBLINGS` (`0x02`) gibt Elemente auf der gleichen Ebene zurück.<br />-   `MDTREEOP_PARENT` (`0x04`) gibt nur das unmittelbar übergeordnete Element.<br />-   `MDTREEOP_SELF` (`0x08`) selbst in der Liste der zurückgegebenen Zeilen zurück.<br />-   `MDTREEOP_DESCENDANTS` (`0x10`) gibt alle Nachfolger zurück.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-CUBE<br />-2-DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  