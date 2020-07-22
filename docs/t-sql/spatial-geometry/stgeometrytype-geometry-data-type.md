---
title: STGeometryType (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryType_TSQL
- STGeometryType (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryType (geometry Data Type)
ms.assetid: 224cdc83-aa83-4ad4-bb82-b7481031e910
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a842e3ee2dcfb86f293e8ae3feba1a30665ffbe0
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554636"
---
# <a name="stgeometrytype-geometry-data-type"></a>STGeometryType (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt den durch eine **geometry**-Instanz dargestellten Open Geospatial Consortium (OGC)-Typnamen zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STGeometryType ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(4000)**  
  
 CLR-Rückgabetyp: **SqlString**  
  
## <a name="remarks"></a>Bemerkungen  
 Die OGC-Typnamen, die von `STGeometryType()` zurückgegeben werden können, sind **Point**, **LineString**, **CircularString**, **CompoundCurve**, **Polygon, CurvePolygon**, **GeometryCollection**, **MultiPoint**, **MultiLineString** und **MultiPolygon**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiels wird eine Instanz von `Polygon` erstellt, und mit `STGeometryType()` wird bestätigt, dass es sich um ein Polygon handelt.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0))', 0);  
SELECT @g.STGeometryType();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

