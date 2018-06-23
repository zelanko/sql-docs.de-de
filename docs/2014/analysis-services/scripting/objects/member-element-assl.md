---
title: Member-Element (ASSL) | Microsoft Docs
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
- Member Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Member
helpviewer_keywords:
- Member element
ms.assetid: 03b4cfcb-ce87-452f-9e25-8745c0423f56
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d2ababe44f923df08b08c3adeaf81bf84e3938f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147985"
---
# <a name="member-element-assl"></a>Member-Element (ASSL)
  Enthält den Namen eines Mitglieds eines [Group](group-element-assl.md) - oder [Role](role-element-assl.md) -Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Members>  
   <Member>  
      <Name>...</Name>  
   </Member>  
</Members>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Elemente](../collections/members-element-assl.md)|  
|Untergeordnete Elemente|[Name](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen `Member` im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.Group> und <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  