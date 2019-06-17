---
title: STCurveToLine (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCurveToLine_TSQL
- STCurveToLine
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveToLine method (geography)
ms.assetid: 2f863a85-6168-465a-b32f-bb5e3de58dee
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 7f237da350b47ea0c3141709cd82d083ef509196
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65939195"
---
# <a name="stcurvetoline-geography-data-type"></a>STCurveToLine (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt eine polygonale Näherung einer Instanz von **geography** mit Kreisbogensegmenten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STCurveToLine()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Gibt eine **LineString** -Instanz für eine **CircularString** - oder **CompoundCurve** -Instanz zurück.  
  
 Gibt eine **Polygon** -Instanz für eine **CurvePolygon** -Instanz zurück.  
  
 Gibt eine Kopie von **geography** -Instanzen zurück, die keine **CircularString**, **CompoundCurve**-Instanz und keine **CurvePolygon** -Instanz enthalten.  
  
 Im Gegensatz zur SQL MM-Spezifikation werden bei dieser Methode keine Werte der Z-Koordinate zur Berechnung der polygonalen Näherung verwendet. In der aufrufenden **geography**-Instanz enthaltene Werte der Z-Koordinate werden ignoriert.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -Instanz zurückgegeben, die eine polygonale Näherung einer `CircularString` -Instanz ist:  
  
```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography;  
 SET @g2 = @g1.STCurveToLine();  
 SELECT @g1.STNumPoints() AS G1, @g2.STNumPoints() AS G2;
 ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [STLength &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/stlength-geography-data-type.md)   
 [STNumPoints &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/stnumpoints-geography-data-type.md)   
 [Übersicht über räumliche Datentypen](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
