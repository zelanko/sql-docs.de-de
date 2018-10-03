---
title: Annotation-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c8c8b70e9e15e01a0864cd9f3491aa188be6777
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103400"
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
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md)|  
|Untergeordnete Elemente|[Name](../properties/name-element-assl.md), [Value](../properties/value-element-assl.md), [Visibility](../properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Annotation` -Element bietet Erweiterbarkeit des ASSL-Schema für alle Objekte, ausgenommen derer, die einzig zur Definition eines komplexen Datentyps verwendet. Das `Value`-Element des `Annotation`-Elements kann gemäß den folgenden Regeln gültiges XML aus allen XML-Namespaces enthalten, ausgenommen ASSL:  
  
-   XML kann nur Elemente enthalten.  
  
-   Jedes Element muss einen eindeutigen Namen haben. Es wird empfohlen, den Wert des der `Name` Element der `Annotation` Element auf den Zielnamespace verweist.  
  
 Diese Regeln werden auferlegt, damit die Inhalte des `Annotation`-Elements als Menge von Name/Wert-Paaren über andere Schnittstellen, wie Decision Support Objects (DSO), verfügbar gemacht werden können.  
  
 Kommentare und Leerzeichen innerhalb des `Annotation`-Elements, die nicht in einem untergeordneten Element eingeschlossen sind, können nicht beibehalten werden. Außerdem müssen alle Elemente über Lese-/Schreibzugriff verfügen. Schreibgeschützte Elemente werden ignoriert.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
