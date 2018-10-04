---
title: PerspectiveCalculation-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- PerspectiveCalculation Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveCalculation
helpviewer_keywords:
- PerspectiveCalculation data type
ms.assetid: 5a5173d2-c96d-4a55-a35c-0cbfd5b0e599
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1b4f56077a784a26617946dd1179738f838b2db3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126086"
---
# <a name="perspectivecalculation-data-type-assl"></a>PerspectiveCalculation-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der die Beziehung zwischen einer Berechnung darstellt und einen [Perspektive](../objects/perspective-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<PerspectiveCalculation>  
      <Name>...</Name>  
   <Type>...</Type>  
   <Annotations>...</Annotations>  
</PerspectiveCalculation>  
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
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [Namen](../properties/name-element-assl.md), [Typ](../properties/type-element-perspectivecalculation-assl.md)|  
|Abgeleitete Elemente|[Berechnung](../objects/calculation-element-assl.md) ([Berechnungen](../collections/calculations-element-assl.md) Auflistung von [Perspektive](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.PerspectiveCalculation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
