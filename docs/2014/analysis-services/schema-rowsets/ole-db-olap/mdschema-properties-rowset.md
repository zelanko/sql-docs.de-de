---
title: MDSCHEMA_PROPERTIES-Rowset | Microsoft Docs
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
- MDSCHEMA_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_PROPERTIES rowset
ms.assetid: 95c480f7-c525-44ba-a59b-cd36f5855a4f
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7c0e0506be8f531018285bba9145a587448e743e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049991"
---
# <a name="mdschemaproperties-rowset"></a>MDSCHEMA_PROPERTIES-Rowset
  Beschreibt die Eigenschaften von Elementen innerhalb einer Datenbank.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_PROPERTIES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name der Datenbank.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Der Name des Schemas, zu dem diese Eigenschaft gehört. `NULL`, wenn der Anbieter keine Schemas unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Dimension. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Hierarchie. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name der Ebene, zu der diese Eigenschaft gehört. Wenn der Anbieter keine benannten Ebenen unterstützt, sollte der `DIMENSION_UNIQUE_NAME`-Wert für dieses Feld zurückgegeben werden. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name des Elements, zu dem diese Eigenschaft gehört. Wird für Datenspeicher verwendet, die keine benannten Ebenen unterstützen oder Eigenschaften elementweise speichern. Wenn die Eigenschaft für alle Elemente in einer Ebene gilt, ist diese Spalte `NULL`. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`PROPERTY_TYPE`|`DBTYPE_I2`||Eine Bitmap, die den Typ der Eigenschaft angibt:<br /><br /> -   `MDPROP_MEMBER` (`1`) bezeichnet eine Eigenschaft eines Elements. Diese Eigenschaft kann in der DIMENSION PROPERTIES-Klausel der SELECT-Anweisung verwendet werden.<br />-   `MDPROP_CELL` (`2`) bezeichnet eine Eigenschaft einer Zelle. Diese Eigenschaft kann in der CELL PROPERTIES-Klausel verwendet werden, die am Ende der SELECT-Anweisung vorkommt.<br />-   `MDPROP_SYSTEM` (`4`) gibt eine interne Eigenschaft.<br />-   `MDPROP_BLOB` (`8`) bezeichnet eine Eigenschaft, die ein binary large Object (Blob) enthält.|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`||Der Name der Eigenschaft. Wenn der Schlüssel für die Eigenschaft dem Namen der Eigenschaft entspricht, ist `PROPERTY_NAME` leer.|  
|`PROPERTY_CAPTION`|`DBTYPE_WSTR`||Eine der Eigenschaft zugeordnete Bezeichnung oder Beschriftung, die hauptsächlich zu Anzeigezwecken verwendet wird. Gibt `PROPERTY_NAME` zurück, wenn keine Beschriftung vorhanden ist.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Der Datentyp der Eigenschaft.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Die maximal mögliche Länge der Eigenschaft, wenn es sich um einen Zeichen-, Binär- oder Bittyp handelt.<br /><br /> Null gibt an, dass es keine definierte maximale Länge gibt.<br /><br /> Gibt `NULL` für alle anderen Datentypen zurück.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Die maximal mögliche Länge der Eigenschaft (in Byte), wenn es sich um einen Zeichen- oder Binärtyp handelt.<br /><br /> Null gibt an, dass es keine definierte maximale Länge gibt.<br /><br /> Gibt `NULL` für alle anderen Datentypen zurück.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Die maximale Genauigkeit der Eigenschaft, wenn es sich um einen numerischen Datentyp handelt.<br /><br /> Gibt `NULL` für alle anderen Datentypen zurück.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Die Anzahl der Stellen rechts neben dem Dezimalzeichen, wenn es sich um einen `DBTYPE_NUMERIC`- oder `DBTYPE_DECIMAL` Typ handelt.<br /><br /> Gibt `NULL` für alle anderen Datentypen zurück.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung der Eigenschaft. `NULL`, wenn keine Beschreibung vorhanden ist.|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`||Der Typ der Eigenschaft. Dieser kann eine der folgenden Enumerationen sein:<br /><br /> -   **MD_PROPTYPE_REGULAR** (`0x00`)<br />-   **MD_PROPTYPE_ID** (`0x01`)<br />-   **MD_PROPTYPE_RELATION_TO_PARENT** (`0x02`)<br />-   **MD_PROPTYPE_ROLLUP_OPERATOR** (`0x03`)<br />-   **MD_PROPTYPE_ORG_TITLE** (`0x11`)<br />-   **MD_PROPTYPE_CAPTION** (`0x21`)<br />-   **MD_PROPTYPE_CAPTION_SHORT** (`0x22`)<br />-   **MD_PROPTYPE_CAPTION_DESCRIPTION** (`0x23`)<br />-   **MD_PROPTYPE_CAPTION_ABREVIATION** (`0x24`)<br />-   **MD_PROPTYPE_WEB_URL** (`0x31`)<br />-   **MD_PROPTYPE_WEB_HTML** (`0x32`)<br />-   **MD_PROPTYPE_WEB_XML_OR_XSL** (`0x33`)<br />-   **MD_PROPTYPE_WEB_MAIL_ALIAS** (`0x34`)<br />-   **MD_PROPTYPE_ADDRESS** (`0x41`)<br />-   **MD_PROPTYPE_ADDRESS_STREET** (`0x42`)<br />-   **MD_PROPTYPE_ADDRESS_HOUSE** (`0x43`)<br />-   **MD_PROPTYPE_ADDRESS_CITY** (`0x44`)<br />-   **MD_PROPTYPE_ADDRESS_STATE_OR_PROVINCE** (`0x45`)<br />-   **MD_PROPTYPE_ADDRESS_ZIP** (`0x46`)<br />-   **MD_PROPTYPE_ADDRESS_QUARTER** (`0x47`)<br />-   **MD_PROPTYPE_ADDRESS_COUNTRY** (`0x48`)<br />-   **MD_PROPTYPE_ADDRESS_BUILDING** (`0x49`)<br />-   **MD_PROPTYPE_ADDRESS_ROOM** (`0x4A`)<br />-   **MD_PROPTYPE_ADDRESS_FLOOR** (`0x4B`)<br />-   **MD_PROPTYPE_ADDRESS_FAX** (`0x4C`)<br />-   **MD_PROPTYPE_ADDRESS_PHONE** (`0x4D`)<br />-   **MD_PROPTYPE_GEO_CENTROID_X** (`0x61`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Y** (`0x62`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Z** (`0x63`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_TOP** (`0x64`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_LEFT** (`0x65`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_BOTTOM** (`0x66`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_RIGHT** (`0x67`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_FRONT** (`0x68`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_REAR** (`0x69`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_POLYGON** (`0x6A`)<br />-   **MD_PROPTYPE_PHYSICAL_SIZE** (`0x71`)<br />-   **MD_PROPTYPE_PHYSICAL_COLOR** (`0x72`)<br />-   **MD_PROPTYPE_PHYSICAL_WEIGHT** (`0x73`)<br />-   **MD_PROPTYPE_PHYSICAL_HEIGHT** (`0x74`)<br />-   **MD_PROPTYPE_PHYSICAL_WIDTH** (`0x75`)<br />-   **MD_PROPTYPE_PHYSICAL_DEPTH** (`0x76`)<br />-   **MD_PROPTYPE_PHYSICAL_VOLUME** (`0x77`)<br />-   **MD_PROPTYPE_PHYSICAL_DENSITY** (`0x78`)<br />-   **MD_PROPTYPE_PERSON_FULL_NAME** (`0x82`)<br />-   **MD_PROPTYPE_PERSON_FIRST_NAME** (`0x83`)<br />-   **MD_PROPTYPE_PERSON_LAST_NAME** (`0x84`)<br />-   **MD_PROPTYPE_PERSON_MIDDLE_NAME** (`0x85`)<br />-   **MD_PROPTYPE_PERSON_DEMOGRAPHIC** (`0x86`)<br />-   **MD_PROPTYPE_PERSON_CONTACT** (`0x87`)<br />-   **MD_PROPTYPE_QTY_RANGE_LOW** (`0x91`)<br />-   **MD_PROPTYPE_QTY_RANGE_HIGH** (`0x92`)<br />-   **MD_PROPTYPE_FORMATTING_COLOR** (`0xA1`)<br />-   **MD_PROPTYPE_FORMATTING_ORDER** (`0xA2`)<br />-   **MD_PROPTYPE_FORMATTING_FONT** (`0xA3`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_EFFECTS** (`0xA4`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_SIZE** (`0xA5`)<br />-   **MD_PROPTYPE_FORMATTING_SUB_TOTAL** (`0xA6`)<br />-   **MD_PROPTYPE_DATE** (`0xB1`)<br />-   **MD_PROPTYPE_DATE_START** (`0xB2`)<br />-   **MD_PROPTYPE_DATE_ENDED** (`0xB3`)<br />-   **MD_PROPTYPE_DATE_CANCELED** (`0xB4`)<br />-   **MD_PROPTYPE_DATE_MODIFIED** (`0xB5`)<br />-   **MD_PROPTYPE_DATE_DURATION** (`0xB6`)<br />-   **MD_PROPTYPE_VERSION** (`0xC1`)|  
|`SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Der Name der Eigenschaft, die in SQL-Abfragen von der Cubedimension oder Datenbankdimension verwendet wird.|  
|`LANGUAGE`|`DBTYPE_UI2`||Die als `LCID` ausgedrückte Übersetzung. Nur gültig für Eigenschaftenübersetzungen.|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`||Gibt den Typ der Hierarchie an, für die die Eigenschaft gilt:<br /><br /> -   `MD_USER_DEFINED` (`1`) gibt an, dass die Eigenschaft auf eine benutzerdefinierte Hierarchie<br />-   `MD_SYSTEM_ENABLED` (`2`) gibt an, dass die Eigenschaft für eine Attributhierarchie gilt<br />-   `MD_SYSTEM_DISABLED` (`4`) gibt an, dass die Eigenschaft auf die Attributhierarchie nicht aktiviert ist.|  
|`PROPERTY_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||Der Name der Attributhierarchie, die als Quelle für diese Eigenschaft dient.|  
|`PROPERTY_CARDINALITY`|`DBTYPE_WSTR`||Die Kardinalität der Eigenschaft. Die folgenden Zeichenfolgen sind möglich:<br /><br /> -   `ONE`<br />-   `MANY`|  
|`MIME_TYPE`|`DBTYPE_WSTR`||Der MIME-Typ für Binary Large Objects (BLOBs).|  
|`PROPERTY_IS_VISIBLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Eigenschaft sichtbar ist.<br /><br /> `TRUE`, wenn die Eigenschaft sichtbar ist; andernfalls `FALSE`.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_PROPERTIES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Obligatorisch.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional|  
|`PROPERTY_TYPE`|`DBTYPE_I2`|Optional|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`|Optional|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`|(Optional) Eine Standardeinschränkung ist für `MDPROP_MEMBER` ODER `MDPROP_CELL` gültig.|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`|(Optional) Eine Standardeinschränkung ist für `MD_USER_DEFINED` ODER `MD_SYSTEM_ENABLED` gültig.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-CUBE<br />-2-DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
|`PROPERTY_VISIBILITY`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -Visible 1<br />-2 nicht sichtbar<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  