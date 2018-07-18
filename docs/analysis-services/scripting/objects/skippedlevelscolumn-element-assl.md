---
title: SkippedLevelsColumn-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 70720ff4cb1acc99cfe0e364c8c2998af3b3ba10
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035421"
---
# <a name="skippedlevelscolumn-element-assl"></a>SkippedLevelsColumn-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
    
> [!NOTE]  
>  Diese Funktion wird in dieser Version von Microsoft SQL Server nicht mehr unterstützt. Verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen nicht, und planen Sie das Ändern von Anwendungen, in denen es zurzeit verwendet wird.  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die **SkippedLevelsColumn** Element gilt nur für übergeordnete Attribute (also der Wert der die [Verwendung](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) -Element für die **DimensionAttribute** übergeordneten festgelegt ist um *übergeordneten*). Das **SkippedLevelsColumn** -Element enthält die Spalte oder das Attribut für das übergeordnete Attribut, das die Anzahl übersprungener Ebenen zwischen jedem Element und dem übergeordneten Element speichert. Dies lässt Über-/Unterordnungshierarchien zu, die darauf basieren, dass übergeordnete Attribute Ebenen zwischen Elementen überspringen. Die in dieser Spalte oder diesem Attribut enthaltenen Werte müssen nicht negative ganze Zahlen sein. Andernfalls tritt ein Verarbeitungsfehler auf. Ist das **SkippedLevelsColumn** -Element nicht festgelegt oder enthält es keinen Wert, verfügt das aktuelle Element über eine Ebenentiefe, die eine Ebene geringer ist als die des übergeordneten Elements.  
  
 Weitere Informationen zu den **DataItem** Typ, einschließlich einer Tabelle von Analysis Services Scripting Language (ASSL)-Objekten und Eigenschaften von der **DataItem** table, finden Sie unter [DataItem-Datentyp &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Das Element, das das übergeordnete Element des entspricht **SkippedLevelsColumn** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute-Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/attributes-element-assl.md)   
 [Dimension-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
