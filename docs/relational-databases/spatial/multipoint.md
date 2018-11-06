---
title: MultiPoint | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1cf571df37585a4a3e575d03b8cc1cd905fdffd1
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018575"
---
# <a name="multipoint"></a>MultiPoint
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ein **MultiPoint** ist eine Auflistung von null oder mehr Punkten. Die Begrenzung einer **MultiPoint** -Instanz ist leer.  
  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Punkt](../../relational-databases/spatial/point.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
