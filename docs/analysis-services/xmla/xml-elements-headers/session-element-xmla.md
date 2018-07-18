---
title: Session-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 02b4c93919e6354a59aad9b42a4f6dc8373c880f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34577502"
---
# <a name="session-element-xmla"></a>Session-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Verwendet den SOAP-Header in einer SOAP-Anforderungsnachricht, um eine vorhandene, explizierte Sitzung auf einer Instanz von Analysis Services zu identifizieren.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
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
|SessionID|Erforderliches **String** -Attribut, das die Sitzung identifiziert, die verwendet werden soll. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] identifiziert eine Sitzung anhand einer GUID (Globally Unique Identifier).|  
  
## <a name="remarks"></a>Hinweise  
 Die **Sitzung** Header-Element identifiziert eine vorhandene, explizit gestartete Sitzung auf die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Das **Session** -Element ist in den folgenden Nachrichtentypen Teil des SOAP-Headers:  
  
-   Eine SOAP-Antwort mit einer [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) SOAP-Header-Element.  
  
-   Eine SOAP-Anforderung zur Identifikation der Sitzung für die Ausführung der [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) oder [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methode.  
  
 Eine Sitzungs-ID garantiert nicht, dass eine Sitzung gültig bleibt. Die im **Session** -Element angegebene Sitzung kann ablaufen. Eine Sitzung kann beispielsweise ablaufen, wenn das Timeout der Sitzung erreicht ist oder wenn die der Sitzung zugeordnete Verbindung beendet wird. Wenn die Sitzung abläuft und nicht mehr gültig ist, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wird die Sitzung beendet und ein Rollback eine Transaktion derzeit im Prozess. Jede SOAP-Nachricht, die zusammen mit einer nicht mehr gültigen ID gesendet wird, schlägt mit einem SOAP-Fehler fehl, der angibt, dass die angegebene Sitzung nicht gefunden werden kann.  
  
 Wenn eine **Sitzung** Element nicht als Teil einer SOAP-Anforderung gesendet wird die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz beginnt implizit eine Sitzung für die Dauer der der **Discover** oder **Execute** Methodenaufruf, und klicken Sie dann endet die Sitzung, wenn der Methodenaufruf abgeschlossen ist.  
  
## <a name="see-also"></a>Siehe auch
 [EndSession-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Header &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
