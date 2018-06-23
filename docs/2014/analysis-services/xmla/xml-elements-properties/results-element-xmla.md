---
title: Element (XMLA) führt | Microsoft Docs
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
- results Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.results
- urn:schemas-microsoft-com:xml-analysis#results
- http://schemas.microsoft.com/analysisservices/2003/engine#results
helpviewer_keywords:
- results element
ms.assetid: 3249a17a-7bfa-4753-b605-8f611ba7ae2b
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 203ad5a79938c80e2bfccc798ff5f9551ac66d8d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058368"
---
# <a name="results-element-xmla"></a>results-Element (XMLA)
  Enthält eine Auflistung von [root](root-element-xmla.md) -Elementen, die von der [Execute](../xml-elements-methods-execute.md) -Methode mit dem Befehl [Batch](../xml-elements-commands/batch-element-xmla.md) zurückgegeben werden.  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
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
|Übergeordnete Elemente|[Rückgabewert](return-element-xmla.md)|  
|Untergeordnete Elemente|[Stamm](root-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein `Batch`-Befehl von der `Execute`-Methode ausgeführt wird, enthält das `return`-Element statt eines einzelnen `results`-Elements ein einzelnes `root`-Element. Der Inhalt des `results`-Elements hängt von den Einstellungen ab, die verwendet werden, um den Befehl `Batch` auszuführen.  
  
 Für nicht transaktionale `Batch`-Befehle enthält das `results`-Element ein `root`-Element für jeden Befehl, der vom `Batch`-Befehl ausgeführt wird, und zwar unabhängig davon, ob der Befehl erfolgreich abgeschlossen werden kann oder nicht. Für transaktionale `Batch`-Befehle enthält das `results`-Element nur ein `root`-Element, das die Fehlerinformationen für den Befehl enthält, der innerhalb des `Batch`-Befehls fehlgeschlagen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  