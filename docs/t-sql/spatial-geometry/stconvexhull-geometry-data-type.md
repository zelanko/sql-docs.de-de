---
title: STConvexHull (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STConvexHull (geometry Data Type)
- STConvexHull_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull (geometry Data Type)
ms.assetid: 60a520a6-1a7c-486b-8d91-34401edf6233
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c8e05b92fdbbcfb34d4e1eb82c4bf159d911b628
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555648"
---
# <a name="stconvexhull-geometry-data-type"></a>STConvexHull (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt ein Objekt zurück, das die konvexe Hülle einer **geometry**-Instanz darstellt.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STConvexHull ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="remarks"></a>Bemerkungen  
 `STConvexHull()` gibt das kleinste konvexe Polygon zurück, das die angegebene **geometry**-Instanz enthält. **Points** oder kolineare **LineString**-Instanzen erzeugen eine Instanz vom gleichen Typ wie die Eingabe.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STConvexHull()` verwendet, um die konvexe Hülle einer nicht-konvexen `Polygon``geometry`-Instanz zu suchen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 1 1, 2 2, 2 0, 0 0))', 0);  
SELECT @g.STConvexHull().ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

