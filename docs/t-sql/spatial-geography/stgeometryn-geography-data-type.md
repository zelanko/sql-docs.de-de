---
title: STGeometryN (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 0c05ded2f6c00dd4c2f28336fb5054796f40607d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85703260"
---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt ein bestimmtes **geography**-Element in einer **GeometryCollection** oder in einem ihrer Untertypen zurück. Wenn STGeometryN() für den Untertyp einer **GeometryCollection** wie **MultiPoint** oder **MultiLineString** verwendet wird, gibt diese Methode bei einem Aufruf mit N=1 die **geography**-Instanz zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein **int**-Ausdruck zwischen 1 und der Anzahl der **geography**-Instanzen in der **GeometryCollection**.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt NULL zurück, wenn der Parameter größer als das Ergebnis von [STNumGeometries()](../../t-sql/spatial-geography/stnumgeometries-geography-data-type.md) ist und löst eine **ArgumentOutOfRangeException** aus, wenn der *expression*-Parameter kleiner als 1 ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `MultiPoint``geography`-Instanz erstellt und `STGeometryN()` verwendet, um nach der zweiten `geography`-Instanz in der **GeometryCollection** zu suchen.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
