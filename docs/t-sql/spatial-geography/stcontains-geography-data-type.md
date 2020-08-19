---
description: STContains (geography-Datentyp)
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
ms.openlocfilehash: d3e9b03eac0107792b9b0cdb59359f5ad70b5474
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459079"
---
# <a name="stcontains--geography-data-type"></a>STContains (geography-Datentyp)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Gibt an, ob die aufrufende **geography**-Instanz die an die Methode übergebene **geography**-Instanz räumlich enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STContains ( other_geography )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *other_geography*  
 Eine andere **geography**-Instanz zum Vergleich mit der Instanz, in der `STContains()` aufgerufen wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Hinweise  
 Gibt 1 zurück, wenn die aufrufende **geography**-Instanz die an die Methode übergebene **geography**-Instanz räumlich enthält, und gibt andernfalls 0 (null) zurück. Gibt **NULL** zurück, wenn die SRID der beiden **geography**-Instanzen nicht übereinstimmt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STContains()` verwendet, um zwei `geography`-Instanzen daraufhin zu überprüfen, ob die erste Instanz die zweite Instanz enthält.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SET @h = geography::Parse('POINT(-121.703796 46.893985)');  
```  
  
 `SELECT @g.STContains(@h);`  
  
  
