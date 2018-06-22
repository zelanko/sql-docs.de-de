---
title: Block-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Block Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Block
helpviewer_keywords:
- Block element
ms.assetid: f45c32ae-e4e0-465a-9564-9ccfb10a858f
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e382ba38c41bc68b3d49b0397cdc3fe3f2dcf0ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148180"
---
# <a name="block-element-assl"></a>Block-Element (ASSL)
  Enthält alles oder einen Teil des binären Inhalts eine [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Blocks>  
   <Block>...</Block>  
</Blocks>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Base64Binary|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Blöcke](../collections/blocks-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="see-also"></a>Siehe auch  
 [Assembly-Element &#40;ASSL&#41;](assembly-element-assl.md)   
 [ClrAssembly-Datentyp &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Dateien Element &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [Datei Element &#40;ASSL&#41;](file-element-assl.md)   
 [ClrAssemblyFile-Datentyp &#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [Datenelement &#40;ASSL&#41;](data-element-assl.md)   
 [DataBlock-Datentyp &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  