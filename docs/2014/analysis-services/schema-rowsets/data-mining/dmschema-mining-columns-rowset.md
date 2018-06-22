---
title: DMSCHEMA_MINING_COLUMNS Rowset | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_COLUMNS rowset
ms.assetid: ae35ccde-4438-46f4-8611-40b2b1a42fce
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d53285b088b471ad7a5fca87536cc897db8126d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149749"
---
# <a name="dmschemaminingcolumns-rowset"></a>DMSCHEMA_MINING_COLUMNS-Rowset
  Beschreibt die einzelnen Spalten aller Datamining-Modellen in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Dieses Rowset wird auf den aktuellen Katalog eingeschränkt.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_COLUMNS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Der Katalogname. Wird mit dem Namen der Datenbank aufgefüllt, von der das Modell ein Element ist.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Der nicht gekennzeichnete Schemaname. Die Spalte wird von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Der Miningmodellname. Diese Spalte enthält den Namen des Miningmodells, dem eine Spalte zugeordnet ist. Sie ist niemals leer.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Name der Spalte.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||Der Spalten-GUID Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||Die Spalteneigenschaften-ID. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Die Ordnungsposition der Spalte. Spalten werden beginnend mit 1 nummeriert. Die Spalte enthält `NULL`, wenn kein stabiler Ordinalwert für die Spalte vorhanden ist.|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Spalte einen Standardwert besitzt.<br /><br /> Ist `TRUE`, wenn die Spalte einen Standardwert besitzt, andernfalls `FALSE`.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Der Standardwert der Spalte.<br /><br /> Wenn der Standardwert der `NULL`-Wert ist, enthält `COLUMN_HASDEFAULT` `TRUE`, und diese Spalte enthält `NULL`.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||Eine Bitmaske, die die Eigenschaften der Spalte beschreibt. Der Enumerationstyp `DBCOLUMNFLAGS` legt die Bits in dieser Bitmaske fest. Diese Spalte ist niemals leer.|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob in dieser Spalte NULL zulässig ist.<br /><br /> Der Wert ist `FALSE`, wenn bekannt ist, dass NULL in der Spalte zulässig ist, andernfalls `TRUE`.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Der Zähler des Datentyps der Spalte. Die folgende Liste zeigt Beispiele der zurückgegebenen Indikatortypen:<br /><br /> `TABLE` würde `DBTYPE_HCHAPTER` zurückgeben.<br /><br /> `TEXT` würde `DBTYPE_WCHAR` zurückgeben.<br /><br /> `LONG` würde `DBTYPE_I8` zurückgeben.<br /><br /> `DOUBLE` würde `DBTYPE_R8` zurückgeben.<br /><br /> `DATE` würde `DBTYPE_DATE` zurückgeben.|  
|`TYPE_GUID`|`DBTYPE_GUID`||Der GUID des Datentyps der Spalte. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `VT_NULL`.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Die maximal mögliche Länge eines Werts in der Spalte. Für Zeichen-, Binär- oder Bitspalten gelten folgende Werte:<br /><br /> – Die maximale Länge der Spalte in Zeichen, Bytes oder Bits, je nach Spaltentyp, wenn eine Länge definiert ist. Eine `CHAR(5)`-Spalte in einer SQL-Tabelle besitzt beispielsweise eine maximale Länge von 5.<br />– Die maximale Länge des Datentyps in Zeichen, Bytes oder Bits, je nach Spaltentyp, wenn die Spalte keine definierte Länge besitzt.<br />-0 (null), wenn weder die Spalte noch der Datentyp eine definierte Maximallänge besitzt.<br />-   `NULL` für alle anderen Typen von Spalten|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Die maximale Länge der Spalte in Oktetten (Bytes), wenn der Spaltentyp Zeichen oder Binär ist. Der Wert 0 (null) bedeutet, dass die Spalte keine maximale Länge verfügt. Die Spalte enthält `NULL` für alle anderen Spaltentypen.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Die maximale Genauigkeit der Spalte, wenn die Spalte einen anderen numerischen Datentyp als `VARNUMERIC` besitzt.<br /><br /> `NULL`, wenn der Datentyp der Spalte nicht "Numerisch" ist oder `VARNUMERIC` ist.<br /><br /> Die Genauigkeit von Spalten mit dem Datentyp `DBTYPE_DECIMAL` oder `DBTYPE_NUMERIC` ist von der Definition der Spalte abhängig.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Die Anzahl der Stellen rechts neben dem Dezimalzeichen, wenn der Typindikator der Spalte `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC` oder `DBTYPE_VARNUMERIC` ist. Andernfalls enthält diese Spalte `VT_NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Die Datum-/Uhrzeit-Genauigkeit (die Anzahl der Stellen im Bereich der Sekundenbruchteile) der Spalte, wenn die Spalte den Datentyp "DateTime" oder "Intervall" besitzt, andernfalls ist der Wert `NULL`.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Der Name des Katalogs, in dem der Zeichensatz definiert ist. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Der nicht gekennzeichnete Schemaname, in dem der Zeichensatz definiert ist. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Der Zeichensatzname. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Der Name des Katalogs, in dem die Sortierung definiert ist. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Der nicht gekennzeichnete Schemaname, in dem die Sortierung definiert ist. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Der Sortierungsname. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Der Name des Katalogs, in dem die Domäne definiert ist. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Nicht gekennzeichneter Name des Schemas, in dem das Objekt definiert ist. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Der Domänenname. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung der Spalte. Diese Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`DISTRIBUTION_FLAG`|`DBTYPE_WSTR`||Eine Beschreibung der statistischen Verteilung der Spalte. Diese Spalte enthält einen der folgenden Werte:<br /><br /> -   "`NORMAL`"<br />-   "`LOG_NORMAL`"<br />-   "`UNIFORM`"|  
|`CONTENT_TYPE`|`DBTYPE_WSTR`||Eine Beschreibung des Spalteninhalts. Diese Spalte enthält einen der folgenden Werte:<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-"`DISCRETIZED(`[Argumente]`)`"<br />-   "`ORDERED`"<br />-   "`KEY TIME`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY_VARIANCE`"<br />-   "`PROBABILITY_STDEV`"<br />-   `"KEY SEQUENCE`"|  
|`MODELING_FLAG`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Flags. Folgende Flags werden definiert:<br /><br /> -   "`MODEL_EXISTENCE_ONLY`"<br />-   "`REGRESSOR`"<br /><br /> Diese Spalte kann auch ein algorithmusspezifisches Modellierungsflag enthalten.|  
|`IS_RELATED_TO_KEY`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Spalte zum Schlüssel gehört.<br /><br /> Der Wert ist `TRUE`, wenn diese Spalte zum Schlüssel gehört. Wenn der Schlüssel eine einzelne Spalte ist, kann das `RELATED_ATTRIBUTE`-Feld optional seinen Spaltennamen enthalten.|  
|`RELATED_ATTRIBUTE`|`DBTYPE_WSTR`||Der Name der Zielspalte, die die aktuelle Spalte bezieht oder ist eine spezielle Eigenschaft.|  
|`IS_INPUT`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Spalte eine Eingabespalte ist.<br /><br /> Der Wert ist `VARIANT_TRUE`, wenn dies eine Eingabespalte ist.|  
|`IS_PREDICTABLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Spalte vorhersagbar ist.<br /><br /> Der Wert ist `TRUE`, wenn die Spalte vorhersagbar ist.|  
|`CONTAINING_COLUMN`|`DBTYPE_WSTR`||Der Name der `TABLE`-Spalte, die diese Spalte enthält. Die Spalte enthält `NULL`, wenn die Spalte nicht in einer anderen Spalte enthalten ist.|  
|`PREDICTION_SCALAR_FUNCTIONS`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Skalarfunktionen, die auf die Spalte angewendet werden können.|  
|`PREDICTION_TABLE_FUNCTIONS`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Funktionen, die auf die Spalte angewendet werden können. Die Funktionen sollten eine Tabelle zurückgeben. Die Liste weist folgendes Format auf:<br /><br /> `<function name>(<column1> [, <column2>], ...)`<br /><br /> Das Format ermöglicht der Clientanwendung, die Signatur (Liste der Parameter) für die jeweilige Funktion zu bestimmen.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Spalte mit einem Satz möglicher Werten trainiert wurde.<br /><br /> Der Wert ist `TRUE`, wenn die Spalte mit einen Satz möglicher Werte trainiert wurde.<br /><br /> Enthält `FALSE`, wenn die Spalte nicht aufgefüllt ist.|  
|`PREDICTION_SCORE`|`DBTYPE_R8`||Das Ergebnis des Modells bei der Vorhersage der Spalte. Das Ergebnis wird verwendet, um die Genauigkeit des Modells zu messen.|  
|`SOURCE_COLUMN`|`DBTYPE_WSTR`||Der Name der Quellminingstruktur-Spalte für die aktuelle Miningspalte.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DMSCHEMA_MINING_COLUMNS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Optional.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  