---
title: Datentypen in Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 910be4f4-3010-41cd-9fdc-f0a79a0ce823
author: minewiskan
ms.author: owend
ms.openlocfilehash: 06b93090918a0fffc9c98e1560b338177eff3d84
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545928"
---
# <a name="data-types-in-analysis-services"></a>Datentypen in Analysis Services
  Bei allen- <xref:Microsoft.AnalysisServices.DataItem> Objekten [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt die folgende Teilmenge von `System.Data.OleDb.OleDbType` . Um den Datentyp festzulegen oder zu lesen, verwenden Sie den [DataItem-Datentyp &#40;ASSL-&#41;](https://docs.microsoft.com/bi-reference/assl/data-type/dataitem-data-type-assl).  
  
## <a name="supported-data-types"></a>Unterstützte Datentypen  
  
|||  
|-|-|  
|BigInt|Ein 64-Bit-Integer mit Vorzeichen Der *bigint* -Werttyp stellt ganze Zahlen dar, deren Werte zwischen negativer 9.223.372.036.854.775.808 und positiv 9.223.372.036.854.775.807 liegen.|  
|Binary|Ein Datenstrom von Binärdaten des **bytetyps** . **Byte** ist ein Werttyp, der ganze Zahlen ohne Vorzeichen mit Werten zwischen 0 und 255 darstellt.|  
|Boolesch|Instanzen dieses Typs weisen den Wert `true` oder `false` auf.|  
|Währung|Ein *Währungs* Wert im Bereich von-922.337.203.685.477,5808 bis + 922.337.203.685.477,5807 mit einer Genauigkeit von einem Zehntausendstel einer Währungseinheit (vier Dezimalstellen).|  
|Date|Datum und Uhrzeitdaten, die als double-Wert gespeichert werden. Der ganzzahlige Teil gibt die Anzahl von Tagen seit dem 30. Dezember 1899 wieder, während der Bruchteil ein Teil eines Tages oder die Tageszeit ist.|  
|Double|Eine Gleitkommazahl im Bereich von -1,79769313486232E +308 bis 1,79769313486232E +308. Ein double-Wert speichert Informationen zur Zahl mit einer Genauigkeit von bis zu 15 Dezimalstellen.|  
|Integer|Eine 32-Bit-Ganzzahl mit Vorzeichen, die ganze Zahlen mit Vorzeichen darstellt, die zwischen -2.147.483.648 und +2.147.483.647 liegen.|  
|Single|Eine Gleitkommazahl im Bereich von -3,4028235E +38 bis 3,4028235E +38. Ein single-Wert speichert Informationen zur Zahl mit einer Genauigkeit von bis zu 7 Dezimalstellen.|  
|Smallint|Eine 16-Bit-Ganzzahl mit Vorzeichen. Der *smallint* -Werttyp stellt ganze Zahlen mit Vorzeichen dar, deren Werte zwischen negativer 32768 und positiv 32767 liegen.|  
|Tinyint|Eine 8-Bit-Ganzzahl mit Vorzeichen. Der Tinyint-Werttyp stellt Ganzzahlen dar, die zwischen -128 und +127 liegen.|  
|UnsignedBigInt|Eine 64-Bit-Ganzzahl ohne Vorzeichen. Der *UnsignedBigInt* -Werttyp stellt Ganzzahlen ohne Vorzeichen mit Werten zwischen 0 und 18446744073709551615 dar.|  
|UnsignedInt|Eine 32-Bit-Ganzzahl ohne Vorzeichen. Der *unsignetdint* -Werttyp stellt Ganzzahlen ohne Vorzeichen mit Werten zwischen 0 und 4.294.967.295 dar.|  
|UnsignedSmallInt|Eine 16-Bit-Ganzzahl ohne Vorzeichen. Der *UnsignedSmallInt* -Werttyp stellt Ganzzahlen ohne Vorzeichen mit Werten zwischen 0 und 65535 dar.|  
|UnsignedTinyInt|Eine 8-Bit-Ganzzahl ohne Vorzeichen. Der *UnsignedTinyInt* -Werttyp stellt Ganzzahlen ohne Vorzeichen mit Werten zwischen 0 und 255 dar.|  
|WChar|Ein mit NULL endender Datenstrom von Unicode-Zeichen. Ein *WCHAR* ist eine sequenzielle Sammlung von Unicode-Zeichen, die zum Darstellen von Text verwendet wird.|  
  
## <a name="amo-validations-on-data-types"></a>AMO-Überprüfungen von Datentypen  
 In der folgenden Tabelle sind die zusätzlichen Überprüfungen aufgelistet, die AMO (Analysis Management Objects) für bestimmte Bindungen ausführt:  
  
|Object|Bindung|Zulässige Datentypen|  
|------------|-------------|------------------------|  
|DimensionAttribute|KeyColumns|Alle bis auf Binary|  
||NameColumn|Nur WChar|  
||SkippedLevelsColumn|Nur ganzzahlige Datentypen: BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
||CustomRollupColumn|Nur WChar|  
||CustomRollupPropertiesColumn|Nur WChar|  
||UnaryOperatorColumn|Nur WChar|  
||ValueColumn|All|  
|AttributeTranslation|CaptionColumn|Nur WChar|  
|ScalarMiningStructureColumn|KeyColumns|Alle bis auf Binary|  
||NameColumn|Nur WChar|  
|TableMiningStructureColumn|ForeignKeyColumns|Alle bis auf Binary|  
|MeasureGroupAttribute|KeyColumns|Alle bis auf Binary|  
|Distinct Count Measure|`Source`|BigInt, Currency, Double, Integer, Single, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
  
  
