---
title: Content-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Content Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Content
helpviewer_keywords:
- Content element
ms.assetid: 221addef-2f88-49c5-b8f5-9eee330497a9
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 98d2de4a0ce93e857a63ebd9fe79dd18d0f9a86e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049984"
---
# <a name="content-element-assl"></a>Content-Element (ASSL)
  Beschreibt den Inhalt der Spalte in der [MiningStructure](../objects/miningstructure-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Diese Enumeration beschreibt den Inhaltstyp, der von einer Miningstrukturspalte dargestellt wird, und kann je nach Bedarf durch Mining-Algorithmusanbieter erweitert werden. Weitere Informationen zu Inhaltstypen finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](../../data-mining/content-types-data-mining.md).  
  
 Die in der folgenden Tabelle aufgelisteten Werte werden i. d. R. von allen Mining-Algorithmusanbietern unterstützt.  
  
|value|Description|  
|-----------|-----------------|  
|*Diskrete*|Diese Spalte enthält diskrete Werte.|  
|*Fortlaufende*|Die Werte für die Spalte definieren einen fortlaufenden Satz von numerischen Daten.|  
|*Diskretisiert*|Die Werte in der Spalte stellen Gruppen (oder Buckets) von Werten dar, die von einer kontinuierlichen Spalte abgeleitet sind.|  
|*Sortiert*|Die Werte für die Spalte definieren eine geordnete Menge.|  
|*Zyklisch*|Die Werte für die Spalte definieren eine zyklisch geordnete Menge.|  
|*Wahrscheinlichkeit*|Die Werte für die Spalte geben eine Wahrscheinlichkeit für die Spalten in der [ClassifiedColumns](../collections/columns-element-assl.md) Element des übergeordneten Elements `ScalarMiningStructureColumn`.|  
|*Variance*|Die Werte für die Spalte geben eine Varianz für die Spalten an, die im `ClassifiedColumns`-Element der übergeordneten `ScalarMiningStructureColumn` enthalten sind.|  
|*StdDev*|Die Werte für die Spalte geben eine Standardabweichung für die Spalten an, die im `ClassifiedColumns`-Element der übergeordneten `ScalarMiningStructureColumn` enthalten sind.|  
|*ProbabilityVariance*|Die Werte für die Spalte geben eine Varianz der Wahrscheinlichkeit für die Spalten an, die im `ClassifiedColumns`-Element der übergeordneten `ScalarMiningStructureColumn` enthalten sind.|  
|*ProbabilityStdDev*|Die Werte für die Spalte geben eine Standardabweichung der Wahrscheinlichkeit für die Spalten an, die im `ClassifiedColumns`-Element der übergeordneten `ScalarMiningStructureColumn` enthalten sind.|  
|*Unterstützung*|Die Werte für die Spalte geben Supportinformationen für die Spalten an, die im `ClassifiedColumns`-Element der übergeordneten `ScalarMiningStructureColumn` enthalten sind. **Hinweis:** dieser Spalte wird als Teil des Standards für Mining-Algorithmusanbietern von Drittanbietern bereitgestellt. **Hinweis:** Microsoft bereitgestellte Algorithmen haben keine Verwendung für diese Spalte. <br /><br /> zugreifen.|  
|*Key*|Die Spalte ist eine Schlüsselspalte. **Hinweis:** diesen Inhaltstyp gilt nur für Schlüsselspalten in dem die `IsKey` -Elementgruppe ist `True`.|  
  
 Zusätzlich zu diesen Standardwerten mining-Algorithmusanbietern enthaltene [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützen die Werte in der folgenden Tabelle.  
  
|value|Description|  
|-----------|-----------------|  
|*Tastenkombination*|Diese Spalte ist eine Schlüsselspalte, und die Werte für diese Spalte stellen eine Folge von Ereignissen dar. **Hinweis:** diesen Inhaltstyp gilt nur für Schlüsselspalten in dem die `IsKey` -Elementgruppe ist `True`.|  
|*Die Schlüsselzeit*|Diese Spalte ist eine Schlüsselspalte, und die Werte für diese Spalte stellen Zeitmaßeinheiten dar. **Hinweis:** diesen Inhaltstyp gilt nur für Schlüsselspalten in dem die `IsKey` -Elementgruppe ist `True`.|  
|*Sequenz*|Die Werte für diese Spalte stellen eine Folge von Ereignissen dar.|  
|*Uhrzeit*|Die Werte für die Spalte stellen Zeitmaßeinheiten dar.|  
  
 Die Enumeration, die den zulässigen Werten für die entsprechende `Content` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [ClassifiedColumns-Element &#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  