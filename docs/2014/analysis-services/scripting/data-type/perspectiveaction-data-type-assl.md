---
title: PerspectiveAction-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- PerspectiveAction Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveAction
helpviewer_keywords:
- PerspectiveAction data type
ms.assetid: a0e4a545-688c-4d4e-b05f-0008d3503349
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 37152ab7db466c200dbe08ae8041037116f2802d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148732"
---
# <a name="perspectiveaction-data-type-assl"></a>PerspectiveAction-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der die Informationen über eine Aktion in einem [Perspektive](../objects/perspective-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID>  
   <Annotations>...</Annotations>  
</PerspectiveAction>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[ActionID](../properties/id-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md)|  
|Abgeleitete Elemente|[Aktion](../objects/action-element-assl.md) ([Aktionen](../collections/actions-element-assl.md) Auflistung von [Perspektive](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.PerspectiveAction>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
