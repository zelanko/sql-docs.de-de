---
title: MDSCHEMA_HIERARCHIES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_HIERARCHIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_HIERARCHIES rowset
ms.assetid: 2e5b2a81-366e-4d5b-af1e-1d372bf596d9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e5361453290ea1c45de4868e7498c51b1738cdfd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134190"
---
# <a name="mdschemahierarchies-rowset"></a>MDSCHEMA_HIERARCHIES-Rowset
  Beschreibt jede Hierarchie innerhalb einer bestimmten Dimension.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_HIERARCHIES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name des Katalogs, zu dem diese Hierarchie gehört. `NULL`, wenn der Anbieter keine Kataloge unterstützt.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nicht unterstützt|  
|`CUBE_NAME`|`DBTYPE_WSTR`||(Erforderlich) Der Name des Cubes, zu dem diese Hierarchie gehört.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Dimension, zu der diese Hierarchie gehört. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`||Der Name der Hierarchie. Leer, wenn es nur eine einzelne Hierarchie in der Dimension gibt. Dies weist immer einen Wert in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Hierarchie.|  
|`HIERARCHY_GUID`|`DBTYPE_GUID`||Nicht unterstützt|  
|`HIERARCHY_CAPTION`|`DBTYPE_WSTR`||Eine Bezeichnung oder Beschriftung, der Hierarchie zugeordnet. Wird hauptsächlich für Anzeigezwecke verwendet. Wenn keine Beschriftung vorhanden ist, wird `HIERARCHY_NAME` zurückgegeben. Wenn die Dimension keine oder nur eine einzelne Hierarchie enthält, enthält diese Spalte den Namen der Dimension.|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||Der Typ der Dimension. Gültige Werte sind unter anderem:<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`HIERARCHY_CARDINALITY`|`DBTYPE_UI4`||Die Anzahl der Member in der Hierarchie.|  
|`DEFAULT_MEMBER`|`DBTYPE_WSTR`||Das Standardelement für diese Hierarchie. Dies ist ein eindeutiger Name. Jede Hierarchie muss ein Standardelement haben.|  
|`ALL_MEMBER`|`DBTYPE_WSTR`||Das Element auf der höchsten Rollupebene.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung der Hierarchie. `NULL`, wenn keine Beschreibung vorhanden ist.|  
|`STRUCTURE`|`DBTYPE_I2`||Die Struktur der Hierarchie. Gültige Werte sind unter anderem:<br /><br /> -   `MD_STRUCTURE_FULLYBALANCED` (`0`)<br />-   `MD_STRUCTURE_RAGGEDBALANCED` (`1`)<br />-   `MD_STRUCTURE_UNBALANCED` (`2`)<br />-   `MD_STRUCTURE_NETWORK` (`3`)|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||Gibt immer `False`.|  
|`IS_READWRITE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die "Rückschreiben von Dimensionen"-Spalte aktiviert ist.<br /><br /> Gibt `TRUE` zurück, wenn die `Write Back to dimension`-Spalte, die diese Hierarchie darstellt, aktiviert wird.|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||Gibt immer `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`) zurück.|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Gibt immer `NULL`.|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Gibt immer `true`. Wenn die Dimension nicht sichtbar ist, wird sie nicht im Schemarowset angezeigt.|  
|`HIERARCHY_ORDINAL`|`DBTYPE_UI4`||Gibt die Ordnungszahl der Hierarchie über alle Hierarchien des Cubes hinweg zurück.|  
|`DIMENSION_IS_SHARED`|`DBTYPE_BOOL`||Gibt immer `TRUE`.|  
|`HIERARCHY_IS_VISIBLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Hierarchie sichtbar ist.<br /><br /> Gibt `TRUE` zurück, wenn die Hierarchie sichtbar ist; andernfalls wird `FALSE` verwendet.|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`||Eine Bitmaske, die die Quelle der Hierarchie bestimmt:<br /><br /> -   `MD_USER_DEFINED` identifiziert benutzerdefinierte Hierarchien und hat den Wert `0x0000001`.<br />-   `MD_SYSTEM_ENABLED` identifiziert Attributhierarchien und verfügt über einen Wert von `0x0000002`.<br />-   `MD_SYSTEM_INTERNAL` identifiziert Attribute ohne Attributhierarchien und verfügt über einen Wert von **0 x 0000004**.<br /><br /> Eine Über-/Unterordnungs-Attributhierarchie ist sowohl `MD_USER_DEFINED` als auch `MD_SYSTEM_ENABLED`.|  
|`HIERARCHY_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Der zu verwendende Pfad beim Anzeigen der Hierarchie in der Benutzeroberfläche. Ordnernamen werden durch ein Semikolon (;) voneinander getrennt. Geschachtelte Ordner werden angezeigt, durch einen umgekehrten Schrägstrich (\\).|  
|`INSTANCE_SELECTION`|`DBTYPE_UI2`||Ein Hinweis an die Clientanwendung, wie die Hierarchie angezeigt werden soll. Gültige Werte sind unter anderem:<br /><br /> -   `MD_INSTANCE_SELECTION_NONE`<br />-   `MD_INSTANCE_SELECTION_DROPDOWN`<br />-   `MD_INSTANCE_SELECTION_LIST`<br />-   `MD_INSTANCE_SELECTION_FILTEREDLIST`<br />-   `MD_INSTANCE_SELECTION_MANDATORYFILTER`|  
|`GROUPING_BEHAVIOR`|`DBTYPE_I2`||Eine Enumeration, die das erwartete Gruppierungsverhalten von Clients für diese Hierarchie angibt. Mögliche Werte sind die folgenden:<br /><br /> -   **EncourageGrouping** (1)<br />-   **DiscourageGrouping** (2)|  
|`STRUCTURE_TYPE`|`DBTYPE_WSTR`||Gibt den Typ der Hierarchie an. Gültige Werte sind unter anderem:<br /><br /> -   `Natural`<br />-   `Unnatural`<br />-   `Unknown`|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME` und `HIERARCHY_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_HIERARCHIES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`|Optional.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`|(Optional) Eine Standardeinschränkung ist für MD_USER_DEFINED und MD_SYSTEM_ENABLED gültig.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-CUBE<br />-2-DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
|`HIERARCHY_VISIBILITY`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-sichtbar<br />– 2 nicht sichtbar<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  
