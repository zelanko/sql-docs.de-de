---
title: ToString (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ToString (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString method
ms.assetid: 045c12fa-8fc6-441a-9500-7021cb4ff13e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fcd5618e6bfa434a3f31ab4817f53114e122846d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85701513"
---
# <a name="tostring-geography-data-type"></a>ToString (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung einer **geography** -Instanz zurück, die um alle von der Instanz getragenen Z- (Höhe) und M-Werte (Measure) erweitert wurde.  
  
 Diese geography-Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlString**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt die Zeichenfolge "NULL" zurück, wenn sie für NULL-Instanzen aufgerufen wird. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wurden die Ergebnisse, die auf dem Server zurückgegeben werden können, um **FullGlobe**-Instanzen erweitert. Diese Methode gibt den gleichen Wert wie `AsTextZM()`zurück.  
  
 Diese Methode ist nicht exakt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -Instanz erstellt und mithilfe von `ToString()` eine Textbeschreibung der Instanz zurückgegeben.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [AsTextZM &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
