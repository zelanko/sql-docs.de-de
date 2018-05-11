---
title: Message-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 649d473f11903cb5306525b7e1fdff3e7af8f233
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="message-element-xmla"></a>Message-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Meldung, die von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] durch einen Aufruf der [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) - oder [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) -Methode zurückgegeben wurde.  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Meldungen](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)|  
|Untergeordnete Elemente|[Error](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md), [Warning](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element wird verwendet, wenn ein **Discover** -Methodenaufruf oder ein einzelner XMLA-Befehl innerhalb eines **Execute** -Methodenaufrufs erfolgreich, jedoch mit Fehlern oder Warnungen, abgeschlossen wird. In einem solchen Fall wird dem Stammelement nach allen anderen Elementen ein **Messages** -Element hinzugefügt, das wiederum mindestens ein **Message** -Element enthält. Jedes **Message** -Element stellt eine einzelne Nachricht dar, entweder eine Fehler- oder eine Warnungsmeldung, die von der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
