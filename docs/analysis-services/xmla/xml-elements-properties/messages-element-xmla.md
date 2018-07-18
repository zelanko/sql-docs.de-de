---
title: Nachrichten-Element (XMLA) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21bb83be0940b806c071f305d75826ab65330c15
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38054197"
---
# <a name="messages-element-xmla"></a>Messages-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Auflistung von [Nachricht](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md) Elemente zurückgegeben werden, von einer Instanz von Analysis Services durch eine [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) oder [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methodenaufruf.  
  
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
|Übergeordnete Elemente|[Resultset](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Untergeordnete Elemente|[MessageBox](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element wird verwendet, wenn ein **Discover** -Methodenaufruf oder ein einzelner XMLA-Befehl innerhalb eines **Execute** -Methodenaufrufs erfolgreich, jedoch mit Fehlern oder Warnungen, abgeschlossen wird. In einem solchen Fall wird nach allen anderen Elementen ein **Messages** -Element zum [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) -Element hinzugefügt, das wiederum ein oder mehrere **Message** -Elemente enthält. Jedes **Message** -Element stellt eine einzelne Nachricht dar, entweder eine Fehler- oder eine Warnungsmeldung, die von der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
