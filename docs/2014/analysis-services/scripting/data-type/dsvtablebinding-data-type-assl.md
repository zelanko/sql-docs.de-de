---
title: DSVTableBinding-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DSVTableBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DSVTableBinding
helpviewer_keywords:
- DSVTableBinding data type
ms.assetid: 149e753f-6218-4805-9223-7155b6827e64
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7b2ceab8524135338aa066837c50170268711a9d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095730"
---
# <a name="dsvtablebinding-data-type-assl"></a>DSVTableBinding-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der die Bindung zwischen einer Tabelle darstellt und einen [DataSourceView](../objects/datasourceview-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DSVTableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceViewID>...</DataSourceViewID>  
   <TableID>...</TableID>  
</DSVTableBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[TabularBinding](binding-data-type-assl.md)|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[DataSourceViewID](../properties/id-element-assl.md), [TableID](../properties/tableid-element-assl.md)|  
|Abgeleitete Elemente|Finden Sie unter [binden](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu der `Binding` -Typ und zu Tabellen von Analysis Services Scripting Language (ASSL)-Objekten, von der `Binding` Typ und der Vererbungshierarchie des `Binding` Datentypen, finden Sie unter [Bindung](binding-data-type-assl.md) Element.  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.DSVTableBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
