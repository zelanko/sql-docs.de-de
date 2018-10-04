---
title: MiningModelingFlag-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93b84a3509d3992ffac20ebeafcda2d4f15f2073
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153015"
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
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|None|  
|Abgeleitete Elemente|[ModelingFlag](../objects/modelingflag-element-assl.md) ([ModelingFlags](../collections/modelingflags-element-assl.md) Auflistung von [MiningModelColumn](miningmodelcolumn-data-type-assl.md) oder [ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Der Flagname enthält möglicherweise Leerzeichen. Die vom eigenen System unterstützten Werte werden in der folgenden Tabelle aufgelistet.  
  
|value|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|Die Spalte sollte so modelliert werden, dass sie unabhängig von den Werten in der Spalte über zwei Zustände verfügt: fehlend und nicht-fehlend. Dies ist besonders nützlich für Spalten in einer geschachtelten Tabelle, in denen es selten fallübergreifende Werte gibt.|  
|*NICHT NULL*|Die Spalte kann keine NULL-Werte akzeptieren.|  
|*REGRESSOR*|Die Spalte gibt Regressorwerte für Testfälle an.|  
  
 Zusätzliche anbieterspezifische Flags können verwendet werden, wenn Drittanbieter-OLE DB oder Data Mining-Anbieter für die Instanz von aggregiert wurden [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Ein eng verwandtes Element im AMO-Objektmodell (Analysis Management Objects) ist <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
