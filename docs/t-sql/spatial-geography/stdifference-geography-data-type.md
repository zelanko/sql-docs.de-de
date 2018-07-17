---
title: STDifference (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8eeb7743ed17f9bd2bbd837b02357723cbb0f49e
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36253932"
---
# <a name="stdifference-geography-data-type"></a>STDifference (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt ein Objekt zurück, das die Punktmenge einer **geography** -Instanz darstellt, die sich außerhalb einer anderen **geography** -Instanz befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Argumente  
 *other_geography*  
 Eine andere **geography**-Instanz, die angibt, welche Punkte aus der Instanz zu entfernen sind, in der STDifference() aufgerufen wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="exceptions"></a>Ausnahmen  
 Diese Methode löst eine **ArgumentException** aus, wenn die Instanz eine gegenüberliegende Kante enthält.  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt immer NULL zurück, wenn die SRIDs (Spatial Reference IDs) der **geography** -Instanzen nicht übereinstimmen.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurden die Ergebnisse, die auf dem Server zurückgegeben werden können, um **FullGlobe**-Instanzen erweitert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt räumliche Instanzen, die größer als eine Hemisphäre sind. Im Ergebnis können nur dann Kreisbogensegmente enthalten sein, wenn die Eingabeinstanzen auch Kreisbogensegmente enthalten. Diese Methode ist nicht exakt.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Berechnen des Unterschiedes zwischen zwei geography-Instanzen  
 Im folgenden Beispiel wird `STDifference()` zum Berechnen der Differenz zwischen zwei **geography** -Instanzen erweitert.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-using-a-fullglobe-with-stdifference"></a>B. Verwenden eines FullGlobe mit STDifference()  
 Im folgenden Beispiel wird eine Instanz von `FullGlobe` verwendet. Das erste Ergebnis ist eine leere `GeometryCollection` , und das zweite Ergebnis ist eine `Polygon` -Instanz. `STDifference()` gibt eine leere `GeometryCollection` zurück, wenn der Parameter eine `FullGlobe`-Instanz ist. Alle Punkte in einer aufrufenden Instanz von `geography` sind in einer Instanz von `FullGlobe` enthalten.  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 DECLARE @h geography = 'FULLGLOBE';  
 SELECT @g.STDifference(@h).ToString(),  
 @h.STDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
