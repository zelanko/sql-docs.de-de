---
title: ADO MD-Objekte | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c06214d23441782cbe5e14433b16928224d5d48c
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66709848"
---
# <a name="ado-md-objects"></a>ADO MD-Objekte

|||  
|-|-|  
|[Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|Stellt eine mit Feldern fester Breite oder Filterachse eines cellSets, die mit der ausgewählten Elemente ein oder mehrere Dimensionen.|  
|[Katalog](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|Mehrdimensionale Schemainformationen (d. h. Cubes und zugrunde liegenden Dimensionen, Hierarchien, Ebenen und Elemente), die speziell für eine mehrdimensionale Datenanbieter (MDP) enthält.|  
|[Cell](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|Stellt die Daten am Schnittpunkt der Achsenkoordinaten enthalten, die in einem Cellset dar.|  
|[Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|Stellt die Ergebnisse einer MDX-Abfrage. Es ist eine Auflistung von Zellen, die aus Cubes oder anderen Cellsets ausgewählt.|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|Stellt einen Cube aus einem mehrdimensionalen Schema, das mit einem Satz von verknüpften Dimensionen dar.|  
|[Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|Stellt eine der Dimensionen eines mehrdimensionalen Cubes, die mit einer oder mehreren Hierarchien von Elementen dar.|  
|[Hierarchy](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|Stellt eine Möglichkeit dar, in dem die Elemente einer Dimension können aggregiert oder "wird durchgeführt." Eine Dimension kann entlang einer oder mehreren Hierarchien aggregiert werden.|  
|[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)|Enthält eine Menge von Elementen, von die jede den gleichen Rang innerhalb einer Hierarchie hat.|  
|[Member](../../../ado/reference/ado-md-api/member-object-ado-md.md)|Stellt ein Element einer Ebene in einem Cube, die untergeordneten Elemente ein Element einer Ebene oder ein Mitglied einer Position auf einer Achse eines cellSets dar.|  
|[Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)|Stellt einen Satz von ein oder mehrere Elemente verschiedener Dimensionen, der einen Punkt auf einer Achse definiert.|  
  
 Darüber hinaus die **Katalog** -Objekt verbunden ist, um ein ADO **Verbindung** -Objekt, das in der standard-ADO-Bibliothek enthalten ist:  
  
|Objekt|Description|  
|------------|-----------------|  
|[Verbindung](../../../ado/reference/ado-api/connection-object-ado.md)|Stellt eine offene Verbindung mit einer Datenquelle dar.|  
  
 Die Beziehungen zwischen diesen Objekten werden dargestellt, der [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md).  
  
 Viele ADO MD-Objekte können in eine entsprechende Sammlung enthalten sein. Z. B. eine [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) Objekt enthalten sein kann, eine [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) Auflistung von einem **Katalog**. Weitere Informationen finden Sie unter [ADO MD-Auflistungen](../../../ado/reference/ado-md-api/ado-md-collections.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ADO MD-API-Referenz](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [ADO MD-Codebeispiele](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [ADO MD-Auflistungen](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [ADO MD-Enumerationskonstanten](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [ADO MD-Methoden](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO MD-Eigenschaften](../../../ado/reference/ado-md-api/ado-md-properties.md)
