---
title: STPointFromText (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointFromText (geography Data Type)
- STPointFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromText method
ms.assetid: e5fe54dc-0007-4631-8dde-7ae4d4c41f6e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d5fe71b55325297a4267901e380831c4df889629
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68120842"
---
# <a name="stpointfromtext-geography-data-type"></a>STPointFromText (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt eine **geography** -Instanz von einer Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung zurück, die um alle von der Instanz getragenen Z (Höhe)- und M (Measure)-Werte erweitert ist.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STPointFromText ( 'point_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argumente  
 *point_tagged_text*  
 Die WKT-Darstellung der Instanz von **geographyPoint**, die zurückgegeben werden soll. *point_tagged_text* ist ein **nvarchar(max)** -Ausdruck.  
  
 *SRID*  
 Ein **int**-Ausdruck, der die SRID (Spatial Reference ID) der **geographyPoint**-Instanz darstellt, die zurückgegeben werden soll.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
 OGC-Typ: **Point**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STPointFromText()` verwendet, um eine `geography`-Instanz zu erstellen.  
  
```  
DECLARE @g geography;  
SET @g = geography::STPointFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Statische geography-Methoden des OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
