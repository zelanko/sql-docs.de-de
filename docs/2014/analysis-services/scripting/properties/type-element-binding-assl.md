---
title: Geben Sie Element (Binding) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: b5f5c485-dc83-4d66-a8d2-e96e96d068f9
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b07c1d781bfdade9228b6c5991b2eb56585cbe85
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049981"
---
# <a name="type-element-binding-assl"></a>Type-Element (Bindung) (ASSL)
  Enthält den Typ der Attributbindung.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Type>...</Type>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AttributeBinding](../data-type/binding-data-type-assl.md), [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Allee*|Alle Ebenen|  
|*Key*|Elementschlüssel|  
|*Name*|Membername|  
|*ReplTest1*|Elementwert|  
|*Übersetzung*|Elementübersetzungen|  
|*UnaryOperator*|Unäre Operatoren|  
|*SkippedLevels*|Übersprungene Ebenen|  
|*CustomRollup*|Benutzerdefinierte Rollupformeln|  
|*CustomRollupProperties*|Benutzerdefinierte Rollupeigenschaften|  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `Type` im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.AttributeBinding> und <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Binding-Datentyp &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  