---
title: DefaultScript-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DefaultScript Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultScript
helpviewer_keywords:
- DefaultScript element
ms.assetid: 60716e63-2d64-4774-9ac9-253efe612fa5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a1eef79aabede1198c45c9f5481f13bd597db42c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152740"
---
# <a name="defaultscript-element-assl"></a>DefaultScript-Element (ASSL)
  Identifiziert das Standard- [MdxScript](../objects/mdxscript-element-assl.md) Element in der [MdxScripts](../collections/mdxscripts-element-assl.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MdxScript>  
   ...  
   <DefaultScript>...</DefaultScript>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|`True`|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MdxScript](../objects/mdxscript-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das Einrichten des Werts für `DefaultScript` auf `True` für ein Skript setzt den Wert für `DefaultScript` auf `False` für alle anderen `MdxScript`-Elemente in der `MdxScripts`-Auflistung.  
  
 Das Element, das dem übergeordneten entspricht `DefaultScript` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
