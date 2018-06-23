---
title: ASSL XML-Konventionen | Microsoft Docs
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
helpviewer_keywords:
- whitespace [Analysis Services Scripting Language]
- trailing whitespace
- XSD data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- cardinality [Analysis Services Scripting Language]
- white space [Analysis Services Scripting Language]
- ASSL, XML conventions
- defaults [Analysis Services Scripting Language]
- leading whitespace
- Analysis Services Scripting Language, XML conventions
- XML [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
- inherited defaults [Analysis Services Scripting Language]
ms.assetid: bce4edad-4420-41ce-9672-8c00c5c0dec6
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d0411903c72aba9b0122beb4c0e46e9f172f4f4e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161681"
---
# <a name="assl-xml-conventions"></a>XML-Konventionen in ASSL
  Die Analysis Services Scripting Language (ASSL) stellt die Hierarchie von Objekten als Satz von Elementtypen dar, die jeweils die untergeordneten Elemente definieren, die sie enthalten können.  
  
 Für die Darstellung der Objekthierarchie verwendet ASSL folgende XML-Konventionen:  
  
-   Alle Objekte und Eigenschaften werden als Elemente dargestellt, mit Ausnahme von XML-Standardattributen wie „xml:lang“.  
  
-   Sowohl Elementnamen als auch Enumerationswerte befolgen die Microsoft .NET Framework-Benennungskonvention der Schreibweise von Pascal ohne Unterstriche.  
  
-   Die Groß-/Kleinschreibung aller Werte wird beibehalten. Bei Werten für Enumerationen wird ebenfalls die Groß-/Kleinschreibung unterschieden.  
  
 Zusätzlich zu dieser Konventionsliste werden in Analysis Services bestimmte Konventionen in Bezug auf Kardinalität, Vererbung, Leerzeichen, Datentypen und Standardwerte befolgt.  
  
## <a name="cardinality"></a>Cardinality  
 Wenn ein Element eine Kardinalität besitzt, die größer als 1 ist, wird dieses Element von einer XML-Elementauflistung gekapselt. Der Name der Auflistung verwendet die Pluralform der in der Auflistung enthaltenen Elemente. Das folgende XML-Fragment stellt beispielsweise die `Dimensions` Auflistung innerhalb einer `Database` Element:  
  
 `<Database>`  
  
 `…`  
  
 `<Dimensions>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `</Dimensions>`  
  
 `</Database>`  
  
 ``  
  
 Die Reihenfolge der Elemente ist bedeutungslos.  
  
## <a name="inheritance"></a>Vererbung  
 Die Vererbung wird bei unterschiedlichen Objekten verwendet, die über überlappende, jedoch deutlich unterschiedliche Sätze von Eigenschaften verfügen. Beispiele für derartige überlappende, jedoch unterschiedliche Objekte sind virtuelle Cubes, verknüpfte Cubes und reguläre Cubes. Für überlappende, jedoch unterschiedliche Objekte wird Analysis Services verwendet den Standard `type` Attribut aus der XML-Instanz Namespace, um die Vererbung anzugeben. Das folgende XML-Fragment zeigt, wie das `type`-Attribut ermittelt, ob ein `Cube`-Element von einem regulären Cube oder von einem virtuellen Cube erbt:  
  
 `<Cubes>`  
  
 `<Cube xsi:type=”RegularCube”>`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type=”VirtualCube”>`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 Die Vererbung wird im Allgemeinen nicht verwendet, wenn mehrere Typen eine Eigenschaft mit dem gleichen Namen besitzen. Die `Name`- und die `ID`-Eigenschaft sind beispielsweise auf zahlreichen Elementen vorhanden, diese Eigenschaften wurden jedoch nicht zu einem abstrakten Typ heraufgestuft.  
  
## <a name="whitespace"></a>Leerzeichen  
 Leerzeichen innerhalb eines Elementwerts werden beibehalten. Führende und nachfolgende Leerzeichen werden jedoch immer entfernt. Die folgenden Elemente besitzen beispielsweise den gleichen Text, jedoch eine unterschiedliche Anzahl von Leerzeichen innerhalb dieses Texts, daher werden sie behandelt, als besäßen sie unterschiedliche Werte:  
  
 `<Description>My text<Description>`  
  
 `<Description>My  text<Description>`  
  
 ``  
  
 Die folgenden Elemente unterscheiden sich jedoch nur durch führende und nachfolgende Leerzeichen, daher werden sie behandelt, als besäßen sie die gleichen Werte.  
  
 `<Description>My text<Description>`  
  
 `<Description>  My text  <Description>`  
  
 ``  
  
## <a name="data-types"></a>Datentypen  
 In Analysis Services werden die folgenden XSD-Standarddatentypen (XML Schema Definition Language) verwendet:  
  
 `Int`  
 Ein ganzzahliger Wert im Bereich von -231 bis 231 – 1.  
  
 `Long`  
 Ein ganzzahliger Wert im Bereich von -263 bis 263 – 1.  
  
 `String`  
 Ein Zeichenfolgenwert, der den folgenden allgemeinen Regeln entspricht:  
  
-   Steuerzeichen werden entfernt.  
  
-   Führende und nachfolgende Leerzeichen werden entfernt.  
  
-   Interne Leerzeichen werden beibehalten.  
  
 `Name` und `ID` -Eigenschaft besitzen spezielle Beschränkungen für gültige Zeichen in Zeichenfolgenelementen. Weitere Informationen zu `Name` und `ID` Konventionen, finden Sie unter [ASSL-Objekte und-Objekteigenschaften](assl-objects-and-object-characteristics.md).  
  
 `DateTime`  
 Ein `DateTime` -Struktur von .NET Framework. Ein `DateTime`-Wert darf nicht NULL sein. Die niedrigste Datum von unterstützt die `DataTime` -Datentyp wird dem 1. Januar 1601 steht für Programmierer als `DateTime.MinValue`. Das früheste unterstützte Datum gibt an, dass ein `DateTime` Wert ist nicht vorhanden.  
  
 `Boolean`  
 Eine Enumeration mit nur zwei Werten wie {true, false} oder {0, 1}.  
  
## <a name="default-values"></a>Standardwerte  
 Analysis Services verwendet die in der folgenden Tabelle aufgelisteten Standardwerte:  
  
|XML-Datentyp|Standardwert|  
|-------------------|-------------------|  
|`Boolean`|False|  
|`String`|"" (leere Zeichenfolge)|  
|`Integer` oder `Long`|0 (Null)|  
|`Timestamp`|12:00:00 Uhr, 1/1/0001 (entsprechend einer .NET Framework-Versionen `System.DateTime` mit 0 Takten)|  
  
 Eine Element, das vorhanden, jedoch leer ist, wird interpretiert, als hätte es den Wert einer NULL-Zeichenfolge, nicht den Standardwert.  
  
### <a name="inherited-defaults"></a>Geerbte Standards  
 Einige auf einem Objekt angegebene Eigenschaften stellen Standardwerte für die gleiche Eigenschaft auf untergeordneten oder nachfolgenden Objekten bereit. Beispielsweise stellt `Cube.StorageMode` den Standardwert für `Partition.StorageMode` bereit. Folgende Regeln werden von Analysis Services auf geerbte Standardwerte angewendet:  
  
-   Wenn die Eigenschaft für das untergeordnete Objekt in XML NULL ist, nimmt ihr Wert standardmäßig den geerbten Wert an. Wenn Sie den Wert jedoch vom Server abfragen, gibt der Server den NULL-Wert des XML-Elements zurück.  
  
-   Es ist nicht möglich, programmgesteuert festzustellen, ob die Eigenschaft eines untergeordneten Objekts direkt auf dem untergeordneten Objekt festgelegt oder geerbt wurde.  
  
 Einige Elemente besitzen definierte Standards, die gelten, wenn das Element fehlt. Beispielsweise entsprechen sich die `Dimension`-Elemente in den folgenden XML-Fragmenten, obwohl ein `Dimension`-Element ein `Visible`-Element enthält, das andere `Dimension`-Element jedoch nicht.  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 Weitere Informationen zu geerbten Standards finden Sie unter [ASSL-Objekte und-Objekteigenschaften](assl-objects-and-object-characteristics.md).  
  
  