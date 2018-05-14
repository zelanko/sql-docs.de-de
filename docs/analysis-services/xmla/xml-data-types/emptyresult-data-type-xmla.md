---
title: EmptyResult-Datentyp (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d9dd3cf815ee616c3519883a59ddcbb8fbd61eb8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="emptyresult-data-type-xmla"></a>EmptyResult-Datentyp (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Definiert einen abgeleiteten Datentyp, der darstellt eine [Root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) Element, das keine Daten zurückgibt eine [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) oder [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) -Methodenaufruf.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis:empty  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Basisdatentypen|[Resultset](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Abgeleitete Datentypen|Keine|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keine|  
|Untergeordnete Elemente|Keine|  
|Abgeleitete Elemente|[Stamm](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Einige XMLA-Befehle (XML for Analysis) müssen keine Ergebnisse zurückgeben oder können aufgrund eines Fehlers keine zurückgeben. XMLA-Befehle, die kein Ergebnis zurückgeben, geben den **EmptyResult** -Datentyp zurück, einen Namespace auf dem **root** -Element.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein **root** -Element, das für ein leeres Ergebnis zurückgegeben wird.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Datentypen &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
