---
title: Ordinal-Element (ASSL) | Microsoft Docs
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
- Ordinal Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Ordinal
helpviewer_keywords:
- Ordinal element
ms.assetid: 64e68ad5-439c-4c1d-9df4-ee90c56761b4
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9c9328a33db828af8bb7b0b129574d8ba855433e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048571"
---
# <a name="ordinal-element-assl"></a>Ordinal-Element (ASSL)
  Gibt die Ordinalzahl an, an die in Auflistungen wie Schlüsseln und Übersetzungen gebunden wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Ordinal>...</Ordinal>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Integer|  
|Standardwert|`0`|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AttributeBinding](../data-type/binding-data-type-assl.md), [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 `AttributeBinding` und `CubeAttributeBinding` Elemente, in denen die [Typ](type-element-binding-assl.md) festgelegt wird entweder *Schlüssel* oder *Übersetzung* gebunden werden kann, um ein Attribut, das wiederum an eine Auflistung von gebunden ist Spalten in den Daten die Datenquellensicht an. Der Wert des `Ordinal`-Elements bestimmt, auf welche Spalte sich `AttributeBinding` oder `CubeAttributeBinding` in der Auflistung beziehen.  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `Ordinal` im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.AttributeBinding> und <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  