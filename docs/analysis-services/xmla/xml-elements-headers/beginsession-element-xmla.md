---
title: BeginSession-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aace4a6f0f8bfbf1cf41853224b98b0dd09fa26a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="beginsession-element-xmla"></a>BeginSession-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Verwendet einen SOAP-Header in einer SOAP-Anforderungsnachricht, um eine neue Sitzung auf einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]zu starten.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <BeginSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keine|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die **BeginSession** -Headerelement ist Teil einer SOAP-Anforderung gesendet, um eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz, und startet explizit eine neue Sitzung auf der Instanz. Der von der SOAP-Antwort zurückgegebene SOAP-Header enthält ein [Session](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md) -Element, das die neue Sitzung identifiziert. Dieser neue Sitzungsbezeichner wird gespeichert und in nachfolgende SOAP-Anforderungen mit dem **Session** -Headerelement gesendet.  
  
 Wenn das **BeginSession** -Headerelement nicht gesendet wird, wird keine Sitzung explizit gestartet. Wenn eine Sitzung nicht explizit gestartet wird, können Transaktionen auf dieser Sitzung nicht verwaltet werden. Mit anderen Worten, Sie können die folgenden XMLA-Befehle (XML for Analysis) nicht verwenden: [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)und [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md). Alle XMLA-Methoden und -Befehle, die auf einer implizit gestarteten Sitzung ausgeführt werden, werden als unteilbare Transaktionen angesehen.  
  
## <a name="see-also"></a>Siehe auch  
 [EndSession-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Session-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [Verwalten von Verbindungen und Sitzungen & #40; XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Header & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
