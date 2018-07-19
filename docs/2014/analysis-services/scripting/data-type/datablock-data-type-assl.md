---
title: DataBlock-Datentyp (ASSL) | Microsoft-Dokumentation
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
- DataBlock Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataBlock
helpviewer_keywords:
- DataBlock data type
ms.assetid: 4192b388-613a-472b-881c-f9c02215aa81
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 167af587de6f06d283ec29f8afbc0fedb2ebc99e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211960"
---
# <a name="datablock-data-type-assl"></a>DataBlock-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der eine von Datenblöcken verwendet Auflistung, um die binären Inhalte speichern eine [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataBlock>  
   <Blocks>...</Blocks>  
</DataBlock>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Blöcke](../collections/blocks-element-assl.md)|  
|Abgeleitete Elemente|[Daten](../objects/data-element-assl.md) Element [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) Typ ([Dateien](../collections/files-element-assl.md) Auflistung von [ClrAssembly](assembly-data-type-assl.md) Typ)|  
  
## <a name="see-also"></a>Siehe auch  
 [Assembly-Element &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [File Element &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Element sperren &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
