---
title: Header (XMLA) | Microsoft-Dokumentation
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
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XMLA, headers
- SOAP headers [XML for Analysis]
- XML for Analysis, headers
- headers [XML for Analysis]
ms.assetid: 36407b5c-d98d-47e4-8d36-d8896e15a748
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1b04b85e3267e7432f37c5f70e823c859a82a952
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291296"
---
# <a name="headers-xmla"></a>Header (XMLA)
  Das XMLA-Protokoll (XML for Analysis) verwendet XML-Elemente innerhalb des SOAP-Headers, um Funktionen auf Protokollebene zu verwalten, wie Sitzungsunterstützung und die Aushandlung von unterstützten Funktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die folgenden Themen beschreiben die XMLA-Header-Elemente, die von implementiert [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Methode|Description|  
|------------|-----------------|  
|[BeginSession-Element &#40;XMLA&#41;](session-element-xmla.md)|Verwendet einen SOAP-Header in einer SOAP-Anforderungsnachricht, um eine neue Sitzung auf einer Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zu starten.|  
|[EndSession-Element &#40;XMLA&#41;](endsession-element-xmla.md)|Verwendet den SOAP-Header in einer SOAP-Anforderungsnachricht, um eine vorhandene Sitzung auf einer Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zu beenden.|  
|[Session-Element &#40;XMLA&#41;](session-element-xmla.md)|Verwendet den SOAP-Header in einer SOAP-Anforderungsnachricht, um eine vorhandene, explizierte Sitzung auf einer Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zu identifizieren.|  
|[ProtocolCapabilities-Element &#40;XMLA&#41;](protocolcapabilities-element-xmla.md)|Verwendet den SOAP-Header in einer SOAP-Anforderungsnachricht, um Protokollfunktionen zwischen einer Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] und einer Clientanwendung zu identifizieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Elemente &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML-Datentypen &#40;XMLA&#41;](../xml-data-types/xml-data-types-xmla.md)   
 [XML-Elemente &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)  
  
  
