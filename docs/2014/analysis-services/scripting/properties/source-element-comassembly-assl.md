---
title: Source-Element (ComAssembly) (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Source Element (ComAssembly)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 5c9209e8-ace6-4688-a64d-4987a7648ab9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7c6259d5bec6c2c1e371df5d9412ccdbc5489a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106510"
---
# <a name="source-element-comassembly-assl"></a>Source-Element (ComAssembly) (ASSL)
  Enthält den Dateinamen oder den programmtechnischen Bezeichner (ProgID) für eine COM-Komponente (Component Object Model).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ComAssembly>  
   ...  
   <Source>...</Source>  
   ...  
</ComAssembly>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ComAssembly](../data-type/assembly-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `Source` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>Siehe auch  
 [Assembly-Element &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [ClrAssembly-Datentyp &#40;ASSL&#41;](../data-type/clrassembly-data-type-assl.md)   
 [Assemblies-Element &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Database-Element &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Server-Element &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
