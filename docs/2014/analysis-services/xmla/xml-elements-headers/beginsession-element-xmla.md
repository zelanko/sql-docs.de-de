---
title: BeginSession-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- BeginSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9194333e376dc8ab685057847c3f4156330d5dfa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180060"
---
# <a name="beginsession-element-xmla"></a>BeginSession-Element (XMLA)
  Verwendet einen SOAP-Header in einer SOAP-Anforderungsnachricht, um eine neue Sitzung starten, auf einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das `BeginSession`-Headerelement ist Teil einer SOAP-Anforderung, die an eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz gesendet wurde, und startet explizit eine neue Sitzung auf einer Instanz. Von der SOAP-Antwort zurückgegebene SOAP-Header enthält ein [Sitzung](session-element-xmla.md) -Element, das die neue Sitzung identifiziert. Dieser neue Sitzungsbezeichner gespeichert und in nachfolgende SOAP-Anforderungen mit gesendet werden die `Session` Header-Element.  
  
 Wenn die `BeginSession` -Headerelement nicht gesendet, die eine Sitzung keine explizit gestartet. Wenn eine Sitzung nicht explizit gestartet wird, können Transaktionen auf dieser Sitzung nicht verwaltet werden. Das heißt, können keine der folgenden XML-Code für Befehle Analysis (XMLA): [BeginTransaction](../xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xml-elements-commands/committransaction-element-xmla.md), und [RollbackTransaction](../xml-elements-commands/rollbacktransaction-element-xmla.md). Alle XMLA-Methoden und -Befehle, die auf einer implizit gestarteten Sitzung ausgeführt werden, werden als unteilbare Transaktionen angesehen.  
  
## <a name="see-also"></a>Siehe auch  
 [EndSession-Element &#40;XMLA&#41;](endsession-element-xmla.md)   
 [Session-Element &#40;XMLA&#41;](session-element-xmla.md)   
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Header &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
