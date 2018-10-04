---
title: Administer-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Administer Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Administer
helpviewer_keywords:
- Administer element
ms.assetid: 52924cd6-6176-47c8-ab17-4ee0e0ce42b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 682c65420383bcd3db70d1c477781c7db1193334
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149300"
---
# <a name="administer-element-assl"></a>Administer-Element (ASSL)
  Gibt an, ob die zugeordnete Berechtigung das Recht zur Verwaltung umfasst eine [Datenbank](../objects/database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DatabasePermission>  
      ...  
      <Administer>...</Administer>  
   ...  
</DatabasePermission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DatabasePermission](../objects/databasepermission-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `Administer` Element gibt an, ob ein Benutzer Verwaltungsfunktionen nur auf der angegebenen Datenbank ausführen kann. Die Serveradministratorrolle kann Verwaltungsfunktionen auf allen von der Instanz enthaltenen Datenbanken ausführen.  
  
 Das Element, das dem übergeordneten entspricht `Administer` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Permission-Datentyp &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Role-Element &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
