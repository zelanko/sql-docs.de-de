---
title: return-Element (XMLA) | Microsoft Docs
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
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1a4468ce3d4b14ff9cd9db7c9373083aad75d3eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046268"
---
# <a name="return-element-xmla"></a>return-Element (XMLA)
  Enthält Informationen, indem Sie eine [DiscoverResponse](../xml-elements-objects-discoverresponse.md) -Element als Antwort auf eine [Discover](../xml-elements-methods-discover.md) Methodenaufruf oder ein [ExecuteResponse](../xml-elements-objects-executeresponse.md) -Element als Antwort auf eine [Execute](../xml-elements-methods-execute.md) -Methodenaufruf.  
  
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
|Vorgänger:[DiscoverResponse](../xml-elements-objects-discoverresponse.md)|Untergeordnetes Element: <br />                        [Stamm](root-element-xmla.md)|  
|Vorgänger: <br />                        [ExecuteResponse](../xml-elements-objects-executeresponse.md)|Untergeordnetes Element: [Root](root-element-xmla.md) oder [Ergebnisse](results-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `return` -Element enthält die zurückgegebene Daten der `Discover` und `Execute` Methoden. In der Regel enthält das `return`-Element ein einzelnes `root`-Element, das entweder die von einem erfolgreichen `Discover`- oder `Execute`-Methodenaufruf zurückgegebenen Daten oder eine von einem nicht erfolgreichen Methodenaufruf zurückgegebene XMLA-Ausnahme (XML for Analysis) enthält. Wenn die `Execute`-Methode einen `Batch`-Befehl enthält, der mehrere Vorgänge ausführt, enthält das `return`-Element ein `results`-Element, das wiederum ein `root`-Element für jeden erfolgreich oder nicht erfolgreich vom `Batch`-Befehl ausgeführten Befehl enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  