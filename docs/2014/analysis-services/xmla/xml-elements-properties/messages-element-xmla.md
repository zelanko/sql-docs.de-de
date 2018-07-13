---
title: Nachrichten-Element (XMLA) | Microsoft-Dokumentation
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
- Messages Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Messages
- microsoft.xml.analysis.messages
- urn:schemas-microsoft-com:xml-analysis#Messages
helpviewer_keywords:
- Messages element
ms.assetid: 719d15ff-f18b-4c56-80ba-a9114c0b7d8a
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0fbaba30716831ef34a40dd94c6c9b2ab507641
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176777"
---
# <a name="messages-element-xmla"></a>Messages-Element (XMLA)
  Enthält eine Auflistung von [Message](message-element-xmla.md) -Elementen, die von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] durch einen Aufruf der Methoden [Discover](../xml-elements-methods-discover.md) oder [Execute](../xml-elements-methods-execute.md) zurückgegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Resultset>  
   <Messages>  
      <Message>  
   </Messages>  
</Resultset>  
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
|Übergeordnete Elemente|[Resultset](../xml-data-types/resultset-data-type-xmla.md)|  
|Untergeordnete Elemente|[MessageBox](message-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element wird verwendet, wenn ein `Discover`-Methodenaufruf oder ein einzelner XMLA-Befehl innerhalb eines `Execute`-Methodenaufrufs erfolgreich, jedoch mit Fehlern oder Warnungen, abgeschlossen wird. In solchen Fällen eine `Messages` Element wird hinzugefügt, um die [Stamm](root-element-xmla.md) Element nach allen anderen Elementen, die wiederum eine oder mehrere enthält `Message` Elemente. Jede `Message` -Element stellt dar, eine einzelne Nachricht, die entweder eine Fehler- oder eine Warnung aus, von zurückgegebenen der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
