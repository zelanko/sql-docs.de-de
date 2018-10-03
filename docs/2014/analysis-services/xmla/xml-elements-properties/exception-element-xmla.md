---
title: Exception-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e447bda3d52ac63125f3a96769fcee2c0158494c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178540"
---
# <a name="exception-element-xmla"></a>Exception-Element (XMLA)
  Gibt an, dass eine Ausnahme zurückgegeben wurde eine [Discover](../xml-elements-methods-discover.md) oder [Execute](../xml-elements-methods-execute.md) Methodenaufruf.  
  
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
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Stammverzeichnis](root-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Bei einem während der Ausführung Fehler eine `Discover` Methodenaufruf oder ein einzelner XMLA-Befehl in einer `Execute` Methodenaufruf der Methode oder der Befehl abgeschlossen ist, der verhindert, dass die `root` -Element für diese Methode / diesen Befehl enthält eine `Exception` Element und ein `Messages` Element. Das `Exception`-Element gibt an, dass ein Fehler aufgetreten ist, der verhindert, dass die Methode oder der Befehl erfolgreich ausgeführt wird, und das `Messages`-Element enthält die Liste der entsprechenden Fehler- oder Warnmeldungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Element Nachrichten &#40;XMLA&#41;](messages-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
