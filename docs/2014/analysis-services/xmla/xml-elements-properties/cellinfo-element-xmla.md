---
title: CellInfo-Element (XMLA) | Microsoft-Dokumentation
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fda3576bb50314c28dd01474e576ff2b5b333cb8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176387"
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
 Die `CellInfo` Element enthält eine Auflistung der Zelleneigenschaften der Zellen enthalten, in dem multidimensionalen Datensatz zurückgegeben werden, indem eine `root` Element mit der `MDDataSet` -Datentyp. Jede Zelleneigenschaft in dem `CellInfo`-Element wird durch ein einzelnes XML-Element definiert, das jeweils ein `name`-Attribut und ein `type`-Attribut enthält. Das `name`-Attribut der Zelleneigenschaft entspricht dem Namen der OLE DB für die OLAP-Zelleneigenschaft, die durch das XML-Element dargestellt wird; das `type`-Attribut stellt den XML-Datentyp der Zelleneigenschaft dar. Der Name des XML-Elements wird verwendet, um den Wert der Zelleneigenschaft der Zellen zu identifizieren, die in dem `CellData`-Element des `root`-Elements enthalten sind.  
  
 Die folgende Syntax beschreibt die Definition einer Zelleneigenschaft:  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 Die verfügbaren Eigenschaften und deren Werte erhalten Sie mithilfe des Anforderungstyps DISCOVER_PROPERTIES mit der `Discover` Methode. Es gibt keine erforderliche Reihenfolge für die im `PropertyList`-Element aufgelisteten Eigenschaften.  
  
 Ein Anbieter kann optional angeben von Standardwerten für einzelne Elemente oder Zelleneigenschaften im der `AxisInfo` oder `CellInfo` Abschnitt. Die Standardwerte können für eine kleinere Ergebnismenge sorgen, wenn die Eigenschaft immer oder fast immer den gleichen Wert hat. An einen Standardwert für eine Eigenschaft, die`Default` -Element optional als untergeordnetes Element eines der Zelleneigenschaften-Definitionselemente angegeben werden. Das Fehlen eines Elements oder einer Zelleneigenschaft im Ergebnis deutet daher darauf hin, dass der angegebene Standardwert der Wert der Zelleneigenschaft ist.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird veranschaulicht, wie die Zelleneigenschaften VALUE, FORMATTED_VALUE und FORMAT_STRING im dargestellt werden die `CellInfo` Element.  
  
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
  
  
