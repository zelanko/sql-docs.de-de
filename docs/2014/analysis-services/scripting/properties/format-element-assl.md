---
title: Format-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ed7cf229d4ef65e324a59d2d9292948ae530147
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228010"
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
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataItem-Objekt](../data-type/dataitem-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
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
  
  
