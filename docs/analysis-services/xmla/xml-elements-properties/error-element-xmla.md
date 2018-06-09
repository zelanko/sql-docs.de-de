---
title: Error-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f223bff2dced01c2b3f954ca14242b1a35c93813
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576552"
---
# <a name="error-element-xmla"></a>Error-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält Informationen zu einem Fehler, die von einer Instanz von Analysis Services zurückgegeben.  
  
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
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MessageBox](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Untergeordnete Elemente|Siehe Tabelle unten.|  
  
|Ancestor|Untergeordnete Elemente|  
|--------------|--------------------|  
|[MessageBox](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|InclusionThresholdSetting|  
|[Zelle](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md), [Zeile](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[Beschreibung](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md), [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md), [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md), [Quelle](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|ErrorCode|Erforderliche **UnsignedInt** Attribut (nur wenn **Nachricht** ist das übergeordnete Element.) Enthält den numerischen Rückgabecode des Fehlers.|  
|Schweregrad|Optionale **Zeichenfolge** Attribut (nur wenn **Nachricht** ist das übergeordnete Element.) Enthält das Ausmaß des Fehlers.|  
|Description|Optionale **Zeichenfolge** Attribut (nur wenn **Nachricht** ist das übergeordnete Element.) Enthält den beschreibenden Text des Fehlers.|  
|Quelle|Optionale **Zeichenfolge** Attribut (nur wenn **Nachricht** ist das übergeordnete Element.) Enthält den Namen der Komponente, die den Fehler generiert hat.|  
|HelpFile|Optionale **Zeichenfolge** Attribut (nur wenn **Nachricht** ist das übergeordnete Element.) Enthält den Pfad oder die URL zur Hilfedatei oder dem Thema, das den Fehler beschreibt.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch
 [Warning-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
