---
title: FoldingParameters-Element (ASSL) | Microsoft Docs
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
topic_type:
- apiref
f1_keywords:
- FoldIndex
- FoldCount
- MaxCases
- FoldingParameters
- FoldTargetAttribute
helpviewer_keywords:
- FoldingParameters element
ms.assetid: 5f5c5a3e-4aed-48fb-bca5-e67f421bef2f
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 12cae8f4ad02f57f63fd168ff41503f233f53c4c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162379"
---
# <a name="foldingparameters-element-assl"></a>FoldingParameters-Element (ASSL)
  Gibt an, die vom verwendeten Parameter den [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Server, wenn sie die übergreifende Überprüfung von Miningmodellen ausführt.  
  
> [!NOTE]  
>  Diese Parameter dienen nur zur internen Verwendung. Die hier bereitgestellten Informationen dienen lediglich als Referenz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModel>  
   ...  
   <ddl100_100:FoldingParameters>...  
      <ddl100_100:FoldIndex>...</ddl100_100:FoldIndex>  
      <ddl100_100:FoldCount>...</ddl100_100:FoldCount>  
      <ddl100_100:MaxCases>...</ddl100_100:MAxCases>  
      <ddl100_100:FoldTargetAttribute>...</ddl100_100:FoldTargetAttribute  
...</ddl100_100:FoldingParameters>  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|*FoldIndex*|Ganze Zahl, die die Anfangsposition der zur Kreuzvalidierung verwendeten Partition angibt.|  
|*FoldCount*|Ganze Zahl, die die Anzahl von Partitionen im Modell nach der Kreuzvalidierung angibt.|  
|*MaxCases*|Ganze Zahl, die angibt, wie viele Modellfälle zur Kreuzvalidierung verwendet werden.<br /><br /> Ein Wert von 0 gibt an, dass alle Fälle verwendet werden.|  
|*FoldTargetAttribute*|Zeichenfolge, die die ID der Modellsspalte angibt, die das vorhersagbare Attribut enthält.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Untergeordnete Elemente|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaften sind nur zur internen Verwendung, und werden nicht zur Verwendung in DDL-Anweisungen unterstützt.  
  
 Informationen zur Verwendung von kreuzvalidierung in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], finden Sie unter [Measures in der übergreifenden Überprüfungsbericht](../../data-mining/measures-in-the-cross-validation-report.md).  
  
 Informationen zum Ausführen der kreuzvalidierung mit [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gespeicherte Prozeduren finden Sie unter [Data Mining Stored Procedures &#40;Analysis Services – Data Mining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
