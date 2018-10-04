---
title: EmptyResult-Datentyp (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EmptyResult Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EmptyResult
- olapxmla_EmptyResult
- urn:schemas-microsoft-com:xml-analysis#EmptyResult
helpviewer_keywords:
- EmptyResult data type
ms.assetid: 63818123-acbb-4220-9d60-1aa20a7326a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc22612f18faa91e6cd668c022f036aadb9ef176
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088542"
---
# <a name="emptyresult-data-type-xmla"></a>EmptyResult-Datentyp (XMLA)
  Definiert einen abgeleiteten Datentyp, der darstellt eine [Stamm](../xml-elements-properties/root-element-xmla.md) -Element, das nicht zurückgeben von Daten aus einer [Discover](../xml-elements-methods-discover.md) oder [Execute](../xml-elements-methods-execute.md) Methodenaufruf.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis:empty  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Resultset](resultset-data-type-xmla.md)|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|None|  
|Abgeleitete Elemente|[Stammverzeichnis](../xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Einige XMLA-Befehle (XML for Analysis) müssen keine Ergebnisse zurückgeben oder können aufgrund eines Fehlers keine zurückgeben. Zurückgeben von XMLA-Befehle, die kein Ergebnis zurückgibt, führen Sie die `EmptyResult` -Datentyp, einen Namespace auf die `root` Element.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein `root`-Element, das für ein leeres Ergebnis zurückgegeben wird.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Datentypen &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
