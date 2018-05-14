---
title: FoldingParameters-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 51a035c923f1598147c36e4b0860b5ab233577de
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="foldingparameters-element-assl"></a>FoldingParameters-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Übergeordnetes Element|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Untergeordnete Elemente|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaften sind nur zur internen Verwendung, und werden nicht zur Verwendung in DDL-Anweisungen unterstützt.  
  
 Informationen zur Verwendung von kreuzvalidierung in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], finden Sie unter [Measures in der übergreifenden Überprüfungsbericht](../../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).  
  
 Informationen zum Ausführen der kreuzvalidierung mit [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gespeicherte Prozeduren finden Sie unter [Data Mining Stored Procedures &#40;Analysis Services – Data Mining&#41;](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
