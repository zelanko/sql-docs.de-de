---
title: DatabasePermission-Element (ASSL) | Microsoft Docs
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
- DatabasePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DatabasePermission
helpviewer_keywords:
- DatabasePermission element
ms.assetid: 6dcb9136-a40d-42e3-ad3b-b8ce8c7ca78c
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e47203616cc76fa09c0fd0658e7dad8a89c90a9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061687"
---
# <a name="databasepermission-element-assl"></a>DatabasePermission-Element (ASSL)
  Definiert die Standardberechtigungen in einem [Datenbank](database-element-assl.md) -Element für ein bestimmtes [Rolle](role-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DatabasePermissions>  
      <DatabasePermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <Administer>...</Administer>  
...</DatabasePermission>  
</DatabasePermissions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[Berechtigung](../data-type/permission-data-type-assl.md)|  
|Standardwert|False|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DatabasePermissions](../collections/databasepermissions-element-assl.md)|  
|Untergeordnete Elemente|[Verwalten](../properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 `DatabasePermission`-Objekte können nur für Rollen vorhanden sein, die im Besitz der Datenbank sind, und nur ein `DatabasePermission`-Objekt kann für eine Rolle vorhanden sein.  
  
 Dieses Element verfügt über die folgenden Überprüfungen unter dem DeploymentMode-Wert 2 (tabellarisches Modell).  
  
-   *Verwalten von* Standardwert des Attributs wird festgelegt, um `False`, außer wenn der Benutzer über Administratorrechte verfügt. Für Benutzer mit Administratorrechten wird der Attributwert auf `True` festgelegt.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element &#40;ASSL&#41;](role-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  