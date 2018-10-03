---
title: ValueColumn-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ValueColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ValueColumn element
ms.assetid: 6c2d6822-8ecc-46df-9fa9-bb92ac716c36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 876d5efb4d4b84e8f42cfd3c360258c8cb67d865
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048141"
---
# <a name="valuecolumn-element-assl"></a>ValueColumn-Element (ASSL)
  Identifiziert die Spalte, die den Wert des übergeordneten Elements bereitstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <ValueColumn xsi:type="DataItem">...</ValueColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[DataItem-Objekt](../data-type/dataitem-data-type-assl.md)|  
|Standardwert|Variiert (siehe Hinweise)|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionAttribute-Objekt](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die [NameColumn](namecolumn-element-assl.md) Element `DimensionAttribute` angegeben wird, gleich `DataItem` Werte werden verwendet, als Standardwerte für die `ValueColumn` Element. Wenn die `NameColumn` Element `DimensionAttribute` nicht angegeben ist und die [KeyColumns](../collections/keycolumns-element-assl.md) Auflistung von `DimensionAttribute` enthält ein einzelnes [KeyColumn](keycolumn-element-assl.md) Element, das eine Schlüsselspalte mit einer Zeichenfolge darstellt -Datentyp, der `DataItem` Werte werden verwendet, als Standardwerte für die `ValueColumn` Element.  
  
 Weitere Informationen zu den `DataItem` Typ, einschließlich einer Tabelle von Analysis Services Scripting Language (ASSL)-Objekten und Eigenschaften der `DataItem` finden Sie unter [DataItem-Datentyp &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `NameColumn` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.DimensionAttribute> und <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
