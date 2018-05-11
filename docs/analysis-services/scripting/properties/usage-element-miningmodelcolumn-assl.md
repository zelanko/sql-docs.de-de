---
title: Usage-Element (MiningModelColumn) (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a7e3326deb1ea9c67b3b64daa5f01efef817c4de
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="usage-element-miningmodelcolumn-assl"></a>Usage-Element (MiningModelColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt, wie die zugeordnete Spalte im übergeordneten [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Key*|Die Spalte ist eine Schlüsselspalte.|  
|*Eingabe*|Die Spalte ist eine Eingabespalte.|  
|*Predict*|Die Spalte ist eine Vorhersagespalte.|  
|*PredictOnly*|Die Spalte ist nur eine Vorhersagespalte.|  
|*InclusionThresholdSetting*|Die Spalte wird nicht vom Modell verwendet.<br /><br /> **\*\* Warnung \*\*** , wenn der Wert der Auslastung des "None" ist, Analysis Services sendet keine ausnahmslos an den Server in der Standardeinstellung; daher wird das Usage-Attribut nicht in der Anforderung/Antwort enthalten.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **Verwendung** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningModelColumnUsages>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
