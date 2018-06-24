---
title: DatabasePermissions-Element (ASSL) | Microsoft Docs
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
- DatabasePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DatabasePermissions
helpviewer_keywords:
- DatabasePermissions element
ms.assetid: c4ce0da3-f7ba-4f11-8cd8-236c32992aaf
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4a9c77244d652aa80b74f9dc007d2b44bba9174e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046989"
---
# <a name="databasepermissions-element-assl"></a>DatabasePermissions-Element (ASSL)
  Enthält die Auflistung der [DatabasePermission](../objects/databasepermission-element-assl.md) Elemente, die zu einem [Datenbank](../objects/database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Database>  
   ...  
   <DatabasePermissions>  
      <DatabasePermission>...</DatabasePermission>  
      </DatabasePermissions>  
      ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Datenbank](../objects/database-element-assl.md)|  
|Untergeordnete Elemente|[DatabasePermission](../objects/databasepermission-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.DatabasePermissionCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Permission-Datentyp &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  