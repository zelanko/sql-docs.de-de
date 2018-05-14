---
title: Axes-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 02b9c91f30c45e59d0f5eba00a5b76262070d711
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="axes-element-xmla"></a>Axes-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Auflistung von [Achse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) Elemente Achsendaten enthalten sind, eine [Root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) Element, das verwendet die [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) -Datentyp.  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Any|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Stamm](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Untergeordnete Elemente|[Achse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Unter den **Achsen** Element, das **Achse** Elemente in der Reihenfolge im Dataset, beginnend mit NULL Auftretens aufgeführt sind. Die **AxisFormat** XMLA-eigenschafteneinstellung bestimmt wie **Achse** -Elemente formatiert werden. Weitere Informationen zu den **AxisFormat** Eigenschaft finden Sie unter [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
|Element|Eine Auflistung von **Member** Objekte aus der gleichen Dimensionshierarchie.|  
|Tupel|Eine Auflistung von Elementen anderer Dimensionshierarchien.|  
|Tupel|Eine Auflistung von **Tupel** Objekte mit der gleichen Dimensionalität.|  
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
  
 Kann ein Client verwenden die **AxisFormat** Eigenschaft, um eine bestimmte Darstellung anzufordern.  
  
## <a name="see-also"></a>Siehe auch  
 [MDDataSet-Datentyp & #40; XMLA & #41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
