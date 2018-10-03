---
title: Root-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Root Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#root
- urn:schemas-microsoft-com:xml-analysis#root
- microsoft.xml.analysis.root
helpviewer_keywords:
- root element
ms.assetid: ecd9d6e8-b16c-4d62-9a87-107c413a0056
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 610ef2a3b332ec59e6ddf31d7f30acfe418549e5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48110250"
---
# <a name="root-element-xmla"></a>root-Element (XMLA)
  Enthält ein Ergebnis zurückgegeben, die von der [Discover](../xml-elements-methods-discover.md) Methode oder ein XML for Analysis (XMLA)-Befehl ausgeführt wird, mit der [Execute](../xml-elements-methods-execute.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<return> <!-- or results-->  
   ...  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">...</root> <!-- for Execute method only -->  
   <!-- or -->  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">...</root>  
   <!-- or -->  
   <root xmlns= xmlns="urn:schemas-microsoft-com:xml-analysis:empty">...</root>  
   ...  
</return>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Standardwert|None|  
|Cardinality|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
## <a name="data-type-and-length"></a>Datentyp und -länge  
  
|Ancestor|Datentyp|  
|--------------|---------------|  
|[DiscoverResponse](../xml-data-types/rowset-data-type-xmla.md), [Olapxmla_EmptyResult](../xml-data-types/emptyresult-data-type-xmla.md)|  
|[ExecuteResponse](../xml-data-types/mddataset-data-type-xmla.md), [Rowset](../xml-data-types/rowset-data-type-xmla.md), [Olapxmla_EmptyResult](../xml-data-types/emptyresult-data-type-xmla.md)|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ergebnisse](results-element-xmla.md), [zurückgeben](return-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `root` -Element enthält die Informationen, die entweder die [DiscoverResponse](../xml-elements-objects-discoverresponse.md) -Element über ein einzelnes `Discover` -Methodenaufruf, oder in der [ExecuteResponse](../xml-elements-objects-executeresponse.md) Element durch einen einzelnen XMLA-Befehl ausgeführt, indem ein einzelnes zurückgegeben `Execute` Methodenaufruf.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
