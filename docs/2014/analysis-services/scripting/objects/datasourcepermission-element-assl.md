---
title: DataSourcePermission-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSourcePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSourcePermission element
ms.assetid: 6dc6fb13-034e-479a-902e-27f3fb78c33f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d4130cd2a0eb83b32c8bcdf703d10ca6305af619
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087620"
---
# <a name="datasourcepermission-element-assl"></a>DataSourcePermission-Element (ASSL)
  Definiert die Standardberechtigungen in einem [DataSource](../data-type/datasource-data-type-assl.md) -Datentyp für eine bestimmte [Rolle](role-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataSourcePermissions>  
   <DataSourcePermission xsi:type="Permission">  
      <!-- No child elements other than those from Permission are defined -->  
...</DataSourcePermission>  
</DataSourcePermissions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[Berechtigung](../data-type/permission-data-type-assl.md)|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das einmal oder mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DataSourcePermissions](../collections/datasourcepermissions-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 `DataSourcePermission`-Objekte können nur für Rollen vorhanden sein, die im Besitz der Datenbank sind, und nur ein `DataSourcePermission`-Objekt kann für eine Rolle vorhanden sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element &#40;ASSL&#41;](role-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
