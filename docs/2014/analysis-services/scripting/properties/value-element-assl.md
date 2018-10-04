---
title: Wert-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d338b8607d8515bf89183eeadd24252c55af8fc5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218190"
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
|Standardwert|None|  
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
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `Value` Element enthält den Wert, der das übergeordnete Objekt zugeordnet. Der erwartete Wert des `Value`-Elements hängt vom übergeordneten Element ab (siehe folgende Tabelle).  
  
|Übergeordnetes Element|Erwarteter Wert|  
|--------------------|--------------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Der Wert des Algorithmusparameters.|  
|[Anmerkung](../objects/annotation-element-assl.md)|Der Wert der Anmerkung.|  
|[KPI](../objects/kpi-element-assl.md)|Ein Multidimensional Expressions (MDX)-Ausdruck, der verwendet wird, um den Wert des Key Performance Indicator (KPI) zu berechnen.|  
|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|Der Wert des Berichtsformatparameters.|  
|[ReportParameter-Objekt](../objects/reportparameter-element-assl.md)|Ein MDX-Ausdruck, der verwendet wird, um den Wert des Berichtsparameters zu berechnen.|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Der Wert der Servereigenschaft für die gerade ausgeführte Instanz.|  
  
 Die Elemente, die den übergeordneten Elementen von `Value` im AMO-Objektmodell (Analysis Management Objects) entsprechen, sind <xref:Microsoft.AnalysisServices.AlgorithmParameter>, <xref:Microsoft.AnalysisServices.Annotation>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.ReportParameter> und <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
