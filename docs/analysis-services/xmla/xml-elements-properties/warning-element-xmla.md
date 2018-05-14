---
title: Warning-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ab17dd225e84061549eab6854d220782456f727f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="warning-element-xmla"></a>Warning-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält Informationen über eine Warnung zurückgegeben, die von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Message>  
   <Warning   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MessageBox](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|ErrorCode|Erforderliches **UnsignedInt** -Attribut. Enthält den numerischen Rückgabecode der Warnung.|  
|Severity|Optionales **String** -Attribut. Enthält das Ausmaß von der Warnung.|  
|Description|Optionales **String** -Attribut. Enthält den beschreibenden Text von der Warnung.|  
|Quelle|Optionales **String** -Attribut. Enthält den Namen der Komponente, die die Warnung generiert hat.|  
|Helpfile|Optionales **String** -Attribut. Enthält den Pfad oder die URL zur Hilfedatei oder dem Thema, das die Warnung beschreibt.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Error-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
