---
title: Assembly-Element (ASSL) | Microsoft Docs
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
- Assembly Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ASSEMBLY
helpviewer_keywords:
- Assembly element [ASSL]
ms.assetid: 1910ccb0-7da0-4ee1-9548-ad6e0068d23d
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 02bc362fd633a7c3cf9fcd4936d2a0580753c01b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048839"
---
# <a name="assembly-element-assl"></a>Assembly-Element (ASSL)
  Stellt eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly oder einer COM-dynamic Link Library (DLL) zugeordnet eine [Server](server-element-assl.md) Element oder ein [Datenbank](database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Assemblies>  
   <Assembly xsi:type="ClrAssembly">...</Assembly>  
   <!-- or -->  
   <Assembly xsi:type="ComAssembly">...</Assembly>  
</Assemblies>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[ClrAssembly](../data-type/assembly-data-type-assl.md), [ComAssembly](../data-type/comassembly-data-type-assl.md)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Assemblys](../collections/assemblies-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Assembly>.  
  
## <a name="see-also"></a>Siehe auch  
 [Server-Element &#40;ASSL&#41;](server-element-assl.md)   
 [Database-Element &#40;ASSL&#41;](database-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  