---
title: DBSCHEMA_COLUMNS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2bb1fec6a1633f545f0c65feda93c7e19c649a6e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="dbschemacolumns-rowset"></a>DBSCHEMA_COLUMNS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Stellt Spalteninformationen für alle Spalten bereit, die den bereitgestellten Einschränkungskriterien entsprechen.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DBSCHEMA_COLUMNS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**||Der Name der Datenbank.|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**TABLE_NAME**|**DBTYPE_WSTR**||Der Name des Cubes.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**||Der Name der Attributhierarchie oder des Measures.|  
|**COLUMN_GUID**|**DBTYPE_GUID**||Nicht unterstützt.|  
|**COLUMN_PROPID**|**DBTYPE_UI4**||Nicht unterstützt.|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**||Die Position der Spalte, beginnend mit 1.|  
|**COLUMN_HAS_DEFAULT**|**DBTYPE_BOOL**||Nicht unterstützt.|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**||Eine **DBCOLUMNFLAGS** -Bitmaske, die die Spalteneigenschaften angibt. Siehe "DBCOLUMNFLAGS Enumerated Type" in [IColumnsInfo::GetColumnInfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|**IS_NULLABLE**|**DBTYPE_BOOL**||Gibt immer **false**zurück.|  
|**DATA_TYPE**|**DBTYPE_WSTR**<br /><br /> **DBTYPE_VARIANT**||Der Datentyp der Spalte. Gibt eine Zeichenfolge für Dimensionsspalten und eine Variante für Measures zurück.|  
|**TYPE_GUID**|**DBTYPE_GUID**||Nicht unterstützt.|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**||Die maximal mögliche Länge eines Werts in der Spalte.<br /><br /> Dieser Wert wird von der **DataSize** -Eigenschaft in **DataItem**abgerufen.|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**||Die maximal mögliche Länge eines Werts in der Spalte in Bytes für Zeichen- oder Binärspalten.<br /><br /> Der Wert null (0) gibt an, dass die Spalte keine maximale Länge besitzt.<br /><br /> Für Spalten, die keine Binär- oder Zeichendatentypen zurückgeben, wird**NULL** zurückgegeben.|  
|**"NUMERIC_PRECISION"**|**DBTYPE_UI2**||Die maximale Genauigkeit der Spalte für andere numerische Datentypen als **DBTYPE_VARNUMERIC**.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||Die Anzahl der Stellen rechts neben dem Dezimalzeichen für **DBTYPE_DECIMAL**, **DBTYPE_NUMERIC**und **DBTYPE_VARNUMERIC**. Andernfalls ist der Wert **NULL**.|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**||Nicht unterstützt.|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**SORTIERUNGSNAME**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**DOMÄNENNAME**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**COLUMN_OLAP_TYPE**|**DBTYPE_WSTR**||Den OLAP-Typ des Objekts.<br /><br /> **MEASURE** gibt an, dass das Objekt ein Measure ist.<br /><br /> **ATTRIBUTE** gibt an, dass das Objekt ein Dimensionsattribut ist.<br /><br /> **SCHEMA** gibt an, dass das Objekt eine Spalte in einem Schema ist.|  
  
 Das Rowset wird sortiert nach **TABLE_CATALOG**, **TABLE_SCHEMA**und **TABLE_NAME**.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DBSCHEMA_COLUMNS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|Optional|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|Optional|  
|**TABLE_NAME**|**DBTYPE_WSTR**|Optional|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|Optional|  
|**COLUMN_OLAP_TYPE**|**DBTYPE_WSTR**|Optional|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Schemarowsets](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
