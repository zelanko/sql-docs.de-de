---
title: Annotation-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 303ed41b27538d5e21541e2912e892d91fd0f3d0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34034477"
---
# <a name="annotation-element-assl"></a>Annotation-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Anmerkungen](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Untergeordnete Elemente|[Name](../../../analysis-services/scripting/properties/name-element-assl.md), [Value](../../../analysis-services/scripting/properties/value-element-assl.md), [Visibility](../../../analysis-services/scripting/properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das **Annotation** -Element bietet Erweiterbarkeit des ASSL-Schemas für alle Objekte, ausgenommen derer, die einzig zur Definition eines komplexen Datentyps verwendet werden. Das **Value** -Element des **Annotation** -Elements kann gemäß den folgenden Regeln gültiges XML aus allen XML-Namespaces enthalten, ausgenommen ASSL:  
  
-   XML kann nur Elemente enthalten.  
  
-   Jedes Element muss einen eindeutigen Namen haben. Es wird empfohlen, dass der Wert des **Name** -Elements des **Annotation** -Elements auf den Zielnamespace verweist.  
  
 Diese Regeln werden auferlegt, damit die Inhalte des **Annotation** -Elements als Menge von Name/Wert-Paaren über andere Schnittstellen, wie Decision Support Objects (DSO), verfügbar gemacht werden können.  
  
 Kommentare und Leerzeichen innerhalb des **Annotation** -Elements, die nicht in einem untergeordneten Element eingeschlossen sind, können nicht beibehalten werden. Außerdem müssen alle Elemente über Lese-/Schreibzugriff verfügen. Schreibgeschützte Elemente werden ignoriert.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
