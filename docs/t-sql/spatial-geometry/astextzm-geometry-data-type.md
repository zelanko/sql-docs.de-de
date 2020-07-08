---
title: AsTextZM (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsTextZM_TSQL
- AsTextZM
- AsTextZM (geometry Data Type)
- AsTextZM_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM (geometry Data Type)
ms.assetid: 08ac8aa0-aff7-4b22-87e0-1a1d55dcbc04
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7754190fe629412ddc08e7087626b05ff2c093d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85700827"
---
# <a name="astextzm-geometry-data-type"></a>AsTextZM (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt die OGC-WKB-Darstellung (Open Geospatial Consortium, Well-Known Binary) einer geometry-Instanz zurück, die um alle **Z**-Werte (Höhe) und **M**-Werte (Measure) der Instanz erweitert ist.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlChars**  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Point` -Instanz mit dem Wert **Z** (Höhe)- und **M** (Measure) erstellt. `STAsText()` wählt die WKT-Werte (1 2) aus; `AsTextZM()` wählt identische WKT-Werte aus und gibt die Werte für **Z** und **M** zurück; dies ergibt (1 2 3 4).  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [M &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [Z &#40;geometry Data Type&#41; (Z (geometry-Datentyp))](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  

