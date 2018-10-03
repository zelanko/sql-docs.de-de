---
title: MDSCHEMA_CUBES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_CUBES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_CUBES rowset
ms.assetid: 5f1b63d4-aa3f-48c6-b866-7ffd91675044
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7282ceaacc4778c205c27e6ef226855f94398be1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048400"
---
# <a name="mdschemacubes-rowset"></a>MDSCHEMA_CUBES-Rowset
  Beschreibt die Struktur der Cubes innerhalb einer Datenbank.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_CUBES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name der Datenbank.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes oder der Dimension. Dimensionsnamen ist ein Dollarzeichensymbol ($) vorangestellt. **Hinweis:** nur Server- und Datenbankadministratoren Berechtigungen haben, um aus einer Dimension erstellten Cubes finden Sie unter.|  
|`CUBE_TYPE`|`DBTYPE_WSTR`||Der Typ des Cubes. Gültige Werte sind:<br /><br /> -   `CUBE`<br />-   `DIMENSION`|  
|`CUBE_GUID`|`DBTYPE_GUID`||Wird nicht unterstützt.|  
|`CREATED_ON`|`DBTYPE_DBTIMESTAMP`||Wird nicht unterstützt.|  
|`LAST_SCHEMA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Der Zeitpunkt der letzten Verarbeitung des Cubes.|  
|`SCHEMA_UPDATED_BY`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`LAST_DATA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Der Zeitpunkt der letzten Verarbeitung des Cubes.|  
|`DATA_UPDATED_BY`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung des Cubes.|  
|`IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||Ein boolescher Wert, der immer True zurückgibt.|  
|`IS_LINKABLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob ein Cube in einem verknüpften Cube verwendet werden kann.|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob für einen Cube der Schreibzugriff aktiviert ist.|  
|`IS_SQL_ENABLED`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob SQL für den Cube verwendet werden kann.|  
|`CUBE_CAPTION`|`DBTYPE_WSTR`||Die Beschriftung des Cubes.|  
|`BASE_CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Quellcubes, wenn dieser Cube ein perspektivischer Cube ist.|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||(Optional) Ein Satz von Hinweisen im XML-Format.|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_CUBES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem dieser gültigen Werte:<br /><br /> -1-CUBE<br />-2-DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
|`Base Cube_Name`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  
