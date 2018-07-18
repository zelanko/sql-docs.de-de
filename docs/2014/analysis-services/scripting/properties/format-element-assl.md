---
title: Format-Element (ASSL) | Microsoft-Dokumentation
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
- Format Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Format
helpviewer_keywords:
- Format element
ms.assetid: 881ea707-52a7-46f7-ba16-ac2ec44eca22
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b8b5fdae50b38c81ad29143887717b412084c2c2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169501"
---
# <a name="format-element-assl"></a>Format-Element (ASSL)
  Enthält das erforderliche Format von der [DataItem](../data-type/dataitem-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataItem-Objekt](../data-type/dataitem-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Zulässige Werte für die `Format` -Element sind Microsoft Office Excel-Formate und die Zeichenfolgen *TrimRight*, *TrimLeft*, *TrimAll*, und  *TrimNone*. Der Standardwert für Kürzungen ist *TrimRight* .  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|Eine beliebige Excel-Formatzeichenfolge|Daten werden gemäß der angegebenen benannten oder benutzerdefinierten Formatzeichenfolge formatiert. Es kann eine beliebige Formatzeichenfolge, die Excel unterstützt, bereitgestellt werden.|  
|*TrimAll*|Die Daten werden auf der linken und auf der rechten Seite gekürzt.|  
|*TrimLeft*|Die Daten werden auf der linken Seite gekürzt.|  
|*TrimNone*|Die Daten werden nicht gekürzt.|  
|*TrimRight*|Die Daten werden auf der rechten Seite gekürzt.|  
  
 Das Element, das dem übergeordneten entspricht `Format` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
