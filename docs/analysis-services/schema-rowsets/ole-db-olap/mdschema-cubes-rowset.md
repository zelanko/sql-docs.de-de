---
title: MDSCHEMA_CUBES-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: da0fc34fedcd6980f8dd19e199314fc1295c78bb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037071"
---
# <a name="mdschemacubes-rowset"></a>MDSCHEMA_CUBES-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt die Struktur der Cubes innerhalb einer Datenbank.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **MDSCHEMA_CUBES** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Der Name der Datenbank.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Nicht unterstützt.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Der Name des Cubes oder der Dimension. Dimensionsnamen ist ein Dollarzeichensymbol ($) vorangestellt.<br /><br /> Hinweis: Nur Server- und Datenbankadministratoren haben Berechtigungen zum Anzeigen von Cubes, die aus einer Dimension erstellt wurden.|  
|**CUBE_TYPE**|**DBTYPE_WSTR**|Der Typ des Cubes. Gültige Werte sind:<br /><br /> **CUBE**<br /><br /> **DIMENSION**|  
|**CUBE_GUID**|**DBTYPE_GUID**|Nicht unterstützt.|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**|Nicht unterstützt.|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**|Der Zeitpunkt der letzten Verarbeitung des Cubes.|  
|**SCHEMA_UPDATED_BY**|**DBTYPE_WSTR**|Nicht unterstützt.|  
|**LAST_DATA_UPDATE**|**DBTYPE_DBTIMESTAMP**|Der Zeitpunkt der letzten Verarbeitung des Cubes.|  
|**DATA_UPDATED_BY**|**DBTYPE_WSTR**|Nicht unterstützt.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Eine benutzerfreundliche Beschreibung des Cubes.|  
|**IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|Ein boolescher Wert, der immer True zurückgibt.|  
|**IS_LINKABLE**|**DBTYPE_BOOL**|Ein boolescher Wert, der angibt, ob ein Cube in einem verknüpften Cube verwendet werden kann.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**|Ein boolescher Wert, der angibt, ob für einen Cube der Schreibzugriff aktiviert ist.|  
|**IS_SQL_ENABLED**|**DBTYPE_BOOL**|Ein boolescher Wert, der angibt, ob SQL für den Cube verwendet werden kann.|  
|**CUBE_CAPTION**|**DBTYPE_WSTR**|Die Beschriftung des Cubes.|  
|**BASE_CUBE_NAME**|**DBTYPE_WSTR**|Der Name des Quellcubes, wenn dieser Cube ein perspektivischer Cube ist.|  
|**ANMERKUNGEN**|**DBTYPE_WSTR**|(Optional) Ein Satz von Hinweisen im XML-Format.|  
  
 Das Rowset wird sortiert nach **CATALOG_NAME**, **SCHEMA_NAME**und **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **MDSCHEMA_CUBES** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Optional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Optional) Standardeinschränkung besitzt den Wert 1. Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**Basis Cube_Name**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
