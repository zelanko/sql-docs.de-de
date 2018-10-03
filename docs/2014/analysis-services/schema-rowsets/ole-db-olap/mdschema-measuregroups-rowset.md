---
title: MDSCHEMA_MEASUREGROUPS-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_MEASUREGROUPS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f889b66a9dcc72053c04adbd5e1949f6ebbf17dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060286"
---
# <a name="mdschemameasuregroups-rowset"></a>MDSCHEMA_MEASUREGROUPS-Rowset
  Beschreibt die Measuregruppen innerhalb einer Datenbank.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_MEASUREGROUPS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name des Katalogs, zu dem diese Measuregruppe gehört. `NULL`, wenn der Anbieter keine Kataloge unterstützt.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes, zu dem diese Measuregruppe gehört.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Der Name der Measuregruppe.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung des Elements.|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob der Schreibzugriff für die Measuregruppe aktiviert ist.<br /><br /> Gibt `true` die Measuregruppe ist Schreibzugriff aktiviert.|  
|`MEASUREGROUP_CAPTION`|`DBTYPE_WSTR`||Die Anzeigebeschriftung für die Measuregruppe.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_MEASUREGROUPS` Rowset kann auf die Spalten in der folgenden Tabelle eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  
