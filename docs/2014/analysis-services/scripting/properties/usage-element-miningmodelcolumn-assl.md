---
title: Usage-Element (MiningModelColumn) (ASSL) | Microsoft-Dokumentation
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
- Usage Element (MiningModelColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: 435a857e-37a9-434e-9de1-354f1ff2993f
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a6767c4c5ac535ac603cc6182cbe645088c8ac05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265298"
---
# <a name="usage-element-miningmodelcolumn-assl"></a>Usage-Element (MiningModelColumn) (ASSL)
  Beschreibt, wie die zugeordnete Spalte im übergeordneten [MiningStructure](../objects/miningstructure-element-assl.md) verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Key*|Die Spalte ist eine Schlüsselspalte.|  
|*Eingabe*|Die Spalte ist eine Eingabespalte.|  
|*Predict*|Die Spalte ist eine Vorhersagespalte.|  
|*PredictOnly*|Die Spalte ist nur eine Vorhersagespalte.|  
|*Keine*|Die Spalte wird nicht vom Modell verwendet. **Warnung:** Wenn der Wert der Auslastung des "None", Analysis Services sendet keine einen beliebigen Wert an den Server in der Standardeinstellung; das Usage-Attribut ist daher nicht enthalten, in der Anforderung/Antwort.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `Usage` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningModelColumnUsages>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
