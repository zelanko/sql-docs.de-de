---
title: ADO MD Objekte | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, objects
- objects [ADO MD]
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
author: rothja
ms.author: jroth
ms.openlocfilehash: 01a35a38812d105a1e26454022321e57448efadd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765251"
---
# <a name="ado-md-objects"></a>ADO MD-Objekte

|||  
|-|-|  
|[Achse](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|Stellt eine Positions-oder Filter Achse eines Cellsets dar, die ausgewählte Elemente aus einer oder mehreren Dimensionen enthält.|  
|[Katalog](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|Enthält mehrdimensionale Schema Informationen (d. h. Cubes und zugrunde liegende Dimensionen, Hierarchien, Ebenen und Elemente), die für einen mehrdimensionalen Datenanbieter (MDP) spezifisch sind.|  
|[Kern](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|Stellt die Daten an der Schnittmenge der Achsen Koordinaten dar, die in einem CellSet enthalten sind.|  
|[Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|Stellt die Ergebnisse einer mehrdimensionalen Abfrage dar. Es handelt sich um eine Sammlung von Zellen, die aus Cubes oder anderen Cellsets ausgewählt wurden.|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|Stellt einen Cube aus einem mehrdimensionalen Schema dar, der einen Satz verwandter Dimensionen enthält.|  
|[Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|Stellt eine der Dimensionen eines mehrdimensionalen Cubes dar, der mindestens eine Hierarchien von Membern enthält.|  
|[Hierarchy](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|Stellt eine Methode dar, mit der die Elemente einer Dimension aggregiert oder "ein Rollup ausgeführt werden können". Eine Dimension kann entlang einer oder mehrerer Hierarchien aggregiert werden.|  
|[Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md)|Enthält einen Satz von Membern, von denen jeder denselben Rang innerhalb einer Hierarchie aufweist.|  
|[Member](../../../ado/reference/ado-md-api/member-object-ado-md.md)|Stellt einen Member einer Ebene in einem Cube, die untergeordneten Elemente eines Members einer Ebene oder einen Member einer Position entlang einer Achse eines Cellsets dar.|  
|[Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)|Stellt einen Satz von einem oder mehreren Membern verschiedener Dimensionen dar, die einen Punkt auf einer Achse definieren.|  
  
 Außerdem ist das **catalog** -Objekt mit einem ADO- **Verbindungs** Objekt verbunden, das in der Standard-ADO-Bibliothek enthalten ist:  
  
|Object|BESCHREIBUNG|  
|------------|-----------------|  
|[Connection](../../../ado/reference/ado-api/connection-object-ado.md)|Stellt eine offene Verbindung mit einer Datenquelle dar.|  
  
 Die Beziehungen zwischen diesen Objekten werden im [ADO MD Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)veranschaulicht.  
  
 Viele ADO MD Objekte können in einer entsprechenden Sammlung enthalten sein. Ein [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) -Objekt kann z. b. in einer [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) -Sammlung eines **Katalogs**enthalten sein. Weitere Informationen finden Sie unter [ADO MD Collections](../../../ado/reference/ado-md-api/ado-md-collections.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Referenz für ADO MD](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [ADO MD Code Beispiele](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [ADO MD Sammlungen](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [Enumerationskonstanten ADO MD](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [ADO MD Methoden](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO MD-Eigenschaften](../../../ado/reference/ado-md-api/ado-md-properties.md)
