---
description: STAsText (geography-Datentyp)
title: STAsText (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STAsText (geography Data Type)
- STAsText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STAsText method
ms.assetid: d3d2635d-ca6c-4205-9d6c-eb939ee314fd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f89f2c2889d880388f74b563abc9aefe1eb28c82
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88422314"
---
# <a name="stastext-geography-data-type"></a>STAsText (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung einer **geography**-Instanz zurück. Dieser Text enthält keine Z (Höhe)- oder M (Measure)-Werte, die von der Instanz getragen werden.  
  
 Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STAsText ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlChars**  
  
## <a name="remarks"></a>Hinweise  
 Der OGC-Typ einer **geography**-Instanz kann durch einen Aufruf von [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md) bestimmt werden.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wurden die Ergebnisse, die auf dem Server zurückgegeben werden können, um **FullGlobe**-Instanzen erweitert.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mithilfe von `STAsText()` eine `LineString``geography`-Instanz von (–122,360; 47,656) bis (-122,343; 47,656) aus Text erstellt. Anschließend wird das Ergebnis als Text zurückgegeben.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
