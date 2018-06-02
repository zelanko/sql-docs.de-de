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
ms.openlocfilehash: 8bf682ff9d93ee61fa300d0055e215fa25d4b4e3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574642"
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
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Abbrechen](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Wenn dieses Element angegeben und auf **True**festgelegt ist, werden alle zugehörigen Verbindungen, Sitzungen und Befehle, die im übergeordneten **Cancel** -Befehl identifiziert sind, abgebrochen.  
  
## <a name="see-also"></a>Siehe auch
 [ConnectionID-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [SessionID-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [SPID-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
