---
title: SourceColumnID-Element (ASSL) | Microsoft-Dokumentation
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
- SourceColumnID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SourceColumnID
helpviewer_keywords:
- SourceColumnID element
ms.assetid: 715c0be7-aa07-4dff-a909-9738224941ec
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 523977b881e9e8357b32cd606252d0a758d3b46a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281776"
---
# <a name="sourcecolumnid-element-assl"></a>SourceColumnID-Element (ASSL)
  Enthält den Bezeichner (ID) der Quellminingstruktur-Spalte in den Vorgänger [MiningStructure](../objects/miningstructure-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <SourceColumnID>...</SourceColumnID>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des der `SourceColumnID` Element entspricht dem Bezeichner der Miningstrukturspalte in der [Spalten](../collections/columns-element-assl.md) Auflistung des übergeordneten Elements `MiningStructure`.  
  
 Das Element, das dem übergeordneten entspricht `SourceColumnID` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningModelColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
