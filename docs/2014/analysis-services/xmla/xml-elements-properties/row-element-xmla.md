---
title: Row-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- row Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#row
- microsoft.xml.analysis.row
- http://schemas.microsoft.com/analysisservices/2003/engine#row
helpviewer_keywords:
- row element
ms.assetid: 4d9977a0-c396-44c7-9fd4-97f4c3d643aa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 45bda6938dd98dae305c7143af39fd7d4bfd4142
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096875"
---
# <a name="row-element-xmla"></a>row-Element (XMLA)
  Enthält eine einzelne Zeile von Daten für eine [Stamm](root-element-xmla.md) -Element, das tabellarische Daten, die vom enthält eine [ermitteln](../xml-elements-methods-discover.md) oder [Execute](../xml-elements-methods-execute.md) Methodenaufruf.  
  
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
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Stamm](root-element-xmla.md) (mithilfe der [Rowset](../xml-data-types/rowset-data-type-xmla.md) -Datentyp)|  
|Untergeordnete Elemente|Ein oder mehrere Column-Elemente.|  
  
## <a name="remarks"></a>Hinweise  
 Jede von einem `root`-Element ausgegebene Zeile, die tabellarische Daten enthält, verfügt über eine entsprechendes `row`-Element. Jede Spalte in der `root` Element durch ein separates XML-Element dargestellt wird. Der Wert der Spalte, für die `row` Element ist, die das XML-Element enthaltenen Daten, und der Name der Spalte entspricht dem Namen des XML-Elements.  
  
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
  
 Wenn ein Column-Element einen Fehler enthält eine `Error` -Element stellt Informationen zu einem Fehler bereit, wie im folgenden Beispiel beschrieben:  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 Weitere Informationen über spaltenbenennung und Schemainformationen für tabellarische Daten finden Sie unter [Rowset-Datentyp &#40;XMLA&#41;](../xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
