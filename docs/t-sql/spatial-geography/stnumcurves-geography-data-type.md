---
description: STNumCurves (geography-Datentyp)
title: STNumCurves (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumCurves
- STNumCurves_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geography)
ms.assetid: e98a56c2-8496-4dfd-9b37-7f3c4ca9b2b5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3f2d2eead1803745d58cc827b85acd612f925a0e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88306041"
---
# <a name="stnumcurves-geography-data-type"></a>STNumCurves (geography-Datentyp)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Anzahl der Kurven in einer eindimensionalen Instanz von **geography** zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STNumCurves()  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Bemerkungen  
 Eindimensionale räumliche Datentypen schließen **LineString**, **CircularString**und **CompoundCurve**ein. Eine leere eindimensionale Instanz von **geography** gibt 0 zurück.  
  
 `STNumCurves`() funktioniert nur mit einfachen Typen; **geography**-Collection wie **MultiLineString** gehören nicht dazu. Wenn die Instanz von**NULL** kein eindimensionaler Datentyp ist, wird **geography** zurückgegeben.  
  
 **Null** wird für nicht initialisierte Instanzen von **geography** zurückgegeben.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. Verwenden von STNumCurves() in einer CircularString-Instanz  
 Im folgenden Beispiel wird gezeigt, wie die Anzahl der Kurven einer Instanz von `CircularString` abgerufen wird:  
  
```
 DECLARE @g geography; 
 SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. Verwenden von STNumCurves() in einer CompoundCurve-Instanz  
 Im folgenden Beispiel wird mit `STNumCurves()` die Anzahl der Kurven in einer Instanz von `CompoundCurve` zurückgegeben.  
  
```
 DECLARE @g geography;  
 SET @g = geography::Parse('COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über räumliche Datentypen](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
