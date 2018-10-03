---
title: MDSCHEMA_KPIS-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_KPIS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_KPIS rowset
ms.assetid: 40fb5112-6a90-4455-82b3-8b6322490222
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77f6dc3fd3f8e9c92fe1d840c9af646269e0effc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124460"
---
# <a name="mdschemakpis-rowset"></a>MDSCHEMA_KPIS-Rowset
  Beschreibt die Key Performance Indicators (KPIs) innerhalb einer Datenbank.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_KPIS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Die Quelldatenbank.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der übergeordnete Cube für den KPI.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Die dem KPI zugeordnete Measuregruppe.<br /><br /> Sie können diese Spalte verwenden, um die Dimensionalität des KPI zu bestimmen. Wenn "**\<NULL >**", der KPI wird von allen Measuregruppen dimensioniert werden.<br /><br /> Der Standardwert ist "**\<NULL >**".|  
|`KPI_NAME`|`DBTYPE_WSTR`||Der Name des KPI.|  
|`KPI_CAPTION`|`DBTYPE_WSTR`||Eine Bezeichnung oder Beschriftung, die dem KPI zugeordnet ist. Wird hauptsächlich für Anzeigezwecke verwendet. Wenn keine Beschriftung vorhanden ist, wird `KPI_NAME` zurückgegeben.|  
|`KPI_DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung des KPI.|  
|`KPI_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Eine Zeichenfolge, die den Pfad des Anzeigeordners angibt, der von der Clientanwendung zum Anzeigen des Elements verwendet wird. Das Trennzeichen für Ordnerebenen wird von der Clientanwendung definiert. Für Tools und Clients, die vom [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], den umgekehrten Schrägstrich (\\) ebenentrennzeichen ist. Um mehrere Anzeigeordner bereitzustellen, verwenden Sie ein Semikolon (;), um die Ordner zu trennen.|  
|`KPI_VALUE`|`DBTYPE_WSTR`||Der eindeutige Name des Elements in der Measuredimension für den KPI-Wert.|  
|`KPI_GOAL`|`DBTYPE_WSTR`||Der eindeutige Name des Elements in der Measuredimension für das KPI-Ziel.<br /><br /> Gibt `NULL` zurück, wenn kein Ziel definiert wurde.|  
|`KPI_STATUS`|`DBTYPE_WSTR`||Der eindeutige Name des Elements in der Measuredimension für den KPI-Status.<br /><br /> Gibt `NULL` zurück, wenn kein Status definiert wurde.|  
|`KPI_TREND`|`DBTYPE_WSTR`||Der eindeutige Name des Elements in der Measuredimension für den KPI-Trend.<br /><br /> Gibt `NULL` zurück, wenn kein Trend definiert wurde.|  
|`KPI_STATUS_GRAPHIC`|`DBTYPE_WSTR`||Die standardmäßige grafische Darstellung des KPI.|  
|`KPI_TREND_GRAPHIC`|`DBTYPE_WSTR`||Die standardmäßige grafische Darstellung des KPI.|  
|`KPI_WEIGHT`|`DBTYPE_WSTR`||Der eindeutige Name des Elements in der Measuredimension für die KPI-Gewichtung.|  
|`KPI_CURRENT_TIME_MEMBER`|`DBTYPE_WSTR`||Der eindeutige Name des Elements in der Zeitdimension, die den zeitlichen Kontext des KPI definiert.<br /><br /> Gibt `NULL` zurück, wenn kein Zeitelement definiert wurde.|  
|`KPI_PARENT_KPI_NAME`|`DBTYPE_WSTR`||Der Name des übergeordneten KPI.|  
|`SCOPE`|`DBTYPE_I4`||Der Gültigkeitsbereich des KPI. Der KPI kann ein Sitzungs-KPI oder ein globaler KPI sein.<br /><br /> Diese Spalte kann einen der folgenden Werte besitzen:<br /><br /> -MDKPI_SCOPE_GLOBAL = 1<br />-MDKPI_SCOPE_SESSION = 2|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||(Optional) Ein Satz von Hinweisen im XML-Format.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_KPIS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`KPI_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -   `1` CUBE<br />-   `2` DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert `1`.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  
