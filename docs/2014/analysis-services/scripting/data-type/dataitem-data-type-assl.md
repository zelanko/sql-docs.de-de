---
title: DataItem-Datentyp (ASSL) | Microsoft Docs
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
- DataItem Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataItem
helpviewer_keywords:
- DataItem data type
ms.assetid: f4f5155f-9c3d-49a1-a390-a9c734fafbce
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0d5622ca2cdda5a08bdcfdfd486e44b6fcd8fbf7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049304"
---
# <a name="dataitem-data-type-assl"></a>DataItem-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der die datenbezogenen Merkmale eines Datenelements darstellt, z. B. eine Spalte oder ein Attribut.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataItem>  
   <DataType>...</DataType>  
   <DataSize>...</DataSize>  
   <MimeType>...</MimeType>  
   <NullProcessing>...</NullProcessing>  
   <Trimming>...</Trimming>  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
      <Collation>...</Collation>  
   <Format>...</Format>  
   <Source>...</Source>  
   <Annotations>...</Annotations>  
</DataItem>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [Sortierung](../properties/collation-element-assl.md), [DataSize](../properties/datasize-element-assl.md), [DataType](../properties/datatype-element-assl.md), [Format](../properties/format-element-assl.md), [InvalidXmlCharacters ](../properties/invalidxmlcharacters-element-assl.md), [MimeType](../properties/mimetype-element-assl.md), [NullProcessing](../properties/nullprocessing-element-assl.md), [Quelle](../properties/source-element-binding-assl.md), [Zuschneiden](../properties/trimming-element-assl.md)|  
|Abgeleitete Elemente|Siehe die Tabelle in den Anmerkungen.|  
  
## <a name="remarks"></a>Hinweise  
 Die `DataItem` -Datentyp wird für jedes Datenelement, das gebunden werden kann; beispielsweise ein Measure, Attributschlüssel und Attributnamen verwendet. Die relevanten Details und die angewendeten Standardwerte hängen von der Verwendung ab; Attributnamen müssen beispielsweise Zeichenfolgen sein.  
  
 Eine Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] akzeptiert nur einen bestimmten Satz an Datentypen. Die Verwendung von anderen Datentypen führt zu einem Fehler und nicht zu einer impliziten Konvertierung in einen der gültigen Datentypen.  
  
 Die folgende Tabelle enthält Elemente des Typs `DataItem`.  
  
|Übergeordnetes Element|Element des Typs `DataItem`|Kommentare|  
|--------------------|----------------------------------|--------------|  
|[AttributeTranslation](../objects/column-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/customrollupcolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/customrolluppropertiescolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/keycolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md), [AttributeBinding](attributebinding-data-type-assl.md) oder [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/namecolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/skippedlevelscolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/unaryoperatorcolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[Measure](../objects/measure-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|`Source` Element von der `DataItem` muss vom Typ [RowBinding](rowbinding-data-type-assl.md), [ColumnBinding](binding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), oder [CubeDimensionBinding](dimensionbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[KeyColumn-Wert](../objects/keycolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md), [AttributeBinding](attributebinding-data-type-assl.md) oder [InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[KeyColumn-Wert](../objects/keycolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[NameColumn-Wert](../objects/namecolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/foreignkeycolumn-element-assl.md)|`Source` Element von der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md)|  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  