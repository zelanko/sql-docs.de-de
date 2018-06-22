---
title: SkippedLevelsColumn-Element (ASSL) | Microsoft Docs
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
- SkippedLevelsColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SkippedLevelsColumn
helpviewer_keywords:
- SkippedLevelsColumn element
ms.assetid: 6b00a288-99c1-4735-9e6b-cd13ed4fa346
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3ae469982f39e1274759eaaea992fe456330d8fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056793"
---
# <a name="skippedlevelscolumn-element-assl"></a>SkippedLevelsColumn-Element (ASSL)
    
> [!NOTE]  
>  Diese Funktion wird in dieser Version von Microsoft SQL Server nicht mehr unterstützt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.  
  
 Stellt die Details einer Spalte bereit, die die Anzahl der übersprungenen (leeren) Ebenen zwischen den einzelnen Elementen und den jeweils übergeordneten Elementen speichert.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <SkippedLevelsColumn xsi:type="DataItem">...</SkippedLevelsColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `SkippedLevelsColumn` Element gilt nur für übergeordnete Attribute (also der Wert der die [Verwendung](../properties/usage-element-dimensionattribute-assl.md) -Element für die `DimensionAttribute` auf Parent festgelegt ist *übergeordneten*). Das `SkippedLevelsColumn`-Element enthält die Spalte oder das Attribut für das übergeordnete Attribut, das die Anzahl übersprungener Ebenen zwischen jedem Element und dem übergeordneten Element speichert. Dies lässt Über-/Unterordnungshierarchien zu, die darauf basieren, dass übergeordnete Attribute Ebenen zwischen Elementen überspringen. Die in dieser Spalte oder diesem Attribut enthaltenen Werte müssen nicht negative ganze Zahlen sein. Andernfalls tritt ein Verarbeitungsfehler auf. Wenn die `SkippedLevelsColumn` Element nicht angegeben oder keinen Wert enthält, die das aktuelle Element verfügt über eine Ebene Tiefe unterhalb des übergeordneten Elements.  
  
 Weitere Informationen zu den `DataItem` Typ, einschließlich einer Tabelle von Analysis Services Scripting Language (ASSL)-Objekten und Eigenschaften von der `DataItem` table, finden Sie unter [DataItem-Datentyp &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Das Element, das das übergeordnete Element des entspricht `SkippedLevelsColumn` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute-Element &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Dimension-Element &#40;ASSL&#41;](dimension-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  