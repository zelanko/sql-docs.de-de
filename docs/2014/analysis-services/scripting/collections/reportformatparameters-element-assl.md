---
title: ReportFormatParameters-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportFormatParameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportFormatParameters
helpviewer_keywords:
- ReportFormatParameters element
ms.assetid: f2e677bf-7b6b-4ce4-b0ec-75a4999306c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 298357fffbbf2fed441a86d7d0e1ad211eef1c3c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171610"
---
# <a name="reportformatparameters-element-assl"></a>ReportFormatParameters-Element (ASSL)
  Enthält die Auflistung der [ReportFormatParameter](../objects/reportformatparameter-element-asl.md) -Elemente für ein [ReportAction](../data-type/action-data-type-assl.md) -Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action xsi:type="ReportAction">  
   ...  
   <ReportFormatParameters>  
      <ReportFormatParameter>...</ReportFormatParameter>  
   </ReportFormatParameters>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Action](../objects/action-element-assl.md) des Typs [ReportAction](../data-type/action-data-type-assl.md)|  
|Untergeordnete Elemente|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `ReportFormatParameters` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
