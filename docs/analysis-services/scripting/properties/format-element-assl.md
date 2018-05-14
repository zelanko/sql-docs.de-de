---
title: Format-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 34220d27f4a0ca1f30b67b5066f5a06877816652
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="format-element-assl"></a>Format-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält das erforderliche Format von der [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Zulässige Werte für das **Format** -Element sind Microsoft Office Excel-Formate und die Zeichenfolgen *TrimRight*, *TrimLeft*, *TrimAll*und *TrimNone*. Der Standardwert für Kürzungen ist *TrimRight* .  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|Eine beliebige Excel-Formatzeichenfolge|Daten werden gemäß der angegebenen benannten oder benutzerdefinierten Formatzeichenfolge formatiert. Es kann eine beliebige Formatzeichenfolge, die Excel unterstützt, bereitgestellt werden.|  
|*TrimAll*|Die Daten werden auf der linken und auf der rechten Seite gekürzt.|  
|*TrimLeft*|Die Daten werden auf der linken Seite gekürzt.|  
|*TrimNone*|Die Daten werden nicht gekürzt.|  
|*TrimRight*|Die Daten werden auf der rechten Seite gekürzt.|  
  
 Das Element, das das übergeordnete Element des entspricht **Format** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
