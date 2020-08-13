---
title: Metadaten für Parameter und Rowsets (OLE DB-Treiber)
description: Metadaten für Parameter und Rowsets
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- metadata [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: a3356134c542cf90c194924a8fbfc44b357c7123
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244903"
---
# <a name="metadata---parameter-and-rowset"></a>Metadaten – Parameter und Rowsets
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dieser Artikel enthält Informationen über den folgenden Typ und die folgenden Typelemente in Verbindung mit den OLE DB-Datums- und Uhrzeitverbesserungen.  
  
-   DBBINDING-Struktur  
  
-   **ICommandWithParameters::GetParameterInfo**  
  
-   **ICommandWithParameters::SetParameterInfo**  
  
-   **IColumnsRowset::GetColumnsRowset**  
  
-   **IColumnsInfo::GetColumnInfo**  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Die folgenden Informationen werden in der DBPARAMINFO-Struktur durch *prgParamInfo* zurückgegeben:  
  
|Parametertyp|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Löschen|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Set|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Löschen|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Löschen|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Set|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Set|  
  
 Beachten Sie, dass in einigen Fällen Wertbereiche nicht kontinuierlich sind. Der Grund dafür ist das Hinzufügen eines Dezimaltrennzeichens, wenn die Genauigkeit von Bruchteilen größer als 0 (NULL) ist.  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE ist nur gültig, wenn eine Verbindung mit einem [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]-Server (oder höher) besteht. Bei einer Verbindung mit einem Downlevelserver ist DBPARAMFLAGS_SS_ISVARIABLESCALE nie festgelegt.  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>ICommandWithParameters::SetParameterInfo und implizite Parametertypen  
 Die in der DBPARAMBINDINFO-Struktur bereitgestellten Informationen müssen Folgendem entsprechen:  
  
|*pwszDataSourceType*<br /><br /> (anbieterspezifisch)|*pwszDataSourceType*<br /><br /> (OLE DB-generisch)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|Wird ignoriert.|  
|date|DBTYPE_DBDATE|6|Wird ignoriert.|  
||DBTYPE_DBTIME|10|Wird ignoriert.|  
|time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|Wird ignoriert.|  
|datetime||16|Wird ignoriert.|  
|datetime2 oder DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 Der Parameter *bPrecision* wird ignoriert.  
  
 Beim Senden von Daten an den Server wird DBPARAMFLAGS_SS_ISVARIABLESCALE ignoriert. Anwendungen können die Verwendung von älteren TDS-Typen (Tabular Data Stream) durch Verwenden der anbieterspezifischen Typnamen **datetime** und **smalldatetime** erzwingen. Bei einer Verbindung mit [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]-Servern (oder späteren Versionen) wird das Format **datetime2** verwendet, und eine implizite Serverkonvertierung wird durchgeführt, sofern erforderlich, wenn der Typname **datetime2** oder DBTYPE_DBTIMESTAMP lautet. Wenn die anbieterspezifischen Typnamen **datetime** oder **smalldatetime** verwendet werden, wird der Parameter *bScale* ignoriert. Andernfalls müssen Anwendungen sicherstellen, dass *bScale* ordnungsgemäß festgelegt wird. Anwendungen mit Upgrades von MDAC und vom OLE DB-Treiber für [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], die „DBTYPE_DBTIMESTAMP“ verwenden, schlagen fehl, wenn sie *bScale* nicht ordnungsgemäß festlegen. Bei Verbindung mit Serverinstanzen vor [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] tritt für einen anderen *bscale*-Wert als 0 oder 3 mit DBTYPE_DBTIMESTAMP ein Fehler auf und E_FAIL wird zurückgegeben.  
  
 Wenn ICommandWithParameters::SetParameterInfo nicht aufgerufen wird, impliziert der Anbieter den Servertyp über den Bindungstyp gemäß der Angabe in IAccessor::CreateAccessor wie folgt:  
  
|Bindungstyp|*pwszDataSourceType*<br /><br /> (anbieterspezifisch)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|date|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 **IColumnsRowset::GetColumnsRowset** gibt die folgenden Spalten zurück:  
  
|Spaltentyp|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS, DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Löschen|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Set|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Löschen|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Löschen|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Set|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Set|  
  
 In DBCOLUMN_FLAGS hat DBCOLUMNFLAGS_ISFIXEDLENGTH für Datum-/Uhrzeit-Typen stets den Wert TRUE, und die folgenden Flags haben immer den Wert FALSE:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Die übrigen Flags (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE und DBCOLUMNFLAGS_WRITEUNKNOWN) können festgelegt werden. Dies hängt von der Definition der Spalte und von der eigentlichen Abfrage ab.  
  
 Ein DBCOLUMNFLAGS_SS_ISVARIABLESCALE-Flag wird in DBCOLUMN_FLAGS zur Verfügung gestellt, damit eine Anwendung den Servertyp der Spalten bestimmen kann, wobei DBCOLUMN_TYPE DBTYPE_DBTIMESTAMP ist. DBCOLUMN_SCALE oder DBCOLUMN_DATETIMEPRECISION muss auch verwendet werden, um den Servertyp zu identifizieren.  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE ist nur gültig, wenn eine Verbindung mit einem [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]-Server (oder höher) besteht. DBPARAMFLAGS_SS_ISVARIABLESCALE ist nicht definiert, wenn eine Verbindung mit einem Downlevelserver besteht.  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 Die DBCOLUMNINFO-Struktur gibt die folgenden Informationen zurück:  
  
|Parametertyp|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Löschen|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|Set|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Löschen|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Löschen|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Set|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Set|  
  
 In *dwFlags* hat DBCOLUMNFLAGS_ISFIXEDLENGTH für Datum-/Uhrzeit-Typen stets den Wert TRUE, und die folgenden Flags haben immer den Wert FALSE:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 Die übrigen Flags (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE und DBCOLUMNFLAGS_WRITEUNKNOWN) können festgelegt werden.  
  
 In *dwFlags* wird das neue Flag DBCOLUMNFLAGS_SS_ISVARIABLESCALE bereitgestellt, mit dem eine Anwendung den Servertyp von Spalten bestimmen kann, wobei *wType* DBTYPE_DBTIMESTAMP ist. *bScale* muss ebenfalls verwendet werden, um den Servertyp zu identifizieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypunterstützung für OLE DB-Datum- und Uhrzeit-Verbesserungen](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
  
  
