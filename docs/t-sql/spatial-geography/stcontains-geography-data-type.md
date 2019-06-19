---
title: STContains (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STContains method (geography)
ms.assetid: b10e8f0a-2926-449a-82ea-be42543420ca
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 6aa5b37955db2aace7785f7a39b768807e7b0e3d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937140"
---
# <a name="stcontains--geography-data-type"></a>STContains (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt an, ob die aufrufende **geography**-Instanz die an die Methode übergebene **geography**-Instanz räumlich enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STContains ( other_geography )  
```  
  
## <a name="arguments"></a>Argumente  
 *other_geography*  
 Eine andere **geography**-Instanz zum Vergleich mit der Instanz, in der `STContains()` aufgerufen wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Gibt 1 zurück, wenn die aufrufende **geography**-Instanz die an die Methode übergebene **geography**-Instanz räumlich enthält, und gibt andernfalls 0 (null) zurück. Gibt **NULL** zurück, wenn die SRID der beiden **geography**-Instanzen nicht übereinstimmt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STContains()` verwendet, um zwei `geography` -Instanzen daraufhin zu überprüfen, ob die erste Instanz die zweite Instanz enthält.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SET @h = geography::Parse('POINT(-121.703796 46.893985)');  
```  
  
 `SELECT @g.STContains(@h);`  
  
  
