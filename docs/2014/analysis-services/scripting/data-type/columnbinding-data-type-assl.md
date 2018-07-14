---
title: ColumnBinding-Datentyp (ASSL) | Microsoft-Dokumentation
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
- ColumnBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnBinding
helpviewer_keywords:
- ColumnBinding data type
ms.assetid: 3ab1bac1-6716-4b17-a107-d5f9c744c5e6
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 227801af8b66d66ebeba50d2713267720adffa9a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200110"
---
# <a name="columnbinding-data-type-assl"></a>ColumnBinding-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der die Bindung einer Spalte in einer Datenquellensicht zu darstellt, der eine [DataItem](dataitem-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ColumnBinding>  
   <!-- The following elements extend Binding -->  
   <TableID>...</TableID>  
      <ColumnID>...</ColumnID>  
</ColumnBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Bindung](binding-data-type-assl.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[ColumnID](../properties/columnid-element-eventcolumn-assl.md), [TableID](../properties/id-element-assl.md)|  
|Abgeleitete Elemente|Finden Sie unter [binden](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Um gültige Namen für XML-Elemente zu erstellen, codieren [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] `DataSet`-Objekte Tabellennamen, während sie in XML-Schemadefinition (XSD) serialisieren; aus dem Namen "Order Details" wird z. B. "Order_x0020_Details". Ebenso müssen das `ColumnID`- und das `TableID`-Element, die im `ColumnBinding`-Element enthalten sind und auf Objekte in der Datenquellensicht (Data Source View, DSV) verweisen, auch während der Serialisierung Namen codieren, um sicherzustellen, dass die Namen direkt mit dem Text in der DSV übereinstimmen. Die Analysis Services-Instanz decodiert diese Namen, ebenso wie das `DataSet`-Objektmodell.  
  
 Ein `TableDefinitions`-Element, das in einem Element enthalten ist, das den `TableBinding`-Datentyp verwendet und das auf Tabellen in der DSV verweist, muss auch bei der Serialisierung in XSD Namen codieren. Die Tabellennamen in den `Partition`-Bindungen sollten jedoch nicht codiert sein, da es sich bei diesen Namen nur um Namen von Tabellen handelt, die in der Datenbank und nicht notwendigerweise in der DSV vorkommen. Werden die Tabellennamen in den `Partition`-Bindungen nicht codiert, kann darüber hinaus Folgendes erreicht werden:  
  
-   Die Datendefinitionsbibliothek (Data Definition Library, DDL) für Partitionen bleibt einfacher.  
  
-   Es kann mehr Konsistenz erzielt werden, da Partitionen entweder einen Tabellennamen oder eine SELECT-Anweisung aufweisen und die SELECT-Anweisung nicht codiert werden sollte.  
  
 Tabellen- und Spaltennamen schließen keine Trennzeichen (z. B. "[" für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) ein.  
  
 Weitere Informationen zu den `Binding` -Typ und zu Tabellen von Analysis Services Scripting Language (ASSL)-Objekten, von der `Binding` Typ und der Vererbungshierarchie des `Binding` Datentypen, finden Sie unter [Binding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Das entsprechende Element im AMO-Objektmodell ist <xref:Microsoft.AnalysisServices.ColumnBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
