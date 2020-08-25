---
description: ADO MD-Objekte
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
ms.openlocfilehash: bb297a35594cad76543713eb45d48b150d53aa0c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776719"
---
# <a name="ado-md-objects"></a>ADO MD-Objekte

|Object|Beschreibung|  
|-|-|  
|[Achse](./axis-object-ado-md.md)|Stellt eine Positions-oder Filter Achse eines Cellsets dar, die ausgewählte Elemente aus einer oder mehreren Dimensionen enthält.|  
|[Katalog](./catalog-object-ado-md.md)|Enthält mehrdimensionale Schema Informationen (d. h. Cubes und zugrunde liegende Dimensionen, Hierarchien, Ebenen und Elemente), die für einen mehrdimensionalen Datenanbieter (MDP) spezifisch sind.|  
|[Cell (Zelle)](./cell-object-ado-md.md)|Stellt die Daten an der Schnittmenge der Achsen Koordinaten dar, die in einem CellSet enthalten sind.|  
|[Cellset](./cellset-object-ado-md.md)|Stellt die Ergebnisse einer mehrdimensionalen Abfrage dar. Es handelt sich um eine Sammlung von Zellen, die aus Cubes oder anderen Cellsets ausgewählt wurden.|  
|[CubeDef](./cubedef-object-ado-md.md)|Stellt einen Cube aus einem mehrdimensionalen Schema dar, der einen Satz verwandter Dimensionen enthält.|  
|[Dimension](./dimension-object-ado-md.md)|Stellt eine der Dimensionen eines mehrdimensionalen Cubes dar, der mindestens eine Hierarchien von Membern enthält.|  
|[Hierarchy](./hierarchy-object-ado-md.md)|Stellt eine Methode dar, mit der die Elemente einer Dimension aggregiert oder "ein Rollup ausgeführt werden können". Eine Dimension kann entlang einer oder mehrerer Hierarchien aggregiert werden.|  
|[Level](./level-object-ado-md.md)|Enthält einen Satz von Membern, von denen jeder denselben Rang innerhalb einer Hierarchie aufweist.|  
|[Member](./member-object-ado-md.md)|Stellt einen Member einer Ebene in einem Cube, die untergeordneten Elemente eines Members einer Ebene oder einen Member einer Position entlang einer Achse eines Cellsets dar.|  
|[Position](./position-object-ado-md.md)|Stellt einen Satz von einem oder mehreren Membern verschiedener Dimensionen dar, die einen Punkt auf einer Achse definieren.|  
  
 Außerdem ist das **catalog** -Objekt mit einem ADO- **Verbindungs** Objekt verbunden, das in der Standard-ADO-Bibliothek enthalten ist:  
  
|Object|Beschreibung|  
|------------|-----------------|  
|[Connection](../ado-api/connection-object-ado.md)|Stellt eine offene Verbindung mit einer Datenquelle dar.|  
  
 Die Beziehungen zwischen diesen Objekten werden im [ADO MD Objektmodell](./ado-md-object-model.md)veranschaulicht.  
  
 Viele ADO MD Objekte können in einer entsprechenden Sammlung enthalten sein. Ein [CubeDef](./cubedef-object-ado-md.md) -Objekt kann z. b. in einer [CubeDefs](./cubedefs-collection-ado-md.md) -Sammlung eines **Katalogs**enthalten sein. Weitere Informationen finden Sie unter [ADO MD Collections](./ado-md-collections.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Referenz für ADO MD](./ado-md-object-model.md?view=sql-server-ver15)   
 [ADO MD Code Beispiele](./ado-md-code-examples.md)   
 [ADO MD Sammlungen](./ado-md-collections.md)   
 [Enumerationskonstanten ADO MD](./ado-md-enumerated-constants.md)   
 [ADO MD Methoden](./ado-md-methods.md)   
 [ADO MD-Objektmodell](./ado-md-object-model.md)   
 [ADO MD-Eigenschaften](./ado-md-properties.md)