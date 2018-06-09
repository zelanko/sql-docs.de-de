---
title: Capability-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
ms.openlocfilehash: dca8f668f64ab8ced157cf817be1f9f8f6390133
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574982"
---
# <a name="capability-element-xmla"></a>Capability-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Gibt Unterstützung für eine Protokollfunktion im übergeordneten [ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md) Header-Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die **Funktion** Element gibt an, dass eine bestimmte Funktion, z. B. Binär- oder Komprimierungsfunktion, indem Sie entweder die Anwendung unterstützt wird, die **ProtocolCapabilities** Header-Element in der SOAP-Header der SOAP-Anforderung oder von der Instanz von Analysis Services, die enthalten die **ProtocolCapabilities** -Headerelement im SOAP-Header der SOAP-Antwort. Der Wert des **Capability** -Elements ist der Name der Funktion, die unterstützt werden soll.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in der folgenden Tabelle aufgeführten Funktionen unterstützt.  
  
|Name der Funktion|Description|  
|---------------------|-----------------|  
|sx|Binäre XML-Unterstützung|  
|xpress|Komprimierungsunterstützung|  
  
## <a name="see-also"></a>Siehe auch
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
