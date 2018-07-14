---
title: MiningModel-Element (ASSL) | Microsoft-Dokumentation
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
- MiningModel Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModel
helpviewer_keywords:
- MiningModel element
ms.assetid: a61d935f-c8f6-457d-ad0c-44f58bb286f5
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ba98443b953f4107b209dd06af74349a81bb2a3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224540"
---
# <a name="miningmodel-element-assl"></a>MiningModel-Element (ASSL)
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
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningModels](../collections/miningmodels-element-assl.md)|  
|Untergeordnete Elemente|[Algorithmus](../properties/algorithm-element-assl.md), [AlgorithmParameters](algorithmparameter-element-assl.md), [AllowDrillThrough](../properties/allowdrillthrough-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [Sortierreihenfolge](../properties/collation-element-assl.md), [ Spalten](../collections/columns-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [Sprache](../properties/language-element-assl.md), [ LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [MiningModelPermissions](../collections/miningmodelpermissions-element-assl.md), [Namen](../properties/name-element-assl.md), [Zustand](../properties/state-element-assl.md), [ Übersetzungen](../collections/translations-element-assl.md),<br /><br /> [FoldingParameters](../properties/foldingparameters-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das `FoldingParameters`-Element des Miningmodells ist zur internen Verwendung durch den Server bestimmt und wird nicht für DDL-Anweisungen unterstützt.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.MiningModel>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
