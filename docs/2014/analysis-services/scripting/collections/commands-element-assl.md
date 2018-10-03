---
title: -Element (ASSL)-Befehle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Commands Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element
ms.assetid: c9f69fe8-2221-469b-b5b0-08563aaa01dc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 14287d7479af8a34e8394b878436bd2ed812d763
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48184750"
---
# <a name="commands-element-assl"></a>Commands-Element (ASSL)
  Enthält die Auflistung der [Command](../objects/command-element-assl.md) -Elemente, die mit einem [MdxScript](../objects/mdxscript-element-assl.md) -Element verknüpft sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MdxScript>  
   ...  
   <Commands>  
      <Command>...</Command>  
...</Commands>  
   ...  
</MdxScript>  
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
|Übergeordnetes Element|[MdxScript](../objects/mdxscript-element-assl.md)|  
|Untergeordnete Elemente|[Befehl](../objects/command-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.CommandCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
