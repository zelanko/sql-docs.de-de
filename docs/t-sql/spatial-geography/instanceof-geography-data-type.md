---
title: InstanceOf (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf method
ms.assetid: 1eaed0e4-1c72-45a9-9926-5b513335cf33
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 09d468b4f39ba50a0c195287961f3c3dc76e0ccd
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552925"
---
# <a name="instanceof-geography-data-type"></a>InstanceOf (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Überprüft die Übereinstimmung der **geography**-Instanz mit dem angegebenen Typ.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
  
.InstanceOf ( 'geography_type')  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
*geography_type*  
Eine **nvarchar(4000)** -Zeichenfolge, die einen von 16 Typen angibt, die in der **geography**-Typhierarchie verfügbar gemacht werden.  
  
## <a name="return-types"></a>Rückgabetypen  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Bemerkungen  
Gibt 1 zurück, wenn der Typ einer **geography**-Instanz mit dem angegebenen Typ übereinstimmt oder der angegebene Typ ein Vorgänger des Instanztyps ist. Andernfalls wird 0 zurückgegeben.  
  
Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
Die Eingabe für die Methode muss einem der folgenden Typen entsprechen: Geometry, Point, Curve, LineString, CircularString, Surface, Polygon, CurvePolygon, **GeometryCollection**, **MultiSurface**, **MultiPolygon, MultiCurve, MultiLineString**, **MultiPoint** oder **FullGlobe**.  
  
Diese Methode löst eine `ArgumentException` aus, wenn Sie andere Zeichenfolgen als die genannten für die Eingabe verwenden.  
  
Diese Methode ist nicht exakt.  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird eine `MultiPoint`-Instanz erstellt und `InstanceOf()` verwendet, um zu überprüfen, ob die Instanz eine `GeometryCollection` ist.  
  
```sql  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
