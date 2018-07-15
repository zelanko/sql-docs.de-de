---
title: DataItem-Datentyp (ASSL) | Microsoft-Dokumentation
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2646dcce64672d98d33ecff3575016269379325
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300890"
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
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [Sortierreihenfolge](../properties/collation-element-assl.md), [DataSize](../properties/datasize-element-assl.md), [DataType](../properties/datatype-element-assl.md), [Format](../properties/format-element-assl.md), [InvalidXmlCharacters ](../properties/invalidxmlcharacters-element-assl.md), [MimeType](../properties/mimetype-element-assl.md), [NullProcessing](../properties/nullprocessing-element-assl.md), [Quelle](../properties/source-element-binding-assl.md), [kürzen](../properties/trimming-element-assl.md)|  
|Abgeleitete Elemente|Siehe die Tabelle in den Anmerkungen.|  
  
## <a name="remarks"></a>Hinweise  
 Die `DataItem` -Datentyp wird für jedes Datenelement, das gebunden werden kann, z. B. eine Measure, Attributschlüssel und Attributnamen verwendet. Die relevanten Details und die angewendeten Standardwerte hängen von der Verwendung ab; Attributnamen müssen beispielsweise Zeichenfolgen sein.  
  
 Eine Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] akzeptiert nur einen bestimmten Satz von Datentypen. Die Verwendung von anderen Datentypen führt zu einem Fehler und nicht zu einer impliziten Konvertierung in einen der gültigen Datentypen.  
  
 Die folgende Tabelle enthält Elemente des Typs `DataItem`.  
  
|Übergeordnetes Element|Element des Typs `DataItem`|Kommentare|  
|--------------------|----------------------------------|--------------|  
|[AttributeTranslation](../objects/column-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute-Objekt](../objects/customrollupcolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute-Objekt](../objects/customrolluppropertiescolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute-Objekt](../objects/keycolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md), [AttributeBinding](attributebinding-data-type-assl.md) oder [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute-Objekt](../objects/namecolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute-Objekt](../objects/skippedlevelscolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute-Objekt](../objects/unaryoperatorcolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md) oder [AttributeBinding](attributebinding-data-type-assl.md)|  
|[Measure](../objects/measure-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|`Source` Element der `DataItem` muss vom Typ [RowBinding](rowbinding-data-type-assl.md), [ColumnBinding](binding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), oder [CubeDimensionBinding](dimensionbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[KeyColumn-Wert](../objects/keycolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md), [AttributeBinding](attributebinding-data-type-assl.md) oder ["inheritedbinding"](inheritedbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[KeyColumn-Wert](../objects/keycolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[NameColumn-Wert](../objects/namecolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/foreignkeycolumn-element-assl.md)|`Source` Element der `DataItem` muss vom Typ [ColumnBinding](binding-data-type-assl.md)|  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
