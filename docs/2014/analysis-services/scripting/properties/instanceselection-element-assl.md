---
title: InstanceSelection-Element (ASSL) | Microsoft-Dokumentation
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
- InstanceSelection Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e9babb9e5066d00b8a396d52dfb2dbdfc2f0b4cf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279766"
---
# <a name="instanceselection-element-assl"></a>InstanceSelection-Element (ASSL)
  Stellt einen Hinweis für Clientanwendungen bezüglich der Anzeige einer Liste von Elementen bereit, der auf der erwarteten Anzahl von Elementen in der Liste basiert.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <InstanceSelection>...</InstanceSelection>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Keine*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DimensionAttribute-Objekt](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der folgenden Zeichenfolgen beschränkt:  
  
|value|Description|  
|-----------|-----------------|  
|*Keine*|Keine Auswahlliste anzeigen. Ermöglicht es den Benutzern, Werte direkt einzugeben.|  
|*Dropdownliste*|Die Anzahl der Elemente ist klein genug für die Anzeige in einer Dropdownliste.|  
|*Listee*|Die Anzahl der Elemente ist zu groß für eine Dropdownliste, erfordert aber keine Filter.|  
|*FilteredList*|Die Anzahl der Elemente ist groß genug, dass das Anwenden von Filtern für ihre Anzeige sinnvoll ist.|  
|*MandatoryFilter*|Die Anzahl der Elemente ist so groß, dass die Anzeige immer gefiltert werden muss.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `InstanceSelection` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
