---
description: sp_help_spatial_geometry_histogram (Transact-SQL)
title: sp_help_spatial_geometry_histogram (Transact-SQL) | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b74fa91b13b3b7f432a4b647f063a91a76e8c56a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535235"
---
# <a name="sp_help_spatial_geometry_histogram-transact-sql"></a>sp_help_spatial_geometry_histogram (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @tabname = ] 'tabname'` Der qualifizierte oder nicht qualifizierte Name der Tabelle, für die der räumliche Index angegeben wurde.  
  
 Anführungszeichen sind nur dann erforderlich, wenn eine qualifizierte Tabelle angegeben wird. Bei Angabe eines vollqualifizierten Namens, einschließlich eines Datenbanknamens, muss es sich bei dem Datenbanknamen um den Namen der aktuellen Datenbank handeln. *tabname* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @colname = ] 'colname'` Der Name der angegebenen räumlichen Spalte. *ColName* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @resolution = ] 'resolution'` Die Auflösung des umgebenden Felds. Werte zwischen 10 und 5000 sind gültig. *Auflösung* ist vom Datentyp **tinyint**und hat keinen Standardwert.  
  
`[ @xmin = ] 'xmin'` Ist die X-minimale Eigenschaft für das umgebende Feld. *xmin* ist vom Datentyp **float**und hat keinen Standardwert.  
  
`[ @ymin = ] 'ymin'` Die Y-minimale Eigenschaft für das umgebende Feld. *ymin* ist vom Datentyp **float**und hat keinen Standardwert.  
  
`[ @xmax = ] 'xmax'` Ist die X-Maximum-Eigenschaft des Begrenzungs Rahmens. *xmax* ist vom Datentyp **float**und hat keinen Standardwert.  
  
`[ @ymax = ] 'ymax'` Ist die maximale Y-Eigenschaft für das umgebende Feld. *ymax* ist vom Datentyp **float**und hat keinen Standardwert.  
  
`[ @sample = ] 'sample'` Der Prozentsatz der verwendeten Tabelle. Gültige Werte sind 0 bis 100. *Sample* ist ein **float**-Wert. Der Standardwert ist 100.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Tabellenwert wird zurückgegeben. In der folgenden Tabelle wird der Spalteninhalt der Tabelle beschrieben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Stellt die eindeutige ID jeder Zelle dar, beginnend mit 1.|  
|**Kern**|**geometry**|Ist ein rechteckiges Polygon, das die einzelnen Zellen darstellt. Die Zellenform ist mit der für die räumliche Indizierung verwendeten Zellenform identisch.|  
|**row_count**|**bigint**|Gibt die Anzahl räumlicher Objekte an, die die Zelle berühren oder enthalten.|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss ein Mitglied der Datenbankrolle **public** sein. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Auf der räumlichen SSMS-Registerkarte wird eine grafische Darstellung der Ergebnisse angezeigt. Sie können die Ergebnisse für das räumliche Fenster abfragen, um die ungefähre Anzahl von Ergebniselementen abzurufen. Objekte in der Tabelle decken möglicherweise mehrere Zellen ab, daher ist die Summe der Zellen möglicherweise größer als die Anzahl der tatsächlichen Objekte.  
  
 Eine zusätzliche Zeile mit der Anzahl der Objekte, die sich außerhalb des Begrenzungsrahmens befinden oder den Rahmen des Begrenzungsrahmens berühren, kann dem Resultset hinzugefügt werden. Der **CellID** dieser Zeile ist 0, und die **Zelle** dieser Zeile enthält eine **LineString** , die das umgebende Feld darstellt. Diese Zeile stellt den gesamten Bereich außerhalb des Begrenzungsrahmens dar.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Beispiel Tabelle erstellt, und anschließend wird **sp_help_spatial_geometry_histogram** für die-Tabelle aufgerufen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für räumliche Indizes &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
