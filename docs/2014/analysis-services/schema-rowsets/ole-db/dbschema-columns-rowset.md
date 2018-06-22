---
title: DBSCHEMA_COLUMNS-Rowset | Microsoft Docs
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
- DBSCHEMA_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_COLUMNS rowset
ms.assetid: 653bdd07-a533-4a99-8b6a-6e5c7322e1f3
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 413e86e156db59e7621c94bdc1c99cd0087a987f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147770"
---
# <a name="dbschemacolumns-rowset"></a>DBSCHEMA_COLUMNS-Rowset
  Stellt Spalteninformationen für alle Spalten bereit, die den bereitgestellten Einschränkungskriterien entsprechen.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DBSCHEMA_COLUMNS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`||Der Name der Datenbank.|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`TABLE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Der Name der Attributhierarchie oder des Measures.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||Nicht unterstützt.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||Wird nicht unterstützt.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Die Position der Spalte, beginnend mit 1.|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||Wird nicht unterstützt.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||Eine `DBCOLUMNFLAGS`-Bitmaske, die die Spalteneigenschaften angibt. Siehe "DBCOLUMNFLAGS Enumerated Type" in [IColumnsInfo::GetColumnInfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Gibt immer `false`.|  
|`DATA_TYPE`|`DBTYPE_WSTR`<br /><br /> `DBTYPE_VARIANT`||Der Datentyp der Spalte. Gibt eine Zeichenfolge für Dimensionsspalten und eine Variante für Measures zurück.|  
|`TYPE_GUID`|`DBTYPE_GUID`||Wird nicht unterstützt.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Die maximal mögliche Länge eines Werts in der Spalte.<br /><br /> Dieser Wert wird von der `DataSize`-Eigenschaft in `DataItem` abgerufen.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Die maximal mögliche Länge eines Werts in der Spalte in Bytes für Zeichen- oder Binärspalten.<br /><br /> Der Wert null (0) gibt an, dass die Spalte keine maximale Länge besitzt.<br /><br /> `NULL` wird für Spalten zurückgegeben werden, die keine Binär-oder Zeichendatentypen Typen zurückgeben.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Die maximale Genauigkeit der Spalte für numerische Daten anderen Datentypen als `DBTYPE_VARNUMERIC`.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Die Anzahl der Ziffern rechts vom Dezimaltrennzeichen für `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC`, `DBTYPE_VARNUMERIC`. Andernfalls ist dies `NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Wird nicht unterstützt.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`||Den OLAP-Typ des Objekts.<br /><br /> `MEASURE` gibt an, dass das Objekt ein Measure ist.<br /><br /> `ATTRIBUTE` Gibt an, dass das Objekt ein Dimensionsattribut ist.<br /><br /> `SCHEMA` Gibt an, dass das Objekt eine Spalte in einem Schema ist.|  
  
 Das Rowset wird sortiert nach `TABLE_CATALOG`, `TABLE_SCHEMA`, `TABLE_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DBSCHEMA_COLUMNS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|Optional|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|Optional|  
|`TABLE_NAME`|`DBTYPE_WSTR`|Optional|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Optional|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`|Optional|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Schemarowsets](ole-db-schema-rowsets.md)  
  
  