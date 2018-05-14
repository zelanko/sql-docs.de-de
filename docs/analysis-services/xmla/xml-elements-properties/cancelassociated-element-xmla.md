---
title: CancelAssociated-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a261a1b76241b475b16065ebd1b649b432f68e9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="cancelassociated-element-xmla"></a>CancelAssociated-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Gibt an, ob das übergeordnete [Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) -Element alle zugeordneten Befehle abbrechen soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Abbrechen](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Wenn dieses Element angegeben und auf **True**festgelegt ist, werden alle zugehörigen Verbindungen, Sitzungen und Befehle, die im übergeordneten **Cancel** -Befehl identifiziert sind, abgebrochen.  
  
## <a name="see-also"></a>Siehe auch  
 [ConnectionID-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [SessionID-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [SPID-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
