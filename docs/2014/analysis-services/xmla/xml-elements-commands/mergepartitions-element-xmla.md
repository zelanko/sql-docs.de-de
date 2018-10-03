---
title: MergePartitions-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MergePartitions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MergePartitions
- microsoft.xml.analysis.mergepartitions
- urn:schemas-microsoft-com:xml-analysis#MergePartitions
helpviewer_keywords:
- MergePartitions command
ms.assetid: cf538189-0629-49b3-8e01-32afba7b020d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fbae4ca1baa8908f172e385d3bb44e7b6b2b3281
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156455"
---
# <a name="mergepartitions-element-xmla"></a>MergePartitions-Element (XMLA)
  Führt die Daten von einer oder mehreren Quellpartitionen zu einer Zielpartition zusammen und löscht dann die Quellpartitionen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <MergePartitions>  
      <Sources>...</Sources>  
      <Target>...</Target>  
   </MergePartitions>  
</Command>  
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
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Quellen](../xml-elements-properties/sources-element-xmla.md), [Ziel](../xml-elements-properties/target-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Alle Objektverweise in den `Sources` und `Target` -Elementen müssen auf verschiedene Partitionen in der gleichen Measuregruppe zeigen. Andernfalls tritt ein Fehler auf.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
