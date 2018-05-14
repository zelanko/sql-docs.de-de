---
title: MiningModelingFlag-Datentyp (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ffbf5b43efb72e32b49cf70a1a114a4b2c07b3de
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="miningmodelingflag-data-type-assl"></a>MiningModelingFlag-Datentyp (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert einen Grunddatentyp, der die verfügbaren Modellierungsflags für ein [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) -Element darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Basisdatentypen|Zeichenfolge (Enumeration)|  
|Abgeleitete Datentypen|Keine|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keine|  
|Untergeordnete Elemente|Keine|  
|Abgeleitete Elemente|[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) ([ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md) , Auflistung von [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md) oder [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Der Flagname enthält möglicherweise Leerzeichen. Die vom eigenen System unterstützten Werte werden in der folgenden Tabelle aufgelistet.  
  
|Wert|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|Die Spalte sollte so modelliert werden, dass sie unabhängig von den Werten in der Spalte über zwei Zustände verfügt: fehlend und nicht-fehlend. Dies ist besonders nützlich für Spalten in einer geschachtelten Tabelle, in denen es selten fallübergreifende Werte gibt.|  
|*NOT NULL*|Die Spalte kann keine NULL-Werte akzeptieren.|  
|*REGRESSOR*|Die Spalte gibt Regressorwerte für Testfälle an.|  
  
 Zusätzliche anbieterspezifische Flags können verwendet werden, wenn OLE-DB von Dritten oder Data Mining-Anbieter auf der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]aggregiert wurden.  
  
 Ein eng verwandtes Element im AMO-Objektmodell (Analysis Management Objects) ist <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
