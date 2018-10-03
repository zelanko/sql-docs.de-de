---
title: Error-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Error Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b9b961a0d8d5a33cb0869b72e0250dee5456ca7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210150"
---
# <a name="error-element-xmla"></a>Error-Element (XMLA)
  Enthält Informationen zu einem Fehler zurückgegeben, die von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Message>  
   <Error   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
<!-- or -->  
<Cell><!-- or row -->  
   <!-- A child element -->  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception"  
         < ErrorCode>...</ErrorCode>  
         < Description>...</Description>  
         < Source>...</Source>  
         < HelpFile>...</HelpFile>  
      </Error>  
   <!-- /A child element -- >  
</Cell>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MessageBox](message-element-xmla.md)|  
  
## <a name="child-elements"></a>Untergeordnete Elemente  
  
|Ancestor|Untergeordnete Elemente|  
|--------------|--------------------|  
|[MessageBox](message-element-xmla.md)|None|  
|[Zelle](cell-element-mddataset-xmla.md), [Zeile](description-element-xmla.md), [ErrorCode](errorcode-element-xmla.md), [HelpFile](file-element-xmla.md), [Quelle](source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|ErrorCode|Erforderliche `UnsignedInt` Attribut (nur, wenn `Message` ist das übergeordnete Element.) Enthält den numerischen Rückgabecode des Fehlers.|  
|Schweregrad|Optionale `String` Attribut (nur, wenn `Message` ist das übergeordnete Element.) Enthält das Ausmaß des Fehlers.|  
|Description|Optionale `String` Attribut (nur, wenn `Message` ist das übergeordnete Element.) Enthält den beschreibenden Text des Fehlers.|  
|Source|Optionale `String` Attribut (nur, wenn `Message` ist das übergeordnete Element.) Enthält den Namen der Komponente, die den Fehler generiert hat.|  
|HelpFile|Optionale `String` Attribut (nur, wenn `Message` ist das übergeordnete Element.) Enthält den Pfad oder die URL zur Hilfedatei oder dem Thema, das den Fehler beschreibt.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Warning-Element &#40;XMLA&#41;](warning-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
