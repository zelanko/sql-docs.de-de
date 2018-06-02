---
title: Folders-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 803ec660944663c7f40f1b7c9dddc118b8b6b76c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575402"
---
# <a name="folders-element-xmla"></a>Folders-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Auflistung von [Folder](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) -Elementen, die vom übergeordneten [Location](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) -Element während eines [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) - oder [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) -Befehls verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Location>  
   ...  
   <Folders>  
      <Folder>...</Folder>  
   </Folders>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine (Auflistung)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Untergeordnete Elemente|[Ordner](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch
 [Restore-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchronize-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
