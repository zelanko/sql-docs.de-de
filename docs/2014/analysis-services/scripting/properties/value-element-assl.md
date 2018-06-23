---
title: Value-Element (ASSL) | Microsoft Docs
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
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Value
helpviewer_keywords:
- Value element
ms.assetid: a2fad411-73fd-42df-b4e1-df2cb8454182
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f350c559e78613df5e0a357b8f87dca073e1d248
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061249"
---
# <a name="value-element-assl"></a>Value-Element (ASSL)
  Enthält den Wert des übergeordneten Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AlgorithmParameter> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Value>...</Value>  
   ...  
</AlgorithmParameter>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
|Vorgänger oder übergeordnetes Element|Datentyp|  
|------------------------|---------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Jeder simpleType|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Jeder simpleType|  
|Alle sonstigen|Zeichenfolge|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md), [Anmerkung](../objects/annotation-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [ReportFormatParameter](../objects/reportformatparameter-element-asl.md), [ReportParameter](../objects/reportparameter-element-assl.md), [ServerProperty](../objects/serverproperty-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `Value` Element enthält den Wert, der das übergeordnete Objekt zugeordnet. Der erwartete Wert des `Value`-Elements hängt vom übergeordneten Element ab (siehe folgende Tabelle).  
  
|Übergeordnetes Element|Erwarteter Wert|  
|--------------------|--------------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Der Wert des Algorithmusparameters.|  
|[Anmerkung](../objects/annotation-element-assl.md)|Der Wert der Anmerkung.|  
|[KPI](../objects/kpi-element-assl.md)|Ein Multidimensional Expressions (MDX)-Ausdruck, der verwendet wird, um den Wert des Key Performance Indicator (KPI) zu berechnen.|  
|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|Der Wert des Berichtsformatparameters.|  
|[ReportParameter](../objects/reportparameter-element-assl.md)|Ein MDX-Ausdruck, der verwendet wird, um den Wert des Berichtsparameters zu berechnen.|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Der Wert der Servereigenschaft für die gerade ausgeführte Instanz.|  
  
 Die Elemente, die den übergeordneten Elementen von `Value` im AMO-Objektmodell (Analysis Management Objects) entsprechen, sind <xref:Microsoft.AnalysisServices.AlgorithmParameter>, <xref:Microsoft.AnalysisServices.Annotation>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.ReportParameter> und <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  