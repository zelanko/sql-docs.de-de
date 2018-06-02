---
title: Row-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84cf252303832ed157981103ffaede9718949e16
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576212"
---
# <a name="row-element-xmla"></a>row-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine einzelne Zeile mit Daten für eine [Stamm](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) Element, das tabellarische Daten zurückgegebenes enthält eine [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) oder [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) -Methodenaufruf.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <row>  
      <!-- One or more column elements -->  
   </row>  
</root>  
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
|Übergeordnete Elemente|[Stamm](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) (mithilfe der [Rowset](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) -Datentyp)|  
|Untergeordnete Elemente|Ein oder mehrere Column-Elemente.|  
  
## <a name="remarks"></a>Hinweise  
 Jede von einem **root** -Element ausgegebene Zeile, die tabellarische Daten enthält, verfügt über eine entsprechendes **row** -Element. Jede Spalte im **root** -Element wird durch ein separates XML-Element dargestellt. Beim Wert der Spalte des **row** -Elements handelt es sich um die Daten, die im XML-Element enthalten sind. Der Name der Spalte entspricht dem Namen des XML-Elements.  
  
 Der NULL-Wert für eine Spalte innerhalb einer Zeile kann auf zwei Arten ausgedrückt werden:  
  
-   Ein fehlendes Column-Element deutet darauf hin, dass die Spalte NULL ist.  
  
-   Das Column-Element kann das `xsi:nil='true'` -Attribut nutzen, um auf den NULL-Wert hinzuweisen.  
  
 Beispiel: enthält eine Zeile eine einzelne Spalte mit Namen Store_Name und ist der Wert NULL, kann dies so ausgedrückt werden:  
  
```  
<row>  
</row>  
```  
  
 Oder:  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
 Wenn ein Column-Element einen Fehler enthält, stellt ein **Error** -Element, wie im folgenden Beispiel beschrieben, Informationen über einen Fehler bereit:  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 Weitere Informationen über spaltenbenennung und Schemainformationen für tabellarische Daten finden Sie unter [Rowset-Datentyp &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
