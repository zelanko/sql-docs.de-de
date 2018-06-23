---
title: Exception-Element (XMLA) | Microsoft Docs
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
- Exception Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Exception
- urn:schemas-microsoft-com:xml-analysis#Exception
- microsoft.xml.analysis.exception
helpviewer_keywords:
- Exception element
ms.assetid: 0be4cc2f-c03e-490a-a6f7-8b1ede5d09ba
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 824743a3e8aeb7d735d6844dd1b025de06e09e9d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057884"
---
# <a name="exception-element-xmla"></a>Exception-Element (XMLA)
  Gibt an, dass eine Ausnahme zurückgegeben wurde, aus einer [Discover](../xml-elements-methods-discover.md) oder [Execute](../xml-elements-methods-execute.md) -Methodenaufruf.  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/exception  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
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
|Übergeordnete Elemente|[Stamm](root-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Bei einem während der Ausführung Fehler einer `Discover` Methodenaufruf oder ein einzelner XMLA-Befehl in eine `Execute` -Methodenaufruf, der die Methode oder der Befehl abgeschlossen ist, verhindert die `root` -Element für diese Methode / diesen Befehl enthält ein `Exception` Element und ein `Messages` Element. Das `Exception`-Element gibt an, dass ein Fehler aufgetreten ist, der verhindert, dass die Methode oder der Befehl erfolgreich ausgeführt wird, und das `Messages`-Element enthält die Liste der entsprechenden Fehler- oder Warnmeldungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Element Nachrichten &#40;XMLA&#41;](messages-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  