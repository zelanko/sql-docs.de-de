---
title: Axes-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Axes Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords:
- Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bdb5aa48dd3a65f99b424274fdb89b3aee8c9591
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094906"
---
# <a name="axes-element-xmla"></a>Axes-Element (XMLA)
  Enthält eine Auflistung von [Achse](axis-element-xmla.md) Elemente Daten enthalten sind, eine [Stamm](root-element-xmla.md) -Element, das verwendet die [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) -Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <Axes>  
      <Axis>...</Axis>  
   </Axes>  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Any|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Stammverzeichnis](root-element-xmla.md)|  
|Untergeordnete Elemente|[Axis](axis-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Unter dem `Axes`-Element sind die `Axis`-Elemente in der Reihenfolge aufgelistet, in der sie im Dataset auftreten, beginnend mit null. Die `AxisFormat`-XMLA-Eigenschafteneinstellung bestimmt, wie `Axis`-Elemente formatiert werden. Weitere Informationen zu den `AxisFormat` -Eigenschaft finden Sie unter [unterstützte XMLA-Eigenschaften &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
 Eine Achse stellt eine Menge von Tupeln dar, in der alle Tupel die gleiche Dimensionalität aufweisen. Eine Menge kann auf verschiedene Weisen dargestellt werden, die unterschiedliche Vorteile bieten. Beispielsweise kann die folgende Menge aus vier Tupeln als Auflistung zweidimensionaler Tupel oder als kartesisches Produkt zweidimensionaler Mengen dargestellt werden.  
  
|1999|1999|2000|2000|  
|----------|----------|----------|----------|  
|Tatsächlich|Budget|Tatsächlich|Budget|  
  
 Diese Menge aus Tupeln kann als Auflistung zweidimensionaler Tupel dargestellt werden:  
  
```  
{ ( 1999, Actual ), ( 1999, Budget ), ( 2000, Actual ), ( 2000, Budget ) }  
```  
  
 Diese Menge kann auch als kartesisches Produkt zwei eindimensionaler Mengen dargestellt werden:  
  
```  
{ 1999, 2000 } x { Actual, Budget }  
```  
  
 Die erste Darstellung, zweidimensionale Tupel, ist für die Verwendung durch Clienttools besser geeignet. Die zweite Darstellung, ein kartesisches Produkt eindimensionaler Mengen, verbraucht weniger Speicherplatz und erhält die mehrdimensionale Eigenschaft der Menge.  
  
 In der folgenden Tabelle sind Vorgänge aufgelistet, die zum Definieren und Charakterisieren der Struktur und der Elemente einer Achse verwendet werden können.  
  
|Vorgang|Description|  
|---------------|-----------------|  
|Member|Die kleinste Einheit einer Achse, die das Element einer Dimensionshierarchie darstellt.|  
|Member|Eine Auflistung von `Member`-Objekten der gleichen Dimensionshierarchie.|  
|Tupel|Eine Auflistung von Elementen anderer Dimensionshierarchien.|  
|Tupel|Eine Auflistung von `Tuple`-Objekten mit der gleichen Dimensionalität.|  
|Union|Eine Vereinigung von Sätzen.|  
|CrossJoin|Ein kartesisches Produkt von Mengen.|  
  
 Diese Vorgänge übersetzen die zweidimensionalen Tupel und das kartesische Produkt eindimensionaler Mengen wie folgt:  
  
## <a name="two-dimensional-tuples"></a>Zweidimensionale Tupel  
  
```  
Tuples (  
   Tuple( Member(1999), Member(Actual) ),  
   Tuple( Member(1999), Member(Budget) ),  
   Tuple( Member(2000), Member(Actual) ),  
   Tuple( Member(2000), Member(Budget) )  
```  
  
## <a name="cartesian-product-of-one-dimensional-sets"></a>Kartesisches Produkt eindimensionaler Mengen  
  
```  
CrossProduct (  
   Members( Member(1999), Member(2000) ),  
   Members( Member(Actual), Member(Budget) )  
```  
  
 Ein Client kann die `AxisFormat`-Eigenschaft verwenden, um eine bestimmte Darstellung anzufordern.  
  
## <a name="see-also"></a>Siehe auch  
 [MDDataSet-Datentyp &#40;XMLA&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
