---
title: Datums-, Uhrzeit- und Schemarowsets | Microsoft-Dokumentation
description: Datums-, Uhrzeit- und Schemarowsets
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], schema rowsets
author: pmasl
ms.author: pelopes
ms.openlocfilehash: f9d852689f008fcaaff53a3325a298a66be5f4e9
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004467"
---
# <a name="metadata---date-and-time-and-schema-rowsets"></a>Metadaten – Datums- und Uhrzeit- sowie Schemarowsets
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dieses Thema enthält Informationen über das COLUMNS-Rowset und das PROCEDURE_PARAMETERS-Rowset. Diese Informationen beziehen sich auf die OLE DB-Verbesserungen in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] in Bezug auf Datum und Uhrzeit.  
  
## <a name="columns-rowset"></a>COLUMNS-Rowset  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|COLUMN_FLAGS, DBCOLUMFLAGS_SS_ISVARIABLESCALE|DATETIME_PRECISION|  
|-----------------|----------------|------------------------------------------------------|-------------------------|  
|date|DBTYPE_DBDATE|Löschen|0|  
|time|DBTYPE_DBTIME2|Set|0..7|  
|smalldatetime|DBTYPE_DBTIMESTAMP|Löschen|0|  
|datetime|DBTYPE_DBTIMESTAMP|Löschen|3|  
|datetime2|DBTYPE_DBTIMESTAMP|Set|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|Set|0..7|  
  
 In COLUMN_FLAGS hat DBCOLUMNFLAGS_ISFIXEDLENGTH für Datum-/Uhrzeittypen stets den Wert TRUE, und die folgenden Flags haben immer den Wert FALSE:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Die übrigen Flags (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE und DBCOLUMNFLAGS_WRITEUNKNOWN) können festgelegt werden. Dies hängt von der Definition der Spalte ab.  
  
 Das neue DBCOLUMNFLAGS_SS_ISVARIABLESCALE-Flag wird in COLUMN_FLAGS bereitgestellt, damit eine Anwendung den Servertyp der Spalten bestimmen kann, wobei DATA_TYPE = DBTYPE_DBTIMESTAMP ist. DATETIME_PRECISION muss ebenfalls verwendet werden, um den Servertyp zu identifizieren.  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE ist nur gültig, wenn eine Verbindung mit einem Server von [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (oder höher) besteht. DBCOLUMNFLAGS_SS_ISFIXEDSCALE ist nicht definiert, wenn eine Verbindung mit einem Downlevelserver besteht.  
  
## <a name="procedure_parameters-rowset"></a>PROCEDURE_PARAMETERS-Rowset  
 DATA_TYPE enthält die gleichen Werte wie das COLUMNS-Schemarowset, und TYPE_NAME enthält den Servertyp.  
  
 Die neue Spalte SS_DATETIME_PRECISION wurde hinzugefügt, um die Genauigkeit des Typs wie in der DATETIME_PRECISION-Spalte zurückzugeben, ähnlich wie beim COLUMNS-Rowset.  
  
## <a name="provider_types-rowset"></a>PROVIDER_TYPES-Rowset  
 Die folgenden Zeilen werden für date/time-Typen zurückgegeben:  
  
|Eingeben von „->“<br /><br /> Column|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_DBDATE|DBTYPE_DBTIME2|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMPOFFSET|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|Skalierung|NULL|NULL|Skalierung|Skalierung|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|0|NULL|NULL|0|0|  
|MAXIMUM_SCALE|NULL|7|NULL|NULL|7|7|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE, außer wenn eine der folgenden Aussagen zutrifft:<br /><br /> Der Client ist mit einem Downlevelserver verbunden.<br /><br /> Die Verbindungseigenschaft für die Datentypkompatibilität gibt einen Kompatibilitätsgrad von 80 an.|VARIANT_TRUE, außer wenn eine der folgenden Aussagen zutrifft:<br /><br /> Der Client ist mit einem Downlevelserver verbunden.<br /><br /> Die Verbindungseigenschaft für die Datentypkompatibilität gibt einen Kompatibilitätsgrad von 80 an.|VARIANT_TRUE|  
|IS_FIXEDLENGTH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
  
 OLE DB definiert lediglich MINIMUM_SCALE und MAXIMUM_SCALE für numerische und Dezimaltypen, weshalb die Verwendung dieser Spalten für „time“, „datetime2“ und „datetimeoffset“ durch den OLE DB-Treiber für SQL Server nicht dem Standardverhalten entspricht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Metadata &#40;OLE DB&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
  
  
