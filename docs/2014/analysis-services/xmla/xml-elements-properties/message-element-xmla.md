---
title: Message-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Message Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.message
- http://schemas.microsoft.com/analysisservices/2003/engine#Message
- urn:schemas-microsoft-com:xml-analysis#Message
helpviewer_keywords:
- Message element
ms.assetid: 028911e2-9779-43b1-824d-6d7fb2295885
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4aebaf918701d4ce10cfda9a4f3c030b53404e9f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054064"
---
# <a name="message-element-xmla"></a>Message-Element (XMLA)
  Enthält eine Meldung, die von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] durch einen Aufruf der [Discover](../xml-elements-methods-discover.md) - oder [Execute](../xml-elements-methods-execute.md) -Methode zurückgegeben wurde.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Messages>  
   ...  
   <Message>  
      <Error>...</Error>  
      <!-- or -->  
      <Warning>...</Warning>  
   </Message>  
   ...  
</Messages>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Meldungen](messages-element-xmla.md)|  
|Untergeordnete Elemente|[Error](error-element-xmla.md), [Warning](warning-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element wird verwendet, wenn ein `Discover`-Methodenaufruf oder ein einzelner XMLA-Befehl innerhalb eines `Execute`-Methodenaufrufs erfolgreich, jedoch mit Fehlern oder Warnungen, abgeschlossen wird. In solchen Fällen eine `Messages` Element wird hinzugefügt dem Stammelement nach allen anderen Elementen, die wiederum eine oder mehrere enthält `Message` Elemente. Jede `Message` -Element stellt dar, eine einzelne Nachricht, die entweder eine Fehler- oder eine Warnung aus, von zurückgegebenen der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
