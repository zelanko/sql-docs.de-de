---
title: MultiPoint | Microsoft-Dokumentation
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: c06ed0be91d64e02f30d6ef4fbebb68e3b9a1272
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014164"
---
# <a name="multipoint"></a>MultiPoint
  Ein `MultiPoint` ist eine Auflistung von null oder mehr Punkten. Die Begrenzung einer `MultiPoint`-Instanz ist leer.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `geometry MultiPoint` -Instanz mit dem SRID 23 und zwei Punkten erstellt: ein Punkt mit den Koordinaten (2, 3), ein Punkt mit den Koordinaten (7, 8) und ein Z-Wert von 9,5.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Diese `MultiPoint` -Instanz kann auch mit `STMPointFromText()` ausgedrückt werden, wie unten dargestellt.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Im folgenden Beispiel wird mit der Methode `STGeometryN()` eine Beschreibung des ersten Punkts der Auflistung abgerufen.  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Punkt](point.md)   
 [Räumliche Daten &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
