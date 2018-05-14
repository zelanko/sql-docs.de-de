---
title: MiningModel-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e3de4138f69df9cfaebb0d726bc9fac27dcbf629
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="miningmodel-element-assl"></a>MiningModel-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert ein einzelnes Data Mining-Modell.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModels>  
      <MiningModel>  
      <Name>...</Name>  
            <ID>...</ID>  
      <Description>...</<Descrip  
            <Algorithm>...</Algorithm>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <AlgorithmParameters>...</AlgorithmParameters>  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <Translations>...</Translations>  
      <Columns>...</Columns>  
      <State>...</State>  
      <MiningModelPermissions>...</MiningModelPermissions>  
      <Language>...</Language>  
            <Collation>...</Collation>  
            <Annotations>...</Annotations>  
            <ddl100_100:FoldingParameters>   </FoldingParameters>  
   </MiningModel>  
</MiningModels>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningModels](../../../analysis-services/scripting/collections/miningmodels-element-assl.md)|  
|Untergeordnete Elemente|[Algorithmus](../../../analysis-services/scripting/properties/algorithm-element-assl.md), [AlgorithmParameters](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md), [AllowDrillThrough](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md), [Anmerkungen](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Sortierung](../../../analysis-services/scripting/properties/collation-element-assl.md), [ Spalten](../../../analysis-services/scripting/collections/columns-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [Beschreibung](../../../analysis-services/scripting/properties/description-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [Sprache](../../../analysis-services/scripting/properties/language-element-assl.md), [ LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [MiningModelPermissions](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md), [Namen](../../../analysis-services/scripting/properties/name-element-assl.md), [Status](../../../analysis-services/scripting/properties/state-element-assl.md), [ Übersetzungen](../../../analysis-services/scripting/collections/translations-element-assl.md),<br /><br /> [FoldingParameters](../../../analysis-services/scripting/properties/foldingparameters-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das **FoldingParameters** -Element des Miningmodells ist zur internen Verwendung durch den Server bestimmt und wird nicht für DDL-Anweisungen unterstützt.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.MiningModel>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
