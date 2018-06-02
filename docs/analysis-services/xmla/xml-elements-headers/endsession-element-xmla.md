---
title: EndSession-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9529d3d704fd1c8bb8eded66c713137b1233d99a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574922"
---
# <a name="endsession-element-xmla"></a>EndSession-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Verwendet den SOAP-Header in einer SOAP-Anforderungsnachricht um zu eine vorhandene Sitzung in einer Instanz von Analysis Services zu beenden.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <EndSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|SessionID|Erforderliches **String** -Attribut, das die Sitzung identifiziert, die beendet werden soll. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] identifiziert eine Sitzung anhand einer GUID (Globally Unique Identifier).|  
  
## <a name="remarks"></a>Hinweise  
 Die **EndSession** -Headerelement ist Teil der SOAP-Anforderung an eine vorhandene, explizit gestartete Sitzung gesendet werden, auf eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Wenn das **EndSession** -Headerelement gesendet wurde, aber einen Sitzungsbezeichner enthält, der nicht mehr länger gültig ist, wird ein SOAP-Fehler zurückgegeben, der angibt, dass die Sitzung nicht gefunden werden kann.  
  
## <a name="see-also"></a>Siehe auch
 [BeginSession-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)   
 [Session-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Header &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
