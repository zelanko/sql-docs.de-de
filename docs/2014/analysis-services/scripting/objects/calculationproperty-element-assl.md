---
title: CalculationProperty-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CalculationProperty Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalculationProperty
helpviewer_keywords:
- CalculationProperty element
ms.assetid: 5f0b4cfc-7d25-4c01-a517-cc2e89859be3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cfd8d16293314db4a9ca382d6a4042dd0a493f06
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161700"
---
# <a name="calculationproperty-element-assl"></a>CalculationProperty-Element (ASSL)
  Enthält eine Auflistung von Benutzeroberflächeneigenschaften für eine Berechnung, die in verwendet eine [MdxScript](mdxscript-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CalculationProperties>  
   <CalculationProperty>  
      <CalculationReference>...</CalculationReference>  
      <CalculationType>...</CalculationType>  
      <Translations>...</Translations>  
      <Description>...</Description>  
      <Visible>...</Visible>  
      <SolveOrder>...</SolveOrder>  
      <FormatString>...</FormatString>  
      <ForeColor>...</ForeColor>  
      <BackColor>...</BackColor>  
            <FontName>...</FontName>  
            <FontSize>...</FontSize>  
            <FontFlags>...</FontFlags>  
            <NonEmptyBehavior>...</NonEmptyBehavior>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <DisplayFolder>...</DisplayFolder>  
   </CalculationProperty>  
</CalculationProperties>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CalculationProperties](../collections/calculationproperties-element-assl.md)|  
|Untergeordnete Elemente|[AssociatedMeasureGroupID](../properties/id-element-assl.md), [BackColor](../properties/backcolor-element-assl.md), [CalculationReference](../properties/calculationreference-element-assl.md), [CalculationType](../properties/calculationtype-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [FontFlags](../properties/fontflags-element-assl.md), [FontName](../properties/name-element-assl.md), [FontSize](../properties/fontsize-element-assl.md), [ForeColor](../properties/forecolor-element-assl.md), [FormatString](../properties/formatstring-element-assl.md), [NonEmptyBehavior](../properties/nonemptybehavior-element-assl.md), [SolveOrder](../properties/solveorder-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md), [sichtbar](../properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
