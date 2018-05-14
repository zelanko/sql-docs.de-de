---
title: MDSCHEMA_INPUT_DATASOURCES-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 329f3081e3e16b3603c5ddd299ccafc0a98f6a9a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="mdschemainputdatasources-rowset"></a>MDSCHEMA_INPUT_DATASOURCES-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt die innerhalb der Datenbank definierten Datenquellen.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **MDSCHEMA_INPUT_DATASOURCES** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Der Name des Katalogs, zu dem diese Datenquelle gehört.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Nicht unterstützt.|  
|**%{DATASOURCE_NAME/}-DATENQUELLE**|**DBTYPE_WSTR**||Der Name des Datenquellenobjekts.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**||Der Typ der Datenquelle. Gültige Werte sind:<br /><br /> **Relationale**<br /><br /> **OLAP**|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**||Das Datum, an dem die Datenquelle erstellt wurde.|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**||Das Datum und die Uhrzeit der letzten Änderung der Datenquelle.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Eine benutzerfreundliche Beschreibung der Aktion.|  
|**TIMEOUT**|**DBTYPE_UI4**||Das Timeout der Datenquelle.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **MDSCHEMA_INPUT_DATASOURCES** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Optional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Optional.|  
|**%{DATASOURCE_NAME/}-DATENQUELLE**|**DBTYPE_WSTR**|Optional.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
