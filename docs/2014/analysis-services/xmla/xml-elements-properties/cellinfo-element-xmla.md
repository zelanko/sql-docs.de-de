---
title: CellInfo-Element (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CellInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cellinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#CellInfo
- urn:schemas-microsoft-com:xml-analysis#CellInfo
helpviewer_keywords:
- CellInfo element
ms.assetid: 8b6420f1-e9a7-4975-b580-1439fa11f5ca
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 803640fe83ccc3137b4597b8c1b78850abeb55c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061676"
---
# <a name="cellinfo-element-xmla"></a>CellInfo-Element (XMLA)
  Stellt die Zellmetadaten dar, die das übergeordnete [OlapInfo](olapinfo-element-xmla.md) -Element enthält.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<OlapInfo>  
   ...  
   <CellInfo>  
      <!-- One or more cell property definitions -->  
   </CellInfo>  
   ...  
</OlapInfo>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[OlapInfo](olapinfo-element-xmla.md)|  
|Untergeordnete Elemente|Eine oder mehrere Definitionen der Zelleneigenschaften|  
  
## <a name="remarks"></a>Hinweise  
 Die `CellInfo` Element enthält eine Auflistung der Zelleneigenschaften der Zellen, die in dem multidimensionalen Datensatz zurückgegeben wird, indem Sie aus einer `root` Element mit der `MDDataSet` -Datentyp. Jede Zelleneigenschaft in dem `CellInfo`-Element wird durch ein einzelnes XML-Element definiert, das jeweils ein `name`-Attribut und ein `type`-Attribut enthält. Das `name`-Attribut der Zelleneigenschaft entspricht dem Namen der OLE DB für die OLAP-Zelleneigenschaft, die durch das XML-Element dargestellt wird; das `type`-Attribut stellt den XML-Datentyp der Zelleneigenschaft dar. Der Name des XML-Elements wird verwendet, um den Wert der Zelleneigenschaft der Zellen zu identifizieren, die in dem `CellData`-Element des `root`-Elements enthalten sind.  
  
 Die folgende Syntax beschreibt die Definition einer Zelleneigenschaft:  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 Die verfügbaren Eigenschaften und ihre Werte können mithilfe des Anforderungstyps DISCOVER_PROPERTIES mit abgerufen werden die `Discover` Methode. Es gibt keine erforderliche Reihenfolge für die im `PropertyList`-Element aufgelisteten Eigenschaften.  
  
 Ein Anbieter kann optional angeben von Standardwerten für einzelne Elemente oder Zelleneigenschaften im die `AxisInfo` oder `CellInfo` Abschnitt. Die Standardwerte können für eine kleinere Ergebnismenge sorgen, wenn die Eigenschaft immer oder fast immer den gleichen Wert hat. Um einen Standardwert für eine Eigenschaft anzugeben, die`Default` Element kann optional als untergeordnetes Element von einem der Zelleneigenschaften-Definitionselemente angegeben werden. Das Fehlen eines Elements oder einer Zelleneigenschaft im Ergebnis deutet daher darauf hin, dass der angegebene Standardwert der Wert der Zelleneigenschaft ist.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird veranschaulicht, wie die Zelleneigenschaften VALUE, FORMATTED_VALUE und FORMAT_STRING dargestellt werden, in dem `CellInfo` Element.  
  
```  
<OlapInfo>  
   ...  
      <CellInfo>  
         <Value name="VALUE"></Value>  
         <FmtValue name="FORMATTED_VALUE"></FmtValue>  
         <FormatString name="FORMAT_STRING"></FormatString>  
      </CellInfo>  
</OlapInfo>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  