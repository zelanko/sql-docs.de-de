---
title: DisplayFolder-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DisplayFolder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DisplayFolder
helpviewer_keywords:
- DisplayFolder element
ms.assetid: 55184c02-03e7-4d6c-b87a-d4d34bc11d0e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 73de197b50ebd3636cb97e6a011fee1e8c3a71af
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220100"
---
# <a name="displayfolder-element-assl"></a>DisplayFolder-Element (ASSL)
  Gibt den Ordner an, in dem das übergeordnete Element aufgelistet werden soll. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Anwendungen für Entwickler und Administratoren unterstützen möglicherweise die Verwendung von anzeigeordnern für die visuelle Kategorisierung mehrerer Elemente.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CalculationProperty> <!-- or Hierarchy, Kpi, Measure, Translation -->  
   ...  
   <DisplayFolder>...</DisplayFolder>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CalculationProperty](../objects/calculationproperty-element-assl.md), [Hierarchie](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [Measure](../objects/measure-element-assl.md), [Übersetzung](../objects/translation-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 In größeren Cubes gibt es möglicherweise Hunderte von Measures und Hierarchien. Die `DisplayFolder` -Eigenschaft definiert die benutzerdarstellung auf dem Client. Der Wert des der `DisplayFolder` Eigenschaft kann eine der folgenden Optionen enthalten:  
  
-   Kann leer sein, wobei angegeben wird, dass das Measure nicht zu einem Ordner gehört.  
  
-   Kann einen einzelnen Ordnernamen enthalten, wobei angegeben wird, dass das Measure als zu einem Ordner mit diesem Namen gehörend gerendert werden sollte.  
  
-   Kann mehrere Ordnernamen an, getrennt durch einen umgekehrten Schrägstrich enthalten (\\), die eine eingebettete Ordnerhierarchie angibt.  
  
 Die `DisplayFolder` Eigenschaft gilt für `CalculationProperty` Elemente, wenn der Wert des [CalculationType](calculationtype-element-assl.md) nastaven NA hodnotu *Member*.  
  
 Die Elemente, die den übergeordneten Elementen von `DisplayFolder` im AMO-Objektmodell (Analysis Management Objects) entsprechen, sind <xref:Microsoft.AnalysisServices.CalculationProperty>, <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.Measure> und <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Siehe auch  
 [CalculationProperties-Element &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript-Element &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts-Element &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
