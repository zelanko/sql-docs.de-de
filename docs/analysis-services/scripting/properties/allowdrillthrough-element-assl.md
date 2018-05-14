---
title: AllowDrillThrough-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 25bad363975494fc8bd6c8cb343a165d8bb85f85
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="allowdrillthrough-element-assl"></a>AllowDrillThrough-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|**False**|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningModel-Element](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [miningstructurepermission-Objekte](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen **AllowDrillThrough** im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, und <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Drillthrough in Miningstrukturen  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], können Sie definieren **AllowDrillthrough** Berechtigungen für Miningstrukturen sowie Miningmodelle. Wenn Sie diese Berechtigung einer Rolle zuordnen, kann jedes Mitglied dieser Rolle das Data Mining-Modell abfragen und Strukturspalten zurückgeben, die nicht im Modell enthalten waren. Zum Beispiel erstellen Sie nur mit folgenden Spalten ein Modell: Kundenschlüssel, Kundeneinkommen und Kundenkäufe. Wenn Sie Drillthrough im Modell aktivieren, können Benutzer Informationen in anderen Spalten der Miningstruktur, z.&nbsp;B. E-Mail-Adressen oder Namen von Kunden, zurückgeben.  
  
 Um sensible Daten zu schützen, gehen Sie daher beim Hinzufügen von Spalten zur Miningstruktur sorgfältig vor. Erteilen Sie außerdem die **AllowDrillthrough** -Berechtigung für eine Struktur nur, wenn es erforderlich ist.  
  
 Um einen Drillthrough zu Strukturspalten auszuführen, verwenden Sie eine Abfrage in einem der folgenden Formate:  
  
 `SELECT * FROM <structure>.CASES`  
  
 oder  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
