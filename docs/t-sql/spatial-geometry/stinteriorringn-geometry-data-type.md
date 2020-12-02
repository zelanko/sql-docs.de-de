---
description: STInteriorRingN (geometry-Datentyp)
title: STInteriorRingN (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 52d1f15affc8f253303bb636c4b94f280e8a3319
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88479267"
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt den angegebenen inneren Ring einer **Polygongeometry**-Instanz zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *expression*  
 Ein **int**-Ausdruck zwischen 1 und der Anzahl der inneren Ringe in der **geometry**-Instanz.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC)-Typ: **LineString**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt **null** zurück, wenn die **geometry** -Instanz kein Polygon ist. Diese Methode löst außerdem eine **ArgumentOutOfRangeException** aus, wenn der Ausdruck größer als die Anzahl der Ringe ist. Die Anzahl der Ringe kann mithilfe von `STNumInteriorRing``()` zurückgegeben werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Polygon`-Instanz erstellt und dann mithilfe von `STInteriorRingN()` der innere Ring des Polygons als **LineString** zurückgegeben.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

