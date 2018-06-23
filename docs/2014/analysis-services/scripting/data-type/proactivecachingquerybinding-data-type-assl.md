---
title: ProactiveCachingQueryBinding-Datentyp (ASSL) | Microsoft Docs
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
- ProactiveCachingQueryBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingQueryBinding data type
ms.assetid: c1b06e50-9e68-40db-bdab-fc2cb3a8ff64
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 339c35a33d3d26268b027068c6ac7f5254046606
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147991"
---
# <a name="proactivecachingquerybinding-data-type-assl"></a>ProactiveCachingQueryBinding-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, die Informationen darstellt, die die [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element über datenquellenänderungen in Tabellen und Sichten, die über die Ausführung von angegebenen Abfragen, das Neuerstellen des Caches erfordern, identifiziert.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProactiveCachingQueryBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <RefreshInterval>...</RefreshInterval>  
   <QueryNotification>...</QueryNotification>  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[QueryNotification](../objects/querynotification-element-assl.md), ["RefreshInterval"](../properties/refreshinterval-element-assl.md)|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu den `ProactiveCachingBinding` Typ, einschließlich einer Tabelle der Vererbungshierarchie der `ProactiveCachingBinding` , finden Sie unter [ProactiveCachingBinding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Weitere Informationen zu der `Binding` Typ, einschließlich Tabellen, die von Analysis Services Scripting Language (ASSL)-Objekten, von der `Binding` Typ und der Vererbungshierarchie der `Binding` , finden Sie unter [Binding-Datentyp &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  