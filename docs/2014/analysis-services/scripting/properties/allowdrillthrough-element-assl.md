---
title: AllowDrillThrough-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AllowDrillThrough Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllowDrillThrough
helpviewer_keywords:
- AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 79abc9833c111c472776d0713a0ca50888cae27d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090850"
---
# <a name="allowdrillthrough-element-assl"></a>AllowDrillThrough-Element (ASSL)
  Bestimmt, ob Drillthrough auf dem übergeordneten Element erlaubt wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|`False`|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningModel-Element](../objects/miningmodel-element-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen `AllowDrillThrough` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, und <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Drillthrough in Miningstrukturen  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], können Sie definieren `AllowDrillthrough` Berechtigungen für Miningstrukturen sowie Miningmodelle. Wenn Sie diese Berechtigung einer Rolle zuordnen, kann jedes Mitglied dieser Rolle das Data Mining-Modell abfragen und Strukturspalten zurückgeben, die nicht im Modell enthalten waren. Zum Beispiel erstellen Sie nur mit folgenden Spalten ein Modell: Kundenschlüssel, Kundeneinkommen und Kundenkäufe. Wenn Sie Drillthrough im Modell aktivieren, können Benutzer Informationen in anderen Spalten der Miningstruktur, z.&nbsp;B. E-Mail-Adressen oder Namen von Kunden, zurückgeben.  
  
 Um sensible Daten zu schützen, gehen Sie daher beim Hinzufügen von Spalten zur Miningstruktur sorgfältig vor. Erteilen Sie außerdem `AllowDrillthrough` -Berechtigung für eine Struktur nur, wenn dies erforderlich ist.  
  
 Um einen Drillthrough zu Strukturspalten auszuführen, verwenden Sie eine Abfrage in einem der folgenden Formate:  
  
 `SELECT * FROM <structure>.CASES`  
  
 oder  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
