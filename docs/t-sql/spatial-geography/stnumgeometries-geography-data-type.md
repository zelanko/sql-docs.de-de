---
title: STNumGeometries (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STNumGeometries (geography Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries method
ms.assetid: 6ae7fac2-62f1-420f-9fc9-a09606be9605
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f3bd4102d8337c7a2b3f22d6c123ad23a1fe03c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33062827"
---
# <a name="stnumgeometries-geography-data-type"></a>STNumGeometries (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die Anzahl der **geometries** -Instanzen zurück, aus denen die **geography** -Instanz besteht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **int**  
  
 CLR-Rückgabetyp: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt 1 zurück, wenn die **geography** -Instanz keine **MultiPoint**-, **MultiLineString**-, **MultiPolygon**- oder **GeometryCollection** -Instanz ist. Sie gibt 0 zurück, wenn die **geography** -Instanz leer ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `MultiPoint` -Instanz erstellt und `STNumGeometries()` verwendet, um festzustellen, wieviele **geometries** die Instanz enthält.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT((-122.360 47.656), (-122.343 47.656))', 4326);  
SELECT @g.STNumGeometries();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
