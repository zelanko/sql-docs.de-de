---
title: SkippedLevelsColumn-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9727a5080437352bebbfa9c7ced1cd3c88689113
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141730"
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
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionAttribute-Objekt](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der `SkippedLevelsColumn` Element ist nur auf übergeordnete Attribute anwendbar (in anderen Worten: der Wert, der die [Nutzung](../properties/usage-element-dimensionattribute-assl.md) -Element für die `DimensionAttribute` übergeordnetes Element festgelegt wird, um *übergeordneten*). Das `SkippedLevelsColumn`-Element enthält die Spalte oder das Attribut für das übergeordnete Attribut, das die Anzahl übersprungener Ebenen zwischen jedem Element und dem übergeordneten Element speichert. Dies lässt Über-/Unterordnungshierarchien zu, die darauf basieren, dass übergeordnete Attribute Ebenen zwischen Elementen überspringen. Die in dieser Spalte oder diesem Attribut enthaltenen Werte müssen nicht negative ganze Zahlen sein. Andernfalls tritt ein Verarbeitungsfehler auf. Wenn die `SkippedLevelsColumn` Element nicht angegeben ist oder keinen Wert enthält, die das aktuelle Element verfügt über eine Ebene Ebenentiefe dem übergeordneten Element.  
  
 Weitere Informationen zu den `DataItem` Typ, einschließlich einer Tabelle von Analysis Services Scripting Language (ASSL)-Objekten und Eigenschaften der `DataItem` table, finden Sie unter [DataItem-Datentyp &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Das Element, das dem übergeordneten entspricht `SkippedLevelsColumn` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Attributes-Element &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Dimension-Element &#40;ASSL&#41;](dimension-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
