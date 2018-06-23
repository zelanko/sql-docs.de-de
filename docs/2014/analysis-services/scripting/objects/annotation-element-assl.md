---
title: Annotation-Element (ASSL) | Microsoft Docs
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
- Annotation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Annotation
helpviewer_keywords:
- Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5dfe8ea881948de8ed53cea0ddcff1e1325a96d3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060396"
---
# <a name="annotation-element-assl"></a>Annotation-Element (ASSL)
  Enthält Elemente, die verwendet werden, um das ASSL-Schema (Analysis Services Scripting Language) zu erweitern.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Annotations>  
   <Annotation>  
      <Name>...</Name>  
      <Visibility>...</Visibility>  
      <Value>...</Value>  
   </Annotation>  
</Annotations >  
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
|Übergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md)|  
|Untergeordnete Elemente|[Name](../properties/name-element-assl.md), [Value](../properties/value-element-assl.md), [Visibility](../properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Annotation` -Element bietet Erweiterbarkeit des ASSL-Schema für alle Objekte, ausgenommen derer, die einzig zur Definition eines komplexen Datentyps verwendet. Das `Value`-Element des `Annotation`-Elements kann gemäß den folgenden Regeln gültiges XML aus allen XML-Namespaces enthalten, ausgenommen ASSL:  
  
-   XML kann nur Elemente enthalten.  
  
-   Jedes Element muss einen eindeutigen Namen haben. Es wird empfohlen, den Wert des der `Name` Element von der `Annotation` Element auf den Zielnamespace verweist.  
  
 Diese Regeln werden auferlegt, damit die Inhalte des `Annotation`-Elements als Menge von Name/Wert-Paaren über andere Schnittstellen, wie Decision Support Objects (DSO), verfügbar gemacht werden können.  
  
 Kommentare und Leerzeichen innerhalb des `Annotation`-Elements, die nicht in einem untergeordneten Element eingeschlossen sind, können nicht beibehalten werden. Außerdem müssen alle Elemente über Lese-/Schreibzugriff verfügen. Schreibgeschützte Elemente werden ignoriert.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  