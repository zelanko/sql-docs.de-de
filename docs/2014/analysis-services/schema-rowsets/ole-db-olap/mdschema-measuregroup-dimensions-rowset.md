---
title: MDSCHEMA_MEASUREGROUP_DIMENSIONS-Rowset | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS rowset
ms.assetid: c731c06a-7382-4e50-ba0e-d8cee3ab4f28
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f607b966099f71acee460a5a343c557e2a81857e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050402"
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>MDSCHEMA_MEASUREGROUP_DIMENSIONS-Rowset
  Listet die Dimensionen der Measuregruppe auf.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_MEASUREGROUP_DIMENSIONS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name des Katalogs, zu dem diese Measuregruppe gehört. `NULL`, wenn der Anbieter keine Kataloge unterstützt.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes, zu dem diese Measuregruppe gehört.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Der Name der Measuregruppe.|  
|`MEASUREGROUP_CARDINALITY`|`DBTYPE_WSTR`||Die Anzahl der Instanzen, die ein Measure in der Measuregruppe für ein einzelnes Dimensionselement haben kann. Zulässige Werte:<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name für die Dimension.|  
|`DIMENSION_CARDINALITY`|`DBTYPE_WSTR`||Die Anzahl der Instanzen, die ein Dimensionselement für eine einzelne Instanz eines Measures der Measuregruppe haben kann.<br /><br /> Zulässige Werte:<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Hierarchien in der Dimension sichtbar sind.<br /><br /> Gibt `TRUE` zurück, wenn eine oder mehrere Hierarchien in der Dimension sichtbar sind; andernfalls wird `FALSE` zurückgegeben.|  
|`DIMENSION_IS_FACT_DIMENSION`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Dimension eine Faktendimension ist.<br /><br /> Gibt `TRUE` zurück, wenn die Dimension eine Faktendimension ist; andernfalls wird `FALSE` zurückgegeben.|  
|`DIMENSION_PATH`|`DBTYPE_HCHAPTER`||Eine Liste der Dimensionen für die Referenzdimension.|  
|`DIMENSION_GRANULARITY`|`DBTYPE_WSTR`||Der eindeutige Name der Granularitätshierarchie.|  
  
 Das Rowset unterstützt die Sortierung nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `MEASUREGROUP_NAME` und `DIMENSION_UNIQUE_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_MEASUREGROUP_DIMENSIONS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Optional.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -Visible 1<br />-2 nicht sichtbar<br />-Die standardeinschränkung ist ein Wert von 1.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  