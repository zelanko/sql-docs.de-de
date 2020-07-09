---
title: AsTextZM (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsTextZM (geography Data Type)
- AsTextZM_TSQL
- AsTextZM
- AsTextZM_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM method
ms.assetid: e9dc27f6-e945-4457-8498-7644db34008e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fe68a2179659a3e5d9cd941d613deb954dbf4726
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731225"
---
# <a name="astextzm-geography-data-type"></a>AsTextZM (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung einer **geography** -Instanz zurück, die um alle von der Instanz getragenen **Z** (Höhe)- und **M** (Measure)-Werte erweitert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlChars**  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Point` -Instanz mit dem Wert **Z** (Höhe)- und **M** (Measure) erstellt. `STAsText()` wählt die WKT-Werte (-122.34900 47.65100) aus; `AsTextZM()` wählt identische WKT-Werte aus und gibt die Werte für **Z** und **M** zurück; dies ergibt (-122.34900 47.65100 10.3 12).  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [Z &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
