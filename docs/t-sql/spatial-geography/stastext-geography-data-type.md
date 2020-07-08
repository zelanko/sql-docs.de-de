---
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
ms.openlocfilehash: 207341d09f153ed819d331960cf00dbb6c410bf3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85704952"
---
# <a name="stastext-geography-data-type"></a>STAsText (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung einer **geography**-Instanz zurück. Dieser Text enthält keine Z (Höhe)- oder M (Measure)-Werte, die von der Instanz getragen werden.  
  
 Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlChars**  
  
## <a name="remarks"></a>Bemerkungen  
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
  
  
