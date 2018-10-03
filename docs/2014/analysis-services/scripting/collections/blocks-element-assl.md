---
title: -Element (ASSL) blockiert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Blocks Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Blocks
helpviewer_keywords:
- Blocks element
ms.assetid: d6fd4e6b-b5bd-43cd-9c28-48af57cf977c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b1030bf5efbfb86319d83a19913f58d834f85fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082720"
---
# <a name="blocks-element-assl"></a>Blocks-Element (ASSL)
  Enthält die Auflistung der Blöcke mit binären Daten, die den binären Inhalt darstellen einer [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Data xsi:type="DataBlock">  
   ...  
   <Blocks>  
      <Block>...</Block>  
   </Blocks>  
   ...  
</File>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Daten](../objects/data-element-assl.md) des Typs [DataBlock](../data-type/datablock-data-type-assl.md)|  
|Untergeordnete Elemente|[Block](../objects/block-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `Blocks` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Siehe auch  
 [Assembly-Element &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [ClrAssembly-Datentyp &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Dateien Element &#40;ASSL&#41;](files-element-assl.md)   
 [File Element &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [ClrAssemblyFile-Datentyp &#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [Datenelement &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [DataBlock-Datentyp &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Blocks-Element](blocks-element-assl.md)   
 [Element sperren &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
