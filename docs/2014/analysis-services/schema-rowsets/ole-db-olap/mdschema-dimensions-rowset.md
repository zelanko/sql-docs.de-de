---
title: MDSCHEMA_DIMENSIONS-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_DIMENSIONS rowset
ms.assetid: a0fd94bb-359a-4df6-93a6-d60d50223944
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 49cd8f4f01840b67cde31d9031320ac276ec6faa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152634"
---
# <a name="mdschemadimensions-rowset"></a>MDSCHEMA_DIMENSIONS-Rowset
  Beschreibt die freigegebenen und privaten Dimensionen innerhalb einer Datenbank.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das `MDSCHEMA_DIMENSIONS`-Rowset enthält die folgenden Spalten:  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name der Datenbank.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Der Name der Dimension. Wenn eine Dimension Teil mehrerer Cubes oder Measuregruppen ist, dann ist für jede eindeutige Kombination aus Dimension, Measuregruppe und Cube eine Zeile vorhanden.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Dimension.|  
|`DIMENSION_GUID`|`DBTYPE_GUID`||Wird nicht unterstützt.|  
|`DIMENSION_CAPTION`|`DBTYPE_WSTR`||Die Beschriftung der Dimension. Diese sollte verwendet werden, wenn dem Benutzer der Name der Dimension angezeigt wird, beispielsweise in der Benutzeroberfläche oder in Berichten.|  
|`DIMENSION_ORDINAL`|`DBTYPE_UI4`||Die Position der Dimension innerhalb des Cubes.|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||Der Typ der Dimension. Gültige Werte sind:<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`DIMENSION_CARDINALITY`|`DBTYPE_UI4`||Die Anzahl der Elemente im Schlüsselattribut.|  
|`DEFAULT_HIERARCHY`|`DBTYPE_WSTR`||Eine Hierarchie aus der Dimension. Dieser Parameter wird aus Gründen der Abwärtskompatibilität beibehalten.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung der Dimension.|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||Immer `FALSE`.|  
|`IS_READWRITE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob der Schreibzugriff für die Dimension aktiviert ist.<br /><br /> `TRUE`, wenn der Schreibzugriff für die Dimension aktiviert ist.|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||Eine Bitmap, die angibt, welche Spalten eindeutige Werte enthalten, wenn die Dimension nur Elemente mit eindeutigen Namen enthält. Die folgenden Bitwertkonstanten sind in der Datei Msmd.h für diese Bitmap definiert:<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE`|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Immer `NULL`.|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Immer `TRUE`. **Hinweis:** eine Dimension ist nicht sichtbar, es sei denn, eine oder mehrere Hierarchien in der Dimension sichtbar sind.|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_DIMENSIONS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`|Optional.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-CUBE<br />-2-DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-sichtbar<br />– 2 nicht sichtbar<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  
