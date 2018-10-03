---
title: DefaultDetailsPosition-Element (XML) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 851ad331-aefd-4277-a5e5-e32a8f5c5e22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95e8f7cecdd76ceb934f2c1d9d9483d8146e8e0d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083410"
---
# <a name="defaultdetailsposition-element-xml"></a>DefaultDetailsPosition-Element (XML)
  Enthält Informationen zur Position des Elements in einer Auflistung von Elementen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <DefaultDetailsPosition>...</DefaultDetailsPosition>  
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
 Für `RelationshipEndVisualizationProperties`-Elemente enthält das `DefaultDetailsPosition`-Element die Position des standardmäßigen Detailelements in einer Auflistung von Details. Der Standardwert von `false` gibt keine zu verwendenden Standarddetails vorhanden ist.  
  
  
