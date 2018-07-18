---
title: Member-Element (XMLA) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1c962452675a0c1c91a3573546f0763060dfb44e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994642"
---
# <a name="member-element-xmla"></a>Member-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Stellt ein einzelnes Element in einem übergeordneten [Mitglieder](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md) oder [Tupel](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Members>  
   ...  
   <Member>  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Members>  
<!-- or -->  
<Tuple>  
   ...  
   <Member Hierarchy="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Tuple>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Mitglieder](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md), [Tupel](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
|Untergeordnete Elemente|[Caption](../../../analysis-services/xmla/xml-elements-properties/caption-element-xmla.md), [DisplayInfo](../../../analysis-services/xmla/xml-elements-properties/displayinfo-element-xmla.md), [LName](../../../analysis-services/xmla/xml-elements-properties/lname-element-xmla.md), [LNum](../../../analysis-services/xmla/xml-elements-properties/lnum-element-xmla.md), [UName](../../../analysis-services/xmla/xml-elements-properties/uname-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|Hierarchy|Erforderliches **String** -Attribut (nur für übergeordnete **Tuple** -Elemente). Der Name der Hierarchie, zu der das Element, das vom **Member** -Element dargestellt wird, gehört.|  
  
## <a name="remarks"></a>Hinweise  
 Das **Member** -Element enthält die Informationen, die benötigt werden, um ein Element innerhalb einer gegebenen Hierarchie zu identifizieren und anzuzeigen. Für übergeordnete **Members** -Elemente wird die Hierarchie bereits vom **Hierarchy** -Attribut des übergeordneten Elements angegeben. Für übergeordnete **Tuple** -Elemente wird die Hierarchie mithilfe des **Hierarchy** -Attributs des **Member** -Elements angegeben.  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
