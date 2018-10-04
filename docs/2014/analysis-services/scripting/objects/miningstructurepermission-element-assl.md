---
title: Miningstructurepermissions-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningStructurePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructurePermission
helpviewer_keywords:
- MiningStructurePermission element
ms.assetid: 4ba2bfd2-9003-4eed-8049-a74d452894ea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 89521b4201e3956ab6d44d95d7234321a0948f56
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197620"
---
# <a name="miningstructurepermission-element-assl"></a>MiningStructurePermissions-Element (ASSL)
  Definiert den Berechtigungen, die Elemente einer [Rolle](role-element-assl.md) Element verfügen, für ein einzelnes [MiningStructure](miningstructure-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructurePermissions>  
   <MiningStructurePermission xsi:type="Permission">  
      <AllowDrillthrough>...</AllowDrillthrough>  
  
      <!-- This element also inherits all the child elements listed in Permission -->  
   </MiningStructurePermission>  
</MiningStructurePermissions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[Berechtigung](../data-type/permission-data-type-assl.md)|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] wurde die `AllowDrillthrough`-Berechtigung auf eine Miningstruktur erweitert. Wenn Sie diese Berechtigung einer Rolle zuordnen, kann jeder Benutzer, der ein Mitglied dieser Rolle ist, die Miningstruktur mit der folgenden Syntax direkt abfragen:  
  
```  
SELECT <structure column list> FROM <structure>.CASES  
```  
  
 Wenn darüber hinaus `AllowDrillthrough` sowohl für die Miningstruktur als auch für das Miningmodell aktiviert ist, können Benutzer mit folgender Syntax Strukturspalten abfragen, die nicht im Miningmodell enthalten waren:  
  
```  
SELECT StructureColumn('<structure column name>' FROM <model>.CASES  
```  
  
 Zum Beispiel erstellen Sie nur mit Spalten für Kundenschlüssel, Kundeneinkommen und Kundenkäufe ein Modell. Mit Drillthrough kann ein Benutzer andere Strukturspalten zurückgeben, die nicht im Miningmodell enthalten waren, z. B. Kundenkontaktinformationen.  
  
 Daher sollten Sie zum Schutz sensibler oder persönlicher Informationen die Datenquellensicht so einrichten, dass persönliche Informationen verborgen sind. Lasse Sie die `AllowDrillthrough`-Berechtigung für eine Miningstruktur nur bei Bedarf zu.  
  
 Weitere Informationen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../data-mining/drillthrough-queries-data-mining.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices.MiningModel.AllowDrillThrough%2A>   
 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModel.AllowDrillThrough%2A>   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
