---
title: Session-Element (XMLA) | Microsoft-Dokumentation
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
- Session Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74ce499ba167c7c0d439fba4e4099638f4e98db6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310370"
---
# <a name="session-element-xmla"></a>Session-Element (XMLA)
  Verwendet den SOAP-Header in einer SOAP-Anforderungsnachricht identifiziert eine vorhandene, explizierte Sitzung auf einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|SessionID|Erforderliches `String`-Attribut, das die Sitzung identifiziert, die verwendet werden soll. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] identifiziert eine Sitzung anhand einer GUID (Globally Unique Identifier).|  
  
## <a name="remarks"></a>Hinweise  
 Das `Session`-Header-Element identifiziert eine vorhandene, explizit gestartet Sitzung auf der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz. Das `Session`-Element ist in den folgenden Nachrichtentypen Teil des SOAP-Headers:  
  
-   Eine SOAP-Antwort mit einem [BeginSession](session-element-xmla.md) SOAP-Header-Element.  
  
-   Eine SOAP-Anforderung zur Identifikation der Sitzung zum Ausführen der [Discover](../xml-elements-methods-discover.md) oder [Execute](../xml-elements-methods-execute.md) Methode.  
  
 Eine Sitzungs-ID garantiert nicht, dass eine Sitzung gültig bleibt. Die im `Session`-Element angegebene Sitzung kann ablaufen. Eine Sitzung kann beispielsweise ablaufen, wenn das Timeout der Sitzung erreicht ist oder wenn die der Sitzung zugeordnete Verbindung beendet wird. Wenn die Sitzung abläuft und nicht mehr gültig ist, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wird die Sitzung beendet und ein Rollback eine Transaktion aktuell im Prozess. Jede SOAP-Nachricht, die zusammen mit einer nicht mehr gültigen ID gesendet wird, schlägt mit einem SOAP-Fehler fehl, der angibt, dass die angegebene Sitzung nicht gefunden werden kann.  
  
 Wenn eine `Session` Element wird nicht als Teil einer SOAP-Anforderung gesendet der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz beginnt implizit eine Sitzung für die Dauer des der `Discover` oder `Execute` Methodenaufruf, und klicken Sie dann beendet diese Sitzung, wenn der Methodenaufruf abgeschlossen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [EndSession-Element &#40;XMLA&#41;](endsession-element-xmla.md)   
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Header &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
