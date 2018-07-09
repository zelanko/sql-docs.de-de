---
title: File-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- File
helpviewer_keywords:
- File element
ms.assetid: 21c70707-d2f8-4040-9acb-cbce23076bcc
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 03b78545b1df04192a69dffa1a49733509b99700
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155352"
---
# <a name="file-element-assl"></a>File-Element (ASSL)
  Definiert eine der Dateien, aus denen ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [ClrAssembly](../data-type/assembly-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Files>  
   <File xsi:type="ClrAssemblyFile">...</File>  
</Files>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[Clrassemblyfile-Objekts](../data-type/clrassemblyfile-data-type-assl.md)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Dateien](../collections/files-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `Files` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Siehe auch  
 [Server-Element &#40;ASSL&#41;](server-element-assl.md)   
 [Database-Element &#40;ASSL&#41;](database-element-assl.md)   
 [Assemblies-Element &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Assembly-Element &#40;ASSL&#41;](assembly-element-assl.md)   
 [ClrAssembly-Datentyp &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Datenelement &#40;ASSL&#41;](data-element-assl.md)   
 [DataBlock-Datentyp &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Element blockiert &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Element sperren &#40;ASSL&#41;](block-element-assl.md)   
 [ComAssembly-Datentyp &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
