---
title: Geben Sie-Element (Dimension) (ASSL) | Microsoft Docs
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
- Type Element (Dimension)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 6a2798b1-26c7-49d8-b556-e681c69d9574
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 582d5b2052f2681630c5f0cd86facacd5e7cfc91
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057027"
---
# <a name="type-element-dimension-assl"></a>Type-Element (Dimension) (ASSL)
  Stellt Informationen über den Inhalt der Dimension bereit.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Dimension>  
      ...  
   <Type>...</Type>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Reguläre*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Dimension](../objects/dimension-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Einige Werte für `Type`, z. B. *Konten*, bestimmen spezifisches Verhalten.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Reguläre*|Die Dimension ist eine reguläre Dimension.|  
|*Uhrzeit*|Die Dimension ist eine Zeitdimension. **Hinweis:** dieser Wert gibt an, dass die Dimension für Zeitdimensionen spezifische Funktionalität unterstützt.|  
|*Geography*|Die Dimension enthält geografische Attribute.|  
|*Organisation*|Die Dimension enthält Organisationsattribute.|  
|*BillOfMaterials*|Die Dimension enthält Stücklistenattribute.|  
|*Konten*|Die Dimension enthält kontobezogene Attribute. **Hinweis:** dieser Wert gibt an, dass die Dimension für kontodimensionen spezifische Funktionalität unterstützt.|  
|*Kunden*|Die Dimension enthält kundenbezogene Attribute.|  
|*Produkte*|Die Dimension enthält produktbezogene Attribute.|  
|*Szenario*|Die Dimension enthält szenariobezogene Attribute.|  
|*Quantitative*|Die Dimension enthält quantitative Attribute.|  
|*Hilfsprogramm*|Die Dimension enthält Hilfsprogrammattribute.|  
|*Währung*|Die Dimension enthält Währungsattribute.|  
|*Raten*|Die Dimension enthält Wechselkursattribute.|  
|*Channel*|Die Dimension enthält Kanalattribute.|  
|*Promotion*|Die Dimension enthält höherstufungsbezogene Attribute.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 Das Element, das das übergeordnete Element des entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  