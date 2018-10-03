---
title: Parameters-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Parameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameters
- urn:schemas-microsoft-com:xml-analysis#Parameters
- microsoft.xml.analysis.parameters
helpviewer_keywords:
- Parameters element
ms.assetid: d46454a1-a1d1-4aa8-95ea-54be22a53e83
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b9c3d0d642ad7248d87e7cc17aaa17953bf6aec
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134050"
---
# <a name="parameters-element-xmla"></a>Parameters-Element (XMLA)
  Enthält eine Auflistung von [Parameter](parameter-element-xmla.md) Elemente, die verwendet werden, indem die [Execute](../xml-elements-methods-execute.md) Methode.  
  
 **Namespace:** `urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
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
|Übergeordnete Elemente|[Ausführen](../xml-elements-methods-execute.md)|  
|Untergeordnete Elemente|[Parameter](parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Einige XMLA-Befehle (XML for Analysis) wie der [Process](../xml-elements-commands/process-element-xmla.md) -Befehl können weitere Informationen erfordern. Die `Parameters` -Element bietet einen Mechanismus zum Bereitstellen zusätzlicher Informationen, einschließlich segmentierter Informationen, XMLA-Befehl.  
  
 Wenn der XMLA-Befehl das `Parameters`-Element nicht verwendet, kann das Element beim Aufrufen der `Execute`-Methode weggelassen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
