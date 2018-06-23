---
title: Datum und Uhrzeit und Schemarowsets | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], schema rowsets
ms.assetid: 8c35e86f-0597-4ef4-b2b8-f643e53ed4c2
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9faf2104ffb2f49281fe677d8e7ff4f23887338d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160642"
---
# <a name="date-and-time-and-schema-rowsets"></a>Datum und Uhrzeit und Schemarowsets
  Dieses Thema enthält Informationen über das COLUMNS-Rowset und das PROCEDURE_PARAMETERS-Rowset. Diese Informationen beziehen sich auf die OLE DB-Verbesserungen in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] in Bezug auf Datum und Uhrzeit.  
  
## <a name="columns-rowset"></a>COLUMNS-Rowset  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|COLUMN_FLAGS, DBCOLUMFLAGS_SS_ISVARIABLESCALE|DATETIME_PRECISION|  
|-----------------|----------------|------------------------------------------------------|-------------------------|  
|date|DBTYPE_DBDATE|Löschen|0|  
|Uhrzeit|DBTYPE_DBTIME2|Legen Sie|0..7|  
|smalldatetime|DBTYPE_DBTIMESTAMP|Löschen|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|Löschen|3|  
|datetime2|DBTYPE_DBTIMESTAMP|Legen Sie|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|Legen Sie|0..7|  
  
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
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE ist nur gültig, wenn es sich bei einer Verbindung mit einem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Server oder höher. DBCOLUMNFLAGS_SS_ISFIXEDSCALE ist nicht definiert, wenn eine Verbindung mit einem Downlevelserver besteht.  
  
## <a name="procedureparameters-rowset"></a>PROCEDURE_PARAMETERS-Rowset  
 DATA_TYPE enthält die gleichen Werte wie das COLUMNS-Schemarowset, und TYPE_NAME enthält den Servertyp.  
  
 Die neue Spalte SS_DATETIME_PRECISION wurde hinzugefügt, um die Genauigkeit des Typs wie in der DATETIME_PRECISION-Spalte zurückzugeben, ähnlich wie beim COLUMNS-Rowset.  
  
## <a name="providertypes-rowset"></a>PROVIDER_TYPES-Rowset  
 Die folgenden Zeilen werden für date/time-Typen zurückgegeben:  
  
|Typ -><br /><br /> Spalte|date|Uhrzeit|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|Uhrzeit|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_DBDATE|DBTYPE_DBTIME2|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMPOFFSET|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|‘|‘|‘|‘|‘|‘|  
|LITERAL_SUFFIX|‘|‘|‘|‘|‘|‘|  
|CREATE_PARAMS|NULL|scale|NULL|NULL|scale|scale|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|date|Uhrzeit|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|0|NULL|NULL|0|0|  
|MAXIMUM_SCALE|NULL|7|NULL|NULL|7|7|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE, außer wenn eine der folgenden Aussagen zutrifft:<br /><br /> -Client mit einem downlevelserver verbunden ist.<br />-Kompatibilität Verbindung Datentypeigenschaft der gibt eines Kompatibilitätsgrad, der 80 entspricht.|VARIANT_TRUE, außer wenn eine der folgenden Aussagen zutrifft:<br /><br /> -Client mit einem downlevelserver verbunden ist.<br />-Kompatibilität Verbindung Datentypeigenschaft der gibt eines Kompatibilitätsgrad, der 80 entspricht.|VARIANT_TRUE|  
|IS_FIXEDLENGTH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
  
 OLE DB definiert lediglich MINIMUM_SCALE und MAXIMUM_SCALE für numerische und Dezimaltypen, weshalb die Verwendung dieser Spalten für time, datetime2 und datetimeoffset durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client nicht standardmäßig ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Metadaten &#40;OLE DB&#41;](../../database-engine/dev-guide/metadata-ole-db.md)  
  
  