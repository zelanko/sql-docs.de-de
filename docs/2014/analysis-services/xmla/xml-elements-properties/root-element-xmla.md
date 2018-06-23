---
title: Root-Element (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 16
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 481947e1d58fe5da34b29f43405bfff48583b8c9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149961"
---
# <a name="root-element-xmla"></a>root-Element (XMLA)
  Ein zurückgegebenes Ergebnis enthält die [Discover](../xml-elements-methods-discover.md) Methode oder ein XML for Analysis (XMLA)-Befehl ausgeführt wird, mithilfe der [Execute](../xml-elements-methods-execute.md) Methode.  
  
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
|Standardwert|InclusionThresholdSetting|  
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
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `root` -Element enthält die Informationen, die entweder die [DiscoverResponse](../xml-elements-objects-discoverresponse.md) -Element über einen einzelnen `Discover` -Methodenaufruf, oder in der [ExecuteResponse](../xml-elements-objects-executeresponse.md) Element einen einzelnen XMLA-Befehl ausgeführt wird, über einen einzelnen zurückgegebenes `Execute` -Methodenaufruf.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  