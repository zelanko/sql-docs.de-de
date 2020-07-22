---
title: Point (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/10/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point method
- Point (geography Data Type)
ms.assetid: 0dc6f422-7aae-4016-b7f4-3289fa8f989c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 04db3c6617669010f63e173415de0ebf6b7a3dca
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86556159"
---
# <a name="point-geography-data-type"></a>Point (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Erstellt eine **geography**-Instanz, die mit ihren Breitengrad- und Längengradwerten sowie der SRID (Spatial Reference ID) eine **Point**-Instanz darstellt.
  
## <a name="syntax"></a>Syntax  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *Lat*  
 Ein **float**-Ausdruck, der die Y-Koordinate der zu erstellenden **Point**-Instanz darstellt.  
  
 *Long*  
 Ein **float**-Ausdruck, der die X-Koordinate der zu erstellenden **Point**-Instanz darstellt. Weitere Informationen zu gültigen Breiten- und Längenwerten finden Sie unter [Point](../../relational-databases/spatial/point.md).  
  
 *SRID*  
 Ein **int**-Ausdruck, der die [Spatial Reference ID](https://docs.microsoft.com/sql/relational-databases/spatial/spatial-reference-identifiers-srids) der **geography**-Instanz darstellt, die Sie zurückgeben möchten.  
  
> [!NOTE]  
>  Argumente für die Punktemethode (Geography-Datentyp) besitzen umgekehrte Koordinaten im Vergleich zu WKT.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `Point()` verwendet, um eine `geography`-Instanz zu erstellen.  
  
```  
DECLARE @g geography;   
SET @g = geography::Point(47.65100, -122.34900, 4326)  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte statische geography-Methoden](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
