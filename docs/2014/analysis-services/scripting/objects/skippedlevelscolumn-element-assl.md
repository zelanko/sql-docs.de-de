---
title: SkippedLevelsColumn-Element (ASSL) | Microsoft-Dokumentation
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c04dea8c63d71483de9a8194a15bc4e4d7be5b88
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196030"
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
|Datentyp und -länge|[DataItem-Objekt](../data-type/dataitem-data-type-assl.md)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionAttribute-Objekt](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der `SkippedLevelsColumn` Element ist nur auf übergeordnete Attribute anwendbar (in anderen Worten: der Wert, der die [Nutzung](../properties/usage-element-dimensionattribute-assl.md) -Element für die `DimensionAttribute` übergeordnetes Element festgelegt wird, um *übergeordneten*). Das `SkippedLevelsColumn`-Element enthält die Spalte oder das Attribut für das übergeordnete Attribut, das die Anzahl übersprungener Ebenen zwischen jedem Element und dem übergeordneten Element speichert. Dies lässt Über-/Unterordnungshierarchien zu, die darauf basieren, dass übergeordnete Attribute Ebenen zwischen Elementen überspringen. Die in dieser Spalte oder diesem Attribut enthaltenen Werte müssen nicht negative ganze Zahlen sein. Andernfalls tritt ein Verarbeitungsfehler auf. Wenn die `SkippedLevelsColumn` Element nicht angegeben ist oder keinen Wert enthält, die das aktuelle Element verfügt über eine Ebene Ebenentiefe dem übergeordneten Element.  
  
 Weitere Informationen zu den `DataItem` Typ, einschließlich einer Tabelle von Analysis Services Scripting Language (ASSL)-Objekten und Eigenschaften der `DataItem` table, finden Sie unter [DataItem-Datentyp &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Das Element, das dem übergeordneten entspricht `SkippedLevelsColumn` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Attributes-Element &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Dimension-Element &#40;ASSL&#41;](dimension-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
