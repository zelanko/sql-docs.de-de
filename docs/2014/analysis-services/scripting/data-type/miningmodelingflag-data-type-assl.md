---
title: MiningModelingFlag-Datentyp (ASSL) | Microsoft Docs
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
- MiningModelingFlag Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 32ee744bdfcd084c4be88511ecba025ca9a270de
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159868"
---
# <a name="miningmodelingflag-data-type-assl"></a>MiningModelingFlag-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der die verfügbaren Modellierungsflags für eine [ModelingFlag](../objects/modelingflag-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|Zeichenfolge (Enumeration)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
|Abgeleitete Elemente|[ModelingFlag](../objects/modelingflag-element-assl.md) ([ModelingFlags](../collections/modelingflags-element-assl.md) Auflistung von [MiningModelColumn](miningmodelcolumn-data-type-assl.md) oder [ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Der Flagname enthält möglicherweise Leerzeichen. Die vom eigenen System unterstützten Werte werden in der folgenden Tabelle aufgelistet.  
  
|value|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|Die Spalte sollte so modelliert werden, dass sie unabhängig von den Werten in der Spalte über zwei Zustände verfügt: fehlend und nicht-fehlend. Dies ist besonders nützlich für Spalten in einer geschachtelten Tabelle, in denen es selten fallübergreifende Werte gibt.|  
|*NOT NULL*|Die Spalte kann keine NULL-Werte akzeptieren.|  
|*REGRESSOR*|Die Spalte gibt Regressorwerte für Testfälle an.|  
  
 Zusätzliche anbieterspezifische Flags können verwendet werden, wenn eines Drittanbieters OLE DB- oder Data Mining-Anbieter für die Instanz von aggregiert wurden [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Ein eng verwandtes Element im AMO-Objektmodell (Analysis Management Objects) ist <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  