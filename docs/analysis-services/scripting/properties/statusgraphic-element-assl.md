---
title: StatusGraphic-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0824eb04dc7d9558c4f5c8ff9531014e007a7a64
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="statusgraphic-element-assl"></a>StatusGraphic-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die empfohlene grafische Darstellung des Status des [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md) -Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Kpi>  
   ...  
   <StatusGraphic>...</StatusGraphic>  
   ...  
</Kpi>  
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
|Übergeordnetes Element|[KPI](../../../analysis-services/scripting/objects/kpi-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Verkehrsampel - Single*|Verkehrsampel (einzeln)|  
|*Verkehrsampel - mehrere*|Verkehrsampel (mehrere)|  
|*Straßenschilder*|Straßenschilder|  
|*Messgerät - aufsteigend*|Messgerät|  
|*Messgerät - absteigend*|Umgekehrter Maßstab|  
|*Thermometer*|Thermometer|  
|*Zylinder*|Zylinder|  
|*Smileysymbol*|Gesicht|  
  
 Das Element, das das übergeordnete Element des entspricht **StatusGraphic** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
