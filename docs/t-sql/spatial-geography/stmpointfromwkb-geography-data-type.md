---
title: STMPointFromWKB (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STMPointFromWKB (geography Data Type)
- STMPointFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB method
ms.assetid: eeb7d806-3cbb-405d-8199-8b82282c53df
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 8056e60488ee156e86ca0462dfb436ad6d22bd7a
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555764"
---
# <a name="stmpointfromwkb-geography-data-type"></a>STMPointFromWKB (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt eine **geographyMultiPoint**-Instanz einer Open Geospatial-Konsortium (OGC) WKB-Darstellung (Well-Known binary) zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STMPointFromWKB ( 'WKB_multipoint' , SRID )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *WKB_multipoint*  
 Die WKB-Darstellung der **geographyMultiPoint**-Instanz, die zurückgegeben werden soll. *WKB_multipoint* ist ein **varbinary(max)** -Ausdruck.  
  
 *SRID*  
 Ein **int**-Ausdruck, der die SRID (Spatial Reference ID) der **geographyMultiPoint**-Instanz darstellt, die Sie zurückgeben möchten.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
 OGC-Typ: **MultiPoint**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STMPointFromWKB()` verwendet, um eine `geography`-Instanz zu erstellen.  
  
```  
DECLARE @g geography;   
SET @g = geography::STMPointFromWKB(0x0104000000020000000101000000D7A3703D0A975EC08716D9CEF7D347400101000000CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Statische geography-Methoden des OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
