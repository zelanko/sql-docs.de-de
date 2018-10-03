---
title: DMSCHEMA_MINING_STRUCTURE_COLUMNS-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_STRUCTURE_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURE_COLUMNS rowset
ms.assetid: 81f25502-ac90-42f1-8ddf-7b0f9752ebfd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c012515df76b1f19712c5bf1ba828dafdc787ef7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088370"
---
# <a name="dmschemaminingstructurecolumns-rowset"></a>DMSCHEMA_MINING_STRUCTURE_COLUMNS-Rowset
  Beschreibt die einzelnen Spalten aller Miningstrukturen, die auf einem Server, auf denen ausgeführt wird, wird bereitgestellt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_STRUCTURE_COLUMNS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`||Der Katalogname.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`||Der nicht gekennzeichnete Schemaname. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt keine Schemas, deshalb ist diese Spalte immer `NULL`.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`||Der Name der Struktur. Diese Spalte darf nicht enthalten. ein `NULL`.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Name der Spalte. Eindeutigkeit wird nur für Spalten garantiert, die das gleiche Muster besitzen. Beispielsweise können zwei geschachtelte Spalten den gleichen Namen besitzen, wenn sie zu zwei unterschiedlichen geschachtelten Tabellen innerhalb der gleichen Struktur gehören.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||Der Spalten-GUID Anbieter, die keine GUIDs zur Identifizierung von Spalten verwenden, sollten `NULL` in dieser Spalte zurückgeben.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||Die Spalteneigenschaften-ID. Anbieter, die Spalten keine Eigenschaften-IDs zuordnen, müssen in dieser Spalte `NULL` zurückgeben. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Gibt `NULL` für diese Spalte.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Die Ordnungszahl der Spalte. Spalten werden beginnend mit 1 nummeriert. `NULL`, wenn kein stabiler Ordinalwert für die Spalte vorhanden ist.|  
|`COLUMN_HASDEFAULT`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob diese Spalte einen Standardwert besitzt.<br /><br /> Ist `TRUE`, wenn die Spalte einen Standardwert besitzt.<br /><br /> Ist `FALSE`, wenn die Spalte keinen Standardwert besitzt oder wenn nicht bekannt ist, ob die Spalte einen Standardwert besitzt.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Der Standardwert der Spalte. Ein Anbieter kann in dem von `DBCOLUMN_DEFAULTVALUE` zurückgegebenen Rowset `DBCOLUMN_HASDEFAULT` verfügbar machen, jedoch nicht `IColumnsRowset::GetColumnsRowset` (für ISO-Tabellen).<br /><br /> Wenn der Standardwert `NULL` ist, wird für `COLUMN_HASDEFAULT` `TRUE` festgelegt und die `COLUMN_DEFAULT`-Spalte besitzt einen `NULL`-Wert.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||– Eine Bitmaske, die Spaltenmerkmale beschreibt. Der Enumerationstyp `DBCOLUMNFLAGS` legt die Bits in dieser Bitmaske fest. Diese Spalte darf keinen `NULL`-Wert enthalten. Gültige Werte sind:<br />-   **DBCOLUMNFLAGS_ISNULLABLE** (`0x20`)<br />-   **DBCOLUMNFLAGS_MAYBENULL** (`0x40`)<br />-   **DBCOLUMNFLAGS_ISLONG** (`0x80`)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob diese Spalte einen Standardwert besitzt.<br /><br /> `TRUE`, wenn die Spalte `NULL` enthalten kann, andernfalls `FALSE`.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Der Zähler des Datentyps der Spalte. Zum Beispiel:<br /><br /> -   "`TABLE`" = `DBTYPE_HCHAPTER`<br />-   "`TEXT`" = `DBTYPE_WCHAR`<br />-   "`LONG`" = `DBTYPE_I8`<br />-   "`DOUBLE`" = `DBTYPE_R8`<br />-   "`DATE`" = `DBTYPE_DATE`|  
|`TYPE_GUID`|`DBTYPE_GUID`||Der GUID des Datentyps der Spalte. Anbieter, die keine GUIDs zur Identifizierung von Datentypen verwenden, sollten `NULL` in dieser Spalte zurückgeben.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Die maximal mögliche Länge eines Werts in der Spalte. Für Zeichen-, Binär- oder Bitspalten gelten folgende Werte:<br /><br /> – Die maximale Länge der Spalte in Zeichen, Bytes oder Bits, wenn die Länge definiert ist. Eine `CHAR(5)`-Spalte in einer SQL-Tabelle besitzt beispielsweise eine maximale Länge von 5.<br />– Die maximale Länge der Daten geben in Zeichen, Bytes oder Bits, bzw., wenn die Spalte keine definierte Länge besitzt.<br />-0 (null), wenn weder die Spalte noch der Datentyp eine definierte Maximallänge besitzt.<br />-   `NULL` für alle anderen Spaltentypen.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Die maximale Länge der Spalte in Oktetten (Bytes), wenn der Spaltentyp Zeichen oder Binär ist. Ein Wert von 0 (null) bedeutet die Spalte keine maximale Länge verfügt. `NULL` für alle anderen Spaltentypen.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Die maximale Genauigkeit der Spalte, wenn die Spalte einen anderen numerischen Datentyp als `VARNUMERIC` besitzt. `NULL`, wenn der Datentyp der Spalte nicht numerisch oder `VARNUMERIC` ist.<br /><br /> Die Genauigkeit von Spalten mit dem Datentyp `DBTYPE_DECIMAL` oder `DBTYPE_NUM`ERIC hängt von der Definition der Spalte.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Die Anzahl der Stellen rechts neben dem Dezimalzeichen, wenn der Typindikator der Spalte `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC` oder `DBTYPE_VARNUMERIC` ist. Andernfalls ist `NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Die DateTime-Genauigkeit (die Anzahl der Stellen im Bereich der Sekundenbruchteile) der Spalte, wenn die Spalte den Datentyp "Datetime" oder "Intervall" besitzt. Wenn der Datentyp der Spalte nicht "Datetime" ist, ist der Wert `NULL`.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Der Name des Katalogs, in dem der Zeichensatz definiert ist. `NULL`, wenn der Anbieter keine Kataloge oder anderen Zeichensätze unterstützt.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Der nicht qualifizierte Schemaname, in dem der Zeichensatz definiert ist. `NULL`, wenn der Anbieter keine Schemas oder anderen Zeichensätze unterstützt.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Der Zeichensatzname. `NULL`, wenn der Anbieter keine anderen Zeichensätze unterstützt.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Der Name des Katalogs, in dem die Sortierung definiert ist. `NULL`, wenn der Anbieter keine Kataloge oder anderen Sortierungen unterstützt.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Der nicht qualifizierte Schemaname, in dem die Sortierung definiert ist. `NULL`, wenn der Anbieter keine Schemas oder anderen Sortierungen unterstützt.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Der Sortierungsname. `NULL`, wenn der Anbieter keine anderen Sortierungen unterstützt.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Der Name des Katalogs, in dem die Domäne definiert ist. `NULL`, wenn der Anbieter keine Kataloge oder Domänen unterstützt.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Nicht gekennzeichneter Name des Schemas, in dem das Objekt definiert ist. `NULL`, wenn der Anbieter keine Schemas oder Domänen unterstützt.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Der Domänenname. `NULL`, wenn der Anbieter keine Domänen unterstützt.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung der Spalte. `NULL`, wenn keine der Spalte zugeordnete Beschreibung vorhanden ist.|  
|`DISTRIBUTION_FLAG`|`DBTYPE_WSTR`||Die Verteilung der Miningstrukturspalte:<br /><br /> -   "`NORMAL`"<br />-"`LOG_NORM`AL"<br />-   "`UNIFORM`"|  
|`CONTENT_TYPE`|`DBTYPE_WSTR`||Der Inhaltstyp der Miningstrukturspalte:<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-"`DISCRETIZED(`[Args]`)`"<br />-   "`ORDERED`"<br />-   "`SEQUENCE_TIME`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY_VARIANCE`"<br />-   "`PROBABILITY_STDEV`"|  
|`MODELING_FLAG`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Modellierungsflags. Das einzige unterstützte Flag einer Strukturspalte ist `NOT NULL`.|  
|`IS_RELATED_TO_KEY`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob diese Spalte zu dem Schlüssel gehört.<br /><br /> `VARIANT_TRUE` Wenn diese Spalte mit dem Schlüssel verbunden ist `VARIANT_FALSE` andernfalls. Wenn der Schlüssel eine einzelne Spalte, die `RELATED_ATTRIBUTE` Feld kann optional seinen Spaltennamen enthalten.|  
|`RELATED_ATTRIBUTE`|`DBTYPE_WSTR`||Der Name der Zielspalte, der die aktuelle Spalte zugeordnet ist oder von der sie eine spezielle Eigenschaft ist.|  
|`CONTAINING_COLUMN`|`DBTYPE_WSTR`||Der Name des der `TABLE` Spalte, die diese Spalte enthält. `NULL`, wenn die Spalte in keiner Tabelle enthalten ist.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob diese Spalte einen Satz von möglichen Werten erfasst hat.<br /><br /> `TRUE`, wenn die Spalte einen Satz möglicher Werte erfasst hat, andernfalls `FALSE`.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DMSCHEMA_MINING_STRUCTURE_COLUMNS` Rowset kann auf die Spalten in der folgenden Tabelle eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`|Optional.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`|Optional.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
