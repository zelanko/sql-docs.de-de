---
title: TimeAttributeBinding-Datentyp (ASSL) | Microsoft-Dokumentation
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
- TimeAttributeBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TimeAttributeBinding
helpviewer_keywords:
- TimeAttributeBinding data type
ms.assetid: e8317b1c-a83a-4074-9538-400792500985
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7e123cad0d54a1512aaa7edac8a230348505b879
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237550"
---
# <a name="timeattributebinding-data-type-assl"></a>TimeAttributeBinding-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der für generierte Elemente (z. B. die Schlüsselspalten eines Attributs) in einer Serverzeitdimension eine "Platzhalter"-Bindung darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<TimeAttributeBinding>  
   <!-- TimeAttributeBinding has no child elements other than those inherited from Binding -->  
</TimeAttributeBinding>  
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
|Untergeordnete Elemente|InclusionThresholdSetting|  
|Abgeleitete Elemente|Finden Sie unter [binden](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu den `Binding` -Typ und zu Tabellen von Analysis Services Scripting Language (ASSL)-Objekten, von der `Binding` Typ und der Vererbungshierarchie des `Binding` Datentypen, finden Sie unter [Binding-Datentyp &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.TimeAttributeBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
