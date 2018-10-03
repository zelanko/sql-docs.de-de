---
title: DisplayKeyPosition-Element (XML) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 345a24e6-186c-4570-baf2-7bfe9b7b4cc1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 325fe14a5df51a49833485926ba10ee3f05f5bbe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48127970"
---
# <a name="displaykeyposition-element-xml"></a>DisplayKeyPosition-Element (XML)
  Enthält Informationen zur Position des Elements in einer Auflistung von Elementen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <DisplayKeyPosition>...</DisplayKeyPosition>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Integer|  
|Standardwert|-1|  
|Cardinality|0-1: Optionales Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Für `RelationshipEndVisualizationProperties`-Elemente enthält das `DisplayKeyPosition`-Element die Position des Anzeigeschlüsselelements in einer Auflistung von Details. Der Standardwert gibt an, dass kein zu verwendender Anzeigeschlüssel vorhanden ist.  
  
  
