---
title: Assembly-Element (ASSL) | Microsoft-Dokumentation
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 38c14744eaebba8e618c7c200341c447393ce773
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151441"
---
# <a name="assembly-element-assl"></a>Assembly-Element (ASSL)
  Stellt eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly oder eine COM-dynamic Link Library (DLL) zugeordnet eine [Server](server-element-assl.md) Element oder ein [Datenbank](database-element-assl.md) Element.  
  
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
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.Assembly>.  
  
## <a name="see-also"></a>Siehe auch  
 [Server-Element &#40;ASSL&#41;](server-element-assl.md)   
 [Database-Element &#40;ASSL&#41;](database-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
