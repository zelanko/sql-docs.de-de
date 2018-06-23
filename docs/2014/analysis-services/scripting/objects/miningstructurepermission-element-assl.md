---
title: Miningstructurepermissions-Element (ASSL) | Microsoft Docs
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
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0c74423bfbf199825dc707d80e21c5b5a4555cc8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060815"
---
# <a name="miningstructurepermission-element-assl"></a>MiningStructurePermissions-Element (ASSL)
  Definiert den Berechtigungen, die Elemente einer [Rolle](role-element-assl.md) Element besitzen, für ein einzelnes [MiningStructure](miningstructure-element-assl.md) Element.  
  
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
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
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
  
  