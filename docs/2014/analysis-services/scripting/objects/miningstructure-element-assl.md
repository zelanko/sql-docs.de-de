---
title: MiningStructure-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningStructure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructure
helpviewer_keywords:
- MiningStructure element
ms.assetid: b943cd92-0ed8-4bd8-8fbc-7dab0534aede
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3d03e52ccb38dc35fada602b6a293d018150efd5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052090"
---
# <a name="miningstructure-element-assl"></a>MiningStructure-Element (ASSL)
  Definiert die Struktur für einen Satz von Miningmodellen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructures>  
   <MiningStructure>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <Source>...</Source>  
      <CreatedTimestamp>...</<CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <CacheMode>...</CacheMode>  
            <Columns>...</Columns>  
      <State>...</State>  
      <HoldoutActualSize>...</HoldoutActualSize>  
      <HoldoutMaxCases>...</HoldoutMaxCases>  
      <HoldoutMaxPercent>...</HoldoutMaxPercent>  
      <HoldoutSeed>...</HoldoutSeed>        
            <MiningStructurePermissions>...</<MiningStructurePermissions>  
            <MiningModels>...</MiningModels>  
            <Annotations>...</Annotations>  
   </MiningStructure>  
</MiningStructures>  
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
|Übergeordnete Elemente|[MiningStructures](../collections/miningstructures-element-assl.md)|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [CacheMode](../properties/cachemode-element-assl.md), [Sortierreihenfolge](../properties/collation-element-assl.md), [Spalten](../collections/columns-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [Beschreibung ](../properties/description-element-assl.md), [ErrorConfiguration](errorconfiguration-element-assl.md),<br /><br /> [HoldoutActualSize](../properties/holdoutactualsize-element.md),<br /><br /> [HoldoutMaxCases](../properties/holdoutmaxcases-element.md),<br /><br /> [HoldoutMaxPercent](../properties/holdoutmaxpercent-element.md),<br /><br /> [HoldoutSeed](../properties/holdoutseed-element.md),<br /><br /> [ID](../properties/id-element-assl.md), [Sprache](../properties/language-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [MiningModels](../collections/miningmodels-element-assl.md), [ MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md), [Namen](../properties/name-element-assl.md), [Quelle](../properties/source-element-binding-assl.md), [Zustand](../properties/state-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die Miningstruktur definiert die Spalten und die Bindungen. Nach dem Definieren einer Miningstruktur können Sie diese Struktur verwenden, um zahlreiche Miningmodelle zu definieren. Die Miningstruktur und jedes darin enthaltene Miningmodell können unabhängig voneinander verarbeitet werden.  
  
> [!NOTE]  
>  Die holdout-Eigenschaften `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` und `HoldoutActualSize` wurden in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] eingeführt. Sie ermöglichen es Ihnen, eine Partition in einer Miningstruktur zu definieren, die als Testsatz für alle der Struktur zugeordneten Miningmodelle fungiert. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] unterstützt diese Eigenschaften nicht. Wenn Sie versuchen, diese Eigenschaften in einer Instanz von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] zu verwenden, gibt [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
## <a name="drillthrough-to-structure-columns"></a>Drillthrough zu Strukturspalten  
 In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], ein neues Berechtigungselement hinzugefügt wurde die [MiningStructurePermissions-Element &#40;ASSL&#41; ](../collections/miningstructurepermissions-element-assl.md) Auflistung. Wenn Sie hinzufügen `AllowDrillthrough` Berechtigung sowohl dem [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md) und [MiningModelPermission](miningmodelpermission-element-assl.md) Auflistungen, Drillthrough des Miningmodells in die Struktur so aktiviert ist Dieses Mitglied einer Rolle mit `AllowDrillthrough` Berechtigungen für das Modell Datamining-Modell Abfragen und strukturspalten, die nicht im Modell enthalten waren zurückgeben können.  
  
 Daher sollten Sie zum Schutz sensibler oder persönlicher Informationen die Datenquellensicht so einrichten, dass persönliche Informationen verborgen sind, und die `AllowDrillthrough`-Berechtigung für eine Miningstruktur nur zulassen, wenn es wirklich erforderlich ist. Weitere Informationen finden Sie unter [AllowDrillThrough-Element &#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md).  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Siehe auch  
 [MiningModel-Element &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)   
 [WÄHLEN SIE &AMP;#40;DMX&AMP;#41;](/sql/dmx/select-dmx)  
  
  
