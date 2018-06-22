---
title: Data-Element (ASSL) | Microsoft Docs
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
- Data Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Data
helpviewer_keywords:
- Data element
ms.assetid: e52b1961-7e11-4029-8ab1-84d275845067
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5a3ff1b93efe374b9ddc8b080de143550aae8388
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061032"
---
# <a name="data-element-assl"></a>Data-Element (ASSL)
  Enthält (in der Auflistung der untergeordneten [Blockelement &#40;ASSL&#41; ](block-element-assl.md) Elemente) des binären Inhalts eine [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<File xsi:type="ClrAssemblyFile">  
   ...  
   <Data xsi:type="DataBlock">...</Data>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[DataBlock](../data-type/datablock-data-type-assl.md)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Datei](file-element-assl.md) des Typs [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das das übergeordnete Element des entspricht `Data` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Siehe auch  
 [Assembly-Element &#40;ASSL&#41;](assembly-element-assl.md)   
 [ClrAssembly-Datentyp &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Dateien Element &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [Element blockiert &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  