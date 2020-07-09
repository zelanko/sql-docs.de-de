---
title: GeomFromGML (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GeomFromGML_TSQL
- GeomFromGML
dev_langs:
- TSQL
helpviewer_keywords:
- GeomFromGML (geography Data Type)
- GeomFromGML method
ms.assetid: 470d0997-3cb0-4d34-9a45-b332fe432b14
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b26d8a7fa1c72a3c31f43d6d8e99bfceedde96a0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731199"
---
# <a name="geomfromgml-geography-data-type"></a>GeomFromGML (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Erstellt eine **geography**-Instanz auf der Grundlage einer Darstellung in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Teilmenge von GML (Geography Markup Language).
  
Weitere Informationen über GML finden Sie in den folgenden OGC-Spezifikationen (Open Geospatial Consortium): [OGC Specifications, Geography Markup Language (OGC-Spezifikationen, Geography Markup Language)](https://go.microsoft.com/fwlink/?LinkId=93629)
  
Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.
  
## <a name="syntax"></a>Syntax  
  
```  
  
GeomFromGml ( GML_input, SRID )  
```  
  
## <a name="arguments"></a>Argumente  
 *GML_input*  
 Eine XML-Eingabe, aus der GML einen Wert zurückgibt.  
  
 *SRID*  
 Ein **int** -Ausdruck, der die SRID (Spatial Reference ID) der Instanz von **geography** darstellt, die zurückgegeben wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
 Diese Methode löst **ArgumentException** aus, wenn die Eingabe einen gegenüberliegenden Edge enthält.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `GeomFromGml()` verwendet, um eine `geography`-Instanz zu erstellen.  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<LineString xmlns="https://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
 Im folgenden Beispiel wird `GeomFromGml()` verwendet, um eine `FullGlobe``geography`-Instanz zu erstellen.  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<FullGlobe xmlns="https://schemas.microsoft.com/sqlserver/2011/geography" />';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte statische geography-Methoden](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
