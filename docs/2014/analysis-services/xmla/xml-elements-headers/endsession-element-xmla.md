---
title: EndSession-Element (XMLA) | Microsoft Docs
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
- EndSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EndSession
- urn:schemas-microsoft-com:xml-analysis#EndSession
- microsoft.xml.analysis.endsession
helpviewer_keywords:
- EndSession element
ms.assetid: e64f1da4-5c83-40a2-b15e-837f5451bafa
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1f54f1ec23fbb07744ffea1009f4df1aef11b6f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058771"
---
# <a name="endsession-element-xmla"></a>EndSession-Element (XMLA)
  Verwendet den SOAP-Header in einer SOAP-Anforderungsnachricht zum Beenden einer vorhandenen Sitzungs in einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|SessionID|Erforderliches `String`-Attribut, das die Sitzung identifiziert, die beendet werden soll. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] identifiziert eine Sitzung anhand einer GUID (Globally Unique Identifier).|  
  
## <a name="remarks"></a>Hinweise  
 Die `EndSession` -Headerelement ist Teil der SOAP-Anforderung an eine vorhandene, explizit gestartete Sitzung gesendet werden, auf eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Wenn die `EndSession` -Headerelement gesendet wurde, aber enthält eine Sitzungs-ID, die nicht mehr gültig ist, ein SOAP-Fehler zurückgegeben, der angibt, dass die Sitzung nicht gefunden werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [BeginSession-Element &#40;XMLA&#41;](session-element-xmla.md)   
 [Session-Element &#40;XMLA&#41;](session-element-xmla.md)   
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Header &#40;XMLA&#41;](xml-elements-headers.md)  
  
  