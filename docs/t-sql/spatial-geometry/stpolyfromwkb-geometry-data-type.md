---
title: STPolyFromWKB (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPolyFromWKB_TSQL
- STPolyFromWKB (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPolyFromWKB (geometry Data Type)
ms.assetid: 8e8f0c41-0c62-4919-9d4c-d37c93fdd31c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 6b732254b9b900a2513243641f8a309695d5eaf9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762186"
---
# <a name="stpolyfromwkb-geometry-data-type"></a>STPolyFromWKB (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt eine **geometryPolygon**-Instanz einer OGC-WKB-Darstellung (Open Geospatial Consortium, Well-Known Binary) zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STPolyFromWKB ( 'WKB_polygon' , SRID )  
```  
  
## <a name="arguments"></a>Argumente  
 *WKB_polygon*  
 Die WKB-Darstellung der Instanz von **geometryPolygon**, die zurückgegeben werden soll. *WKB_polygon* ist ein **varbinary(max)** -Ausdruck.  
  
 *SRID*  
 Ein **int**-Ausdruck, der die SRID (Spatial Reference ID) der **geometryPolygon**-Instanz darstellt, die zurückgegeben werden soll.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 OGC-Typ: **Polygon**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STPolyFromWKB()` verwendet, um eine `geometry`-Instanz zu erstellen.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPolyFromWKB(0x0103000000010000000400000000000000000014400000000000001440000000000000244000000000000014400000000000002440000000000000244000000000000014400000000000001440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Statische geometry-Methoden des OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

