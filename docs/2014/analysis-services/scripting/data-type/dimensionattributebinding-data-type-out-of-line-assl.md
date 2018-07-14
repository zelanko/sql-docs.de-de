---
title: DimensionAttributeBinding-Datentyp (Out-of-Line) (ASSL) | Microsoft-Dokumentation
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
- DimensionAttributeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DimensionAttributeBinding data type
ms.assetid: d8ec77a9-749f-4b08-8d56-8b6514a70248
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 34e2f45189a92397bd0afcbde2e504fa82d83604
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187087"
---
# <a name="dimensionattributebinding-data-type-out-of-line-assl"></a>DimensionAttributeBinding-Datentyp (Out-of-Line) (ASSL)
  Definiert einen abgeleiteten Datentyp, der die Out-of-Line-Bindung eines Attributs in einer Dimension darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <DimensionID>...</DimensionID>  
   <AttributeID>...</AttributeID>  
   <KeyColumns>...</KeyColumns>  
   <NameColumn>...</NameColumn>  
   <Translations>...</Translations>  
</DimensionAttributeBinding>  
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
|Untergeordnete Elemente|[AttributeID](../properties/id-element-assl.md), [DatabaseID](../../xmla/xml-elements-properties/id-element-xmla.md), [DimensionID](../properties/dimensionid-element-assl.md), [KeyColumns](../collections/columns-element-assl.md), [NameColumn](../objects/column-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md)|  
|Abgeleitete Elemente|[Binden von](../../xmla/xml-elements-properties/binding-element-xmla.md) ([Bindungen](../collections/attributes-element-assl.md) Auflistung von XML for Analysis (XMLA) [Batch](../../xmla/xml-elements-commands/batch-element-xmla.md) und [Prozess](../../xmla/xml-elements-commands/process-element-xmla.md) Befehle)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Out-of-Line-Bindungen finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
