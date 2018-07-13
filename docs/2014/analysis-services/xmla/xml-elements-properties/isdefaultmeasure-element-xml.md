---
title: IsDefaultMeasure-Element (XML) | Microsoft-Dokumentation
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
ms.assetid: 523cf3d7-9df0-4f9d-8486-9109de8d3cca
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c89445c0e31187951b4b4a9f2bbd6f97733e9572
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190850"
---
# <a name="isdefaultmeasure-element-xml"></a>IsDefaultMeasure-Element (XML)
  Gibt an, dass die Möglichkeit besteht, das Standardmeasure für diese Entität durch Navigieren von dieser Beziehung zur anderen Tabelle und durch Abrufen des Members mit dem Attribut "DefaultMeasure" abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultMeasure>...</IsDefaultMeasure>  
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
|Übergeordnete Elemente|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Für `RelationshipEndVisualizationProperties` Elemente, die `IsDefaultMeasure` Element gibt an, dass das Standardmeasure für diese Entität durch Navigieren zum anderen Ende dieser Beziehung abgerufen werden. Der Standardwert von `false` zeigt an, dass kein abzurufendes Standardmeasure abgerufen werden sollen.  
  
  
