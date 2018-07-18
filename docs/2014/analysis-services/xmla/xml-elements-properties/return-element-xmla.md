---
title: return-Element (XMLA) | Microsoft-Dokumentation
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
- return Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4808372fbf80b2b3a79bc11e3f2423511eb717be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192403"
---
# <a name="return-element-xmla"></a>return-Element (XMLA)
  Enthält Informationen, indem eine [DiscoverResponse](../xml-elements-objects-discoverresponse.md) -Element als Antwort auf eine [Discover](../xml-elements-methods-discover.md) Methodenaufruf oder ein [ExecuteResponse](../xml-elements-objects-executeresponse.md) -Element als Antwort auf eine [Execute](../xml-elements-methods-execute.md) Methodenaufruf.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DiscoverResponse> <!-- or ExecuteResponse -->  
   <return>  
      <root>...</root>  
      <!-- or -->  
      <results>...</results> <!-- ExecuteResponse only -->  
   </return>  
</DiscoverResponse>  
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
|Übergeordnete Elemente|[DiscoverResponse](../xml-elements-objects-discoverresponse.md), [ExecuteResponse](../xml-elements-objects-executeresponse.md)|  
|Vorgänger:[DiscoverResponse](../xml-elements-objects-discoverresponse.md)|Untergeordnetes Element: <br />                        [Stammverzeichnis](root-element-xmla.md)|  
|Vorgänger: <br />                        [ExecuteResponse](../xml-elements-objects-executeresponse.md)|Untergeordnete: [Stamm](root-element-xmla.md) oder [Ergebnisse](results-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `return` Element enthält, die vom zurückgegebenen Daten die `Discover` und `Execute` Methoden. In der Regel enthält das `return`-Element ein einzelnes `root`-Element, das entweder die von einem erfolgreichen `Discover`- oder `Execute`-Methodenaufruf zurückgegebenen Daten oder eine von einem nicht erfolgreichen Methodenaufruf zurückgegebene XMLA-Ausnahme (XML for Analysis) enthält. Wenn die `Execute`-Methode einen `Batch`-Befehl enthält, der mehrere Vorgänge ausführt, enthält das `return`-Element ein `results`-Element, das wiederum ein `root`-Element für jeden erfolgreich oder nicht erfolgreich vom `Batch`-Befehl ausgeführten Befehl enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
