---
title: -Element (ASSL)-Dateien | Microsoft-Dokumentation
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
- Files Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Files
helpviewer_keywords:
- Files element
ms.assetid: 8a1327cb-1f60-42a7-b8ef-213d45a63e55
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d4ed9199f5b715c00e70da39e1742a2638cf67a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196040"
---
# <a name="files-element-assl"></a>Files-Element (ASSL)
  Enthält die Auflistung der [Datei](../objects/file-element-assl.md) Elemente, aus denen ein [ClrAssembly](../data-type/assembly-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Assembly xsi:type="ClrAssembly">  
   ...  
   <Files>  
      <File xsi:type="ClrAssemblyFile">...</File>  
   </Files>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Assembly](../objects/assembly-element-assl.md) des Typs [ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|Untergeordnete Elemente|[Datei](../objects/file-element-assl.md) des Typs [clrassemblyfile-Objekts](../data-type/clrassemblyfile-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.ClrAssemblyFileCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Server-Element &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Database-Element &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Assemblies-Element &#40;ASSL&#41;](assemblies-element-assl.md)   
 [Datenelement &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [DataBlock-Datentyp &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Element blockiert &#40;ASSL&#41;](blocks-element-assl.md)   
 [Element sperren &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [ComAssembly-Datentyp &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
