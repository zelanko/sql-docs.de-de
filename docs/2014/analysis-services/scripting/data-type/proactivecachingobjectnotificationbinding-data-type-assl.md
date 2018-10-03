---
title: ProactiveCachingObjectNotificationBinding-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProactiveCachingObjectNotificationBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingObjectNotificationBinding data type
ms.assetid: b3cf5fb6-6121-4f25-8de6-f171792c440d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 201774fd7b46bf3d4fc30dfe304c8ffd80f7c6eb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080380"
---
# <a name="proactivecachingobjectnotificationbinding-data-type-assl"></a>ProactiveCachingObjectNotificationBinding-Datentyp (ASSL)
  Definiert einen abstrakten abgeleiteten Datentyp, die Informationen darstellt, das die [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element über datenquellenänderungen in angegebenen Tabellen und Sichten oder in Tabellen und Sichten, die über vorhandene datenbindungen, identifiziert die Neuerstellen des Caches erfordern.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProactiveCachingObjectNotificationBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingObjectNotificationBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|Abgeleitete Datentypen|[ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md), ["proactivecachinginheritedbinding"](proactivecachingtablesbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[NotificationTechnique](../properties/notificationtechnique-element-assl.md)|  
|Abgeleitete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu den `ProactiveCachingBinding` Typ, einschließlich einer Tabelle der Vererbungshierarchie der `ProactiveCachingBinding` Datentypen, finden Sie unter [ProactiveCachingBinding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Weitere Informationen zu den `Binding` -Typ und zu Tabellen von Analysis Services Scripting Language (ASSL)-Objekten, von der `Binding` Typ und der Vererbungshierarchie des `Binding` Datentypen, finden Sie unter [Binding-Datentyp &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.ProactiveCachingObjectNotificationBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
