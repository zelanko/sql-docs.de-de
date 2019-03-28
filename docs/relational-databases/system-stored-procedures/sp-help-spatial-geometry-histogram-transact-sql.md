---
title: Sp_help_spatial_geometry_histogram (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_histogram
- sp_help_spatial_geometry_histogram_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geometry_histogram
ms.assetid: 036aaf61-df3e-40f7-aa4e-62983c5a37bd
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 914c68d313d77d1cb363f44daee2935976161418
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534292"
---
# <a name="sphelpspatialgeometryhistogram-transact-sql"></a>sp_help_spatial_geometry_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Erleichtert es, Begrenzungsrahmen und Rasterparameter für einen räumlichen Index mit Schlüsseln zu versehen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_spatial_geometry_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @xmin = ] 'minx' ]   
     [ , [ @ymin = ] 'miny' ]   
     [ ,.[ @xmax = ] 'maxx' ]  
     [ , [ @ymax = ] 'maxy' ]  
     [ , [ @sample = ] 'sample' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @tabname = ] 'tabname'` Ist der qualifizierte oder nicht qualifizierte Name der Tabelle für die der räumlichkeitsindex angegeben wurde.  
  
 Anführungszeichen sind nur dann erforderlich, wenn eine qualifizierte Tabelle angegeben wird. Bei Angabe eines vollqualifizierten Namens, einschließlich eines Datenbanknamens, muss es sich bei dem Datenbanknamen um den Namen der aktuellen Datenbank handeln. *Tabname* ist **Sysname**, hat keinen Standardwert.  
  
`[ @colname = ] 'colname'` Ist der Name der angegebenen räumlichen Spalte. *Colname* ist eine **Sysname**, hat keinen Standardwert.  
  
`[ @resolution = ] 'resolution'` Ist die Auflösung des Begrenzungsrahmens. Werte zwischen 10 und 5000 sind gültig. *Auflösung* ist eine **Tinyint**, hat keinen Standardwert.  
  
`[ @xmin = ] 'xmin'` Ist die X-Minimum-Eigenschaft des Begrenzungsrahmens an. *"xmin"* ist eine **"float"**, hat keinen Standardwert.  
  
`[ @ymin = ] 'ymin'` Ist die Y-Minimum-Eigenschaft des Begrenzungsrahmens an. *Ymin* ist eine **"float"**, hat keinen Standardwert.  
  
`[ @xmax = ] 'xmax'` Ist die X-Maximum-Eigenschaft des Begrenzungsrahmens an. *"xmax"* ist eine **"float"**, hat keinen Standardwert.  
  
`[ @ymax = ] 'ymax'` Ist die Y-Maximum-Eigenschaft des Begrenzungsrahmens an. *Ymax* ist eine **"float"**, hat keinen Standardwert.  
  
`[ @sample = ] 'sample'` Ist der Prozentsatz der Tabelle, die verwendet wird. Gültige Werte liegen zwischen 0 und 100. *Beispiel* ist eine **"float"**. Standardwert ist 100.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Tabellenwert wird zurückgegeben. In der folgenden Tabelle wird der Spalteninhalt der Tabelle beschrieben.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Stellt die eindeutige ID jeder Zelle dar, beginnend mit 1.|  
|**cell**|**Geometrie**|Ist ein rechteckiges Polygon, das die einzelnen Zellen darstellt. Die Zellenform ist mit der für die räumliche Indizierung verwendeten Zellenform identisch.|  
|**row_count**|**bigint**|Gibt die Anzahl räumlicher Objekte an, die die Zelle berühren oder enthalten.|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss ein Mitglied der Datenbankrolle **public** sein. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Auf der räumlichen SSMS-Registerkarte wird eine grafische Darstellung der Ergebnisse angezeigt. Sie können die Ergebnisse für das räumliche Fenster abfragen, um die ungefähre Anzahl von Ergebniselementen abzurufen. Objekte in der Tabelle decken möglicherweise mehrere Zellen ab, daher ist die Summe der Zellen möglicherweise größer als die Anzahl der tatsächlichen Objekte.  
  
 Eine zusätzliche Zeile mit der Anzahl der Objekte, die sich außerhalb des Begrenzungsrahmens befinden oder den Rahmen des Begrenzungsrahmens berühren, kann dem Resultset hinzugefügt werden. Die **Cellid** dieser Zeile ist 0 und der **Zelle** dieser Zeile enthält einen **LineString** , das das umgebende Feld darstellt. Diese Zeile stellt den gesamten Bereich außerhalb des Begrenzungsrahmens dar.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Beispieltabelle erstellt, und ruft dann **Sp_help_spatial_geometry_histogram** für die Tabelle.  
  
 `USE AdventureWorksDW2012`  
  
 `GO`  
  
 `-- Set database compatibility for circular arc segments`  
  
 `ALTER DATABASE AdventureWorksDW2012`  
  
 `SET COMPATIBILITY_LEVEL = 110;`  
  
 `GO`  
  
 `-- Create table to execute sp_help_spatial_geometry_histogram on`  
  
 `CREATE TABLE TownSites`  
  
 `(`  
  
 `Location geometry NULL,`  
  
 `SiteName nvarchar(50) NULL`  
  
 `)`  
  
 `GO`  
  
 `-- Insert site data into table`  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('POINT(0 0)');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Booth Map';`  
  
 `SET @g = geometry::Parse('POLYGON((1 1, 1 2, 2 2, 2 1, 1 1))');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Town Hall';`  
  
 `SET @g = geometry::Parse('CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-1 0, 0 -1, 1 0),(1 0, 1 2, -1 0)))');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Main Park';`  
  
 `SET @g = geometry::Parse('CIRCULARSTRING(1 5, 2 2, 5 1)');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Main Road';`  
  
 `-- Call proc to see data within bounding box`  
  
 `EXEC sp_help_spatial_geometry_histogram @tabname = TownSites, @colname = Location, @resolution = 64, @xmin = -2, @ymin = -2, @xmax = 3, @ymax = 3, @sample = 100;`  
  
 `GO`  
  
 `DROP TABLE TownSites;`  
  
 `GO`  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Räumlichkeitsindizes &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
