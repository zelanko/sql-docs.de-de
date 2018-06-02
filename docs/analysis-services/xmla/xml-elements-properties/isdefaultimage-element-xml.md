---
title: IsDefaultImage-Element (XML) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cf053ce660091fa9b47048e9dccb9b7f470acaad
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575352"
---
# <a name="isdefaultimage-element-xml"></a>IsDefaultImage-Element (XML)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Gibt an, dass die Möglichkeit besteht, das Standardimage für diese Entität durch Navigieren von dieser Beziehung zur anderen Tabelle und durch Abrufen des Members mit dem Attribut "IsDefaultImage" abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultImage>...</IsDefaultImage>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|false|  
|Cardinality|0-1: Optionales Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[RelationshipEndVisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Für **RelationshipEndVisualizationProperties** -Elemente gibt das **IsDefaultImage** -Element an, dass das Standardimage für diese Entität durch Navigieren zum anderen Ende dieser Beziehung abgerufen werden kann. Der Standardwert **false** gibt an, dass kein abzurufendes Standardimage vorhanden ist.  
  
  
