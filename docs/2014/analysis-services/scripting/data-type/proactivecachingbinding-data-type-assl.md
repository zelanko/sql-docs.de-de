---
title: ProactiveCachingBinding-Datentyp (ASSL) | Microsoft-Dokumentation
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
- ProactiveCachingBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingBinding data type
ms.assetid: 02e6ff2f-2f18-4607-9198-bb46f113f9ac
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d440911eefa33981ef435240c4e440378da34a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189097"
---
# <a name="proactivecachingbinding-data-type-assl"></a>ProactiveCachingBinding-Datentyp (ASSL)
  Definiert einen abstrakten abgeleiteten Datentyp, die Informationen darstellt, das die [ProactiveCaching](../objects/proactivecaching-element-assl.md) Element über datenquellenänderungen, die Neuerstellung des Caches erfordern, sowie über den Status des Neuerstellungsprozesses.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProactiveCachingBinding>  
   <!-- ProactiveCachingBinding is an abstract base class with no child elements -->  
</ProactiveCachingBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Bindung](binding-data-type-assl.md)|  
|Abgeleitete Datentypen|[ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md), ["proactivecachingobjectnotificationbinding"](proactivecachingobjectnotificationbinding-data-type-assl.md), [ProactiveCachingQueryBinding](querybinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu den `Binding` -Typ und zu Tabellen von Analysis Services Scripting Language (ASSL)-Objekten, von der `Binding` Typ und der Vererbungshierarchie des `Binding` Datentypen, finden Sie unter [Binding-Datentyp &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>.  
  
## <a name="inheritance-hierarchy-of-proactivecachingbinding-types"></a>Vererbungshierarchie für ProactiveCachingBinding-Typen  
 Die folgende Hierarchie veranschaulicht die Vererbung von `ProactiveCachingBinding` Typen.  
  
 [Binden von](binding-data-type-assl.md) Element  
  
 `ProactiveCachingBinding`-Element  
  
 [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md) Element  
  
 [ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md) Element  
  
 [ProactiveCachingTablesBinding](proactivecachingtablesbinding-data-type-assl.md) Element  
  
 [ProactiveCachingQueryBinding](querybinding-data-type-assl.md) Element  
  
 [ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md) Element  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
