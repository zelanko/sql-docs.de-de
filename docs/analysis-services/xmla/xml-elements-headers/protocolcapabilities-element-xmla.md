---
title: ProtocolCapabilities-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85ddeb22fac03e5ae7f66521ac3ca8a46e210fe7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574782"
---
# <a name="protocolcapabilities-element-xmla"></a>ProtocolCapabilities-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Verwendet den SOAP-Header in einer SOAP-Anforderungsnachricht, um Protokollfunktionen zwischen einer Instanz von Analysis Services und einer Clientanwendung zu identifizieren.  
  
 **Namespace** `http://schemas.microsoft.com/analysisservices/2003/engine`  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <ProtocolCapabilities xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
         <Capability>...</Capability>  
      </ProtocolCapabilities>  
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
|Untergeordnete Elemente|[Funktion](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die **ProtocolCapabilities** Element ermöglicht Clientanwendungen das aushandeln, Protokollfunktionen, z. B. für binäres XML und Komprimierung unterstützt, wobei ein [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz zu einem beliebigen Zeitpunkt. Die Protokollaushandlung schließt die folgenden Schritte ein:  
  
1.  Die Clientanwendung identifiziert die Protokollfunktion, indem sie eine SOAP-Anforderung sendet, die sowohl das **ProtocolCapabilities** -Element als auch den SOAP-Header enthält.  
  
2.  Die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz empfängt und verarbeitet die SOAP-Anforderung.  
  
3.  Wenn die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz hat die gleiche Protokollfunktion wie angefordert, sendet die Instanz eine SOAP-Antwort, die die gleiche enthält **ProtocolCapabilities** Element in der SOAP-Anforderung gesendet und das Protokoll wurde erfolgreich ausgehandelt. Andernfalls werden die Protokollfunktionen nicht erfolgreich ausgehandelt, und die Instanz gibt einen SOAP-Fehler zurück.  
  
 Nach erfolgreich Protokollfunktionen, wie lange die Clientanwendung und die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz Verwendung eines bestimmten Protokolls hängt davon ab, ob die Sitzung implizit oder explizit ist:  
  
-   Eine explizite Sitzung ist eine, die erstellt wird, mithilfe der [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) Header-Element. Bei einer expliziten Sitzung wird das verhandelte Protokoll so lange verwendet, bis die Clientanwendung ein neues **ProtocolCapabilities** -Element sendet oder bis die Sitzung endet.  
  
-   Eine implizite Sitzung ist eine Sitzung, die über eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz erstellt wird und nicht beim Übermitteln einer SOAP-Anforderung explizit von der Clientanwendung angegeben wird. Bei einer impliziten Sitzung wird das ausgehandelte Protokoll nur so lange verwendet, bis die SOAP-Anforderung abgeschlossen ist.  
  
 Protokollfunktionen müssen nicht explizit ausgehandelt werden. Das heißt, dass eine Clientanwendung kein **ProtocolCapabilities** -Element als Teil der SOAP-Anforderung enthalten muss. Wenn eine SOAP-Anforderung nicht enthalten ist ein **ProtocolCapabilities** Element, das [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz antwortet mit dem gleichen Format wie die SOAP-Anforderung.  
  
## <a name="see-also"></a>Siehe auch
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Header &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
