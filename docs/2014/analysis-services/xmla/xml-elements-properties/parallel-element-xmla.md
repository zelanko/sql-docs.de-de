---
title: Parallel-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2015-12-07
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Parallel Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Parallel
- http://schemas.microsoft.com/analysisservices/2003/engine#Parallel
- microsoft.xml.analysis.parallel
helpviewer_keywords:
- Parallel element
ms.assetid: 04726d94-37ee-460b-9744-d62b45f536b9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 90c722d8bb1b32e17ef5dc27e8ea0c84b00ff80e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091560"
---
# <a name="parallel-element-xmla"></a>Parallel Element (XMLA)
  Identifiziert gleichzeitig vom übergeordneten [Batch](../xml-elements-commands/batch-element-xmla.md) -Befehl auszuführende Befehle.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Batch>  
   ....  
   <Parallel maxParallel="Integer">  
      <!-- One or more XMLA commands -->  
   </Parallel>  
   ....  
</Batch>  
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
|Übergeordnete Elemente|[Batch](../xml-elements-commands/batch-element-xmla.md)|  
|Untergeordnete Elemente|[Process-Element](../xml-elements-commands/process-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|maxParallel|Optionale `Integer` Attribut. Gibt die maximale Anzahl an Threads an, auf denen gleichzeitig Befehle ausgeführt werden sollen. Die Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] bestimmt, sofern nicht angegeben oder auf 0 gesetzt, eine optimale Anzahl an Threads, basierend auf der auf dem Computer verfügbaren Anzahl an Prozessoren.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
