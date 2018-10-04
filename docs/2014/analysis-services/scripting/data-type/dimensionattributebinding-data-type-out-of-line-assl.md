---
title: DimensionAttributeBinding-Datentyp (Out-of-Line) (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d649dcfc5070d0c60a2ab3cea421e5c8b0c328b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197760"
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
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[AttributeID](../properties/id-element-assl.md), [DatabaseID](../../xmla/xml-elements-properties/id-element-xmla.md), [DimensionID](../properties/dimensionid-element-assl.md), [KeyColumns](../collections/columns-element-assl.md), [NameColumn](../objects/column-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md)|  
|Abgeleitete Elemente|[Binden von](../../xmla/xml-elements-properties/binding-element-xmla.md) ([Bindungen](../collections/attributes-element-assl.md) Auflistung von XML for Analysis (XMLA) [Batch](../../xmla/xml-elements-commands/batch-element-xmla.md) und [Prozess](../../xmla/xml-elements-commands/process-element-xmla.md) Befehle)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Out-of-Line-Bindungen finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
