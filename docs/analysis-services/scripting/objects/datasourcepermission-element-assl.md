---
title: DataSourcePermission-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c6dabefaa319bb847975da03b5593e5dc79e4268
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="datasourcepermission-element-assl"></a>DataSourcePermission-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert die Standardberechtigungen in einem [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) für einen bestimmten Datentyp [Rolle](../../../analysis-services/scripting/objects/role-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataSourcePermissions>  
   <DataSourcePermission xsi:type="Permission">  
      <!-- No child elements other than those from Permission are defined -->  
...</DataSourcePermission>  
</DataSourcePermissions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|[Berechtigung](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das einmal oder mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DataSourcePermissions](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 **DataSourcePermission** -Objekte können nur für Rollen vorhanden sein, die im Besitz der Datenbank sind, und nur ein **DataSourcePermission** -Objekt kann für eine Rolle vorhanden sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
