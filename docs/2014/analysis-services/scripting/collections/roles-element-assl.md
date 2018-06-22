---
title: Roles-Element (ASSL) | Microsoft Docs
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
- Roles Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Roles
helpviewer_keywords:
- Roles element
ms.assetid: 4191b7ce-bae4-4200-8550-3904420efafd
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f8ced51e40e2804054a0c63368622d2df70f81fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150997"
---
# <a name="roles-element-assl"></a>Roles-Element (ASSL)
  Enthält die Auflistung der [Role](../objects/role-element-assl.md) -Elemente, die unter dem übergeordneten Element definiert sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Database> <!-- or Server -->  
   ...  
   <Roles>  
      <Role>...</Role>  
   </Roles>  
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
|Übergeordnete Elemente|[Database](../objects/database-element-assl.md), [Server](../objects/server-element-assl.md)|  
|Untergeordnete Elemente|[Rolle](../objects/role-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das `Roles`-Element, das einem `Server`-Element zugeordnet ist, enthält nur eine Rolle mit dem Namen Administrators, die die Serveradministratorrolle darstellt. Die Serveradministratorrolle kann nicht geändert oder gelöscht werden. Ein Hinzufügen zusätzlicher Rollen zur Auflistung ist ebenfalls nicht möglich.  
  
 Die `Roles` Element Verknüpfen mit einer `Database` Element enthält, die für diese Datenbank definierten Rollen.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.RoleCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  