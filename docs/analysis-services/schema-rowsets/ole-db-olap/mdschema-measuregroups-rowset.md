---
title: MDSCHEMA_MEASUREGROUPS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df2bfe8aecc32c8f046d18fff4e72cd15409fdc8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029041"
---
# <a name="mdschemameasuregroups-rowset"></a>MDSCHEMA_MEASUREGROUPS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt die Measuregruppen innerhalb einer Datenbank.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **MDSCHEMA_MEASUREGROUPS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Der Name des Katalogs, zu dem diese Measuregruppe gehört. **NULL** , wenn der Anbieter keine Kataloge unterstützt.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Der Name des Cubes, zu dem diese Measuregruppe gehört.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Der Name der Measuregruppe.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Eine lesbare Beschreibung des Elements.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**||Ein boolescher Wert, der angibt, ob der Schreibzugriff für die Measuregruppe aktiviert ist.<br /><br /> Gibt **true** zurück, wenn der Schreibzugriff für die Measuregruppe aktiviert ist.|  
|**MEASUREGROUP_CAPTION**|**DBTYPE_WSTR**||Die Anzeigebeschriftung für die Measuregruppe.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **MDSCHEMA_MEASUREGROUPS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Optional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
