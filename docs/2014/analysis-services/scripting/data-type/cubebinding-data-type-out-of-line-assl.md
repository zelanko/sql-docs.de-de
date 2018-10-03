---
title: CubeBinding-Datentyp (Out-of-Line) (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeBinding
helpviewer_keywords:
- CubeBinding data type
ms.assetid: 5e1ee8ef-855c-4f3d-ae21-a33360d00d66
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ee354905f21670a143d8ec711bb45495086dbf05
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136651"
---
# <a name="cubebinding-data-type-out-of-line-assl"></a>CubeBinding-Datentyp (Out-of-Line) (ASSL)
  Definiert einen Grunddatentyp, der die Beziehung zwischen einer [Cube](../objects/cube-element-assl.md) Element und ein [DataSource](../objects/datasource-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeBinding>  
   <ID>...</ID>  
   <DataSourceID>...</DataSourceID>  
   <DataSource>...</DataSource>  
   <MeasureGroup>...</MeasureGroup>  
</CubeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[DataSource](../objects/datasource-element-assl.md), [DataSourceID](../properties/id-element-assl.md), [ID](../properties/id-element-assl.md), [MeasureGroup-Objekt](../objects/group-element-assl.md)|  
|Abgeleitete Elemente|[Binden von](../../xmla/xml-elements-properties/binding-element-xmla.md) ([Bindungen](../../xmla/xml-elements-properties/bindings-element-xmla.md) Auflistung von [Prozess](../../xmla/xml-elements-commands/process-element-xmla.md) oder [Batch](../../xmla/xml-elements-commands/batch-element-xmla.md) Befehle)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Out-of-Line-Bindungen finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
