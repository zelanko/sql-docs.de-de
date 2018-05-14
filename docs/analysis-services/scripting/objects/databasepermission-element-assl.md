---
title: DatabasePermission-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 855c632b78beb3a5ba75ff7acf31b72fff229e95
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="databasepermission-element-assl"></a>DatabasePermission-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert die Standardberechtigungen in einem [Datenbank](../../../analysis-services/scripting/objects/database-element-assl.md) -Element für ein bestimmtes [Rolle](../../../analysis-services/scripting/objects/role-element-assl.md) Element.  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|[Berechtigung](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Standardwert|False|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DatabasePermissions](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)|  
|Untergeordnete Elemente|[Verwalten](../../../analysis-services/scripting/properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 **DatabasePermission** -Objekte können nur für Rollen vorhanden sein, die im Besitz der Datenbank sind, und nur ein **DatabasePermission** -Objekt kann für eine Rolle vorhanden sein.  
  
 Dieses Element verfügt über die folgenden Überprüfungen unter dem DeploymentMode-Wert 2 (tabellarisches Modell).  
  
-   *Administer* -Attribut, dessen Standardwert auf **False**festgelegt wird, außer wenn der Benutzer Administratorrechte besitzt. Für Benutzer mit Administratorrechten wird der Attributwert auf **True**festgelegt.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
