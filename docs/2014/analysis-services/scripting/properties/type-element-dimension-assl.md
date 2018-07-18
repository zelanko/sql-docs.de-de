---
title: Type-Element (Dimension) (ASSL) | Microsoft-Dokumentation
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6afa3b273200630a4d36e0c4df679c58efb6bd5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283946"
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
|*Tarife*|Die Dimension enthält Wechselkursattribute.|  
|*Channel*|Die Dimension enthält Kanalattribute.|  
|*Heraufstufung*|Die Dimension enthält höherstufungsbezogene Attribute.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 Das Element, das dem übergeordneten entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
