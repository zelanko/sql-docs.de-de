---
title: Datum und Uhrzeit OLE DB-Features mit früheren SQL Server-Versionen
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 96976bac-018c-47cc-b1b2-fa9605eb55e5
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a90863fb061912dd0a6c44fe23ba2baa402662c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301017"
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>Neue Funktionen für Datum und Uhrzeit bei früheren SQL Server-Versionen (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema wird das erwartete Verhalten beschrieben, wenn eine Clientanwendung, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]erweiterte Datums- und Uhrzeitfeatures verwendet, mit einer Version von früher als kommuniziert und wenn ein Client, der mit einer Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client früher kompiliert wurde, Befehle an einen Server [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sendet, der erweiterte Datums- und Uhrzeitfeatures unterstützt.  
  
## <a name="down-level-client-behavior"></a>Downlevelclient-Verhalten  
 Clientanwendungen, die eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Native Client verwenden, sehen die neuen Datums-/Uhrzeittypen als **nvarchar-Spalten.** Die Spalten enthalten literale Darstellungen. Weitere Informationen finden Sie im Abschnitt "Datenformate: Zeichenfolgen und Literale" im Abschnitt [Datentypunterstützung für OLE DB Datums- und Zeitverbesserungen](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md). Die Spaltengröße ist die maximale Literallänge für die Genauigkeit, die für die Spalte festgelegt wurde.  
  
 Katalog-APIs geben Metadaten zurück, die mit dem an den Client zurückgegebenen Datentypcode auf der Ebene (z. B. **nvarchar)** und der zugehörigen Darstellung auf der Ebene (z. B. das entsprechende Literalformat) übereinstimmen. Der zurückgegebene Datentypname ist jedoch der echte [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Typname.  
  
 Wenn eine Clientanwendung auf der [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Ebene auf einem (oder neueren) Server ausgeführt wird, auf dem Schemaänderungen an Datums-/Uhrzeittypen vorgenommen wurden, wird folgendes erwartet:  
  
|OLE DB-Clienttyp|SQL Server 2005-Typ|SQL Server 2008 (oder höher)|Ergebniskonvertierung (Server zu Client)|Parameterkonvertierung (Client zu Server)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|Datetime|Date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Zeitfelder werden auf 0 (Null) festgelegt.|IRowsetChange schlägt aufgrund der Zeichenfolgenkürzung fehl, wenn das Zeitfeld ungleich Null ist.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Datumsfelder werden auf das aktuelle Datum festgelegt.|IRowsetChange schlägt aufgrund der Zeichenfolgenkürzung fehl, wenn Die Sekundenbruchteile ungleich Null sind.<br /><br /> Datum wird ignoriert.|  
|DBTYPE_DBTIME||Time(7)|Fails - ungültiges Zeitliteral.|OK|  
|DBTYPE_DBTIMESTAMP|||Fails - ungültiges Zeitliteral.|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2(3)|OK|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2(7)|OK|OK|  
|DBTYPE_DBDATE|Smalldatetime|Date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Zeitfelder werden auf 0 (Null) festgelegt.|IRowsetChange schlägt aufgrund der Zeichenfolgenkürzung fehl, wenn das Zeitfeld ungleich Null ist.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Datumsfelder werden auf das aktuelle Datum festgelegt.|IRowsetChange schlägt aufgrund der Zeichenfolgenkürzung fehl, wenn Die Sekundenbruchteile ungleich Null sind.<br /><br /> Datum wird ignoriert.|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|OK|OK|  
  
 'OK' bedeutet, dass sich die Funktionsweise von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) nicht unterscheidet.  
  
 Nur die folgenden allgemeinen Schemaänderungen wurden berücksichtigt:  
  
-   Verwenden eines neuen Typs, wenn eine Anwendung logisch nur einen Datums- oder Zeitwert erfordert. Die Anwendung war jedoch gezwungen, **datetime** oder **smalldatetime** zu verwenden, da keine separaten Datums- und Uhrzeittypen verfügbar waren.  
  
-   Verwenden eines neuen Typs, um zusätzliche Genauigkeit in Sekundenbruchteilen zu erzielen.  
  
-   Wechseln zu **datetime2,** da dies der bevorzugte Datentyp für Datum und Uhrzeit ist.  
  
 Anwendungen, die Servermetadaten verwenden, die über ICommandWithParameters::GetParameterInfo oder Schemarowsets zum Festlegen von Parametertypinformationen über ICommandWithParameters::SetParameterInfo abgerufen werden, schlagen bei Clientkonvertierungen fehl, bei denen die Zeichenfolgendarstellung eines Quelltyps größer als die Zeichenfolgendarstellung des Zieltyps ist. Wenn z. B. eine Clientbindung DBTYPE_DBTIMESTAMP verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und die Serverspalte Datum ist, konvertiert Native Client den Wert in "yyyy-dd-mm hh:mm:ss.fff", aber Servermetadaten werden als **nvarchar(10)** zurückgegeben. Der resultierende Überlauf löst DBSTATUS_E_CATCONVERTVALUE aus. Ähnliche Probleme treten bei Datenkonvertierungen durch IRowsetChange auf, da die Rowset-Metadaten aus den Resultset-Metadaten festgelegt werden.  
  
### <a name="parameter-and-rowset-metadata"></a>Metadaten für Parameter und Rowsets  
 In diesem Abschnitt werden Metadaten für Parameter, Ergebnisspalten und Schemarowsets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für Clients [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]beschrieben, die mit einer Version von Native Client vor kompiliert wurden.  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Die DBPARAMINFO-Struktur gibt die folgenden Informationen über den Parameter *prgParamInfo* zurück:  
  
|Parametertyp|wType|ulParamSize|bPrecision|bscale|  
|--------------------|-----------|-----------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
 Beachten Sie, dass einige dieser Wertbereiche nicht fortlaufend sind; z. B. fehlt 9 in 8,10..16. Der Grund dafür ist das Hinzufügen eines Dezimaltrennzeichens, wenn die Genauigkeit von Bruchteilen größer als 0 (NULL) ist.  
  
#### <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Folgende Spalten werden zurückgegeben:  
  
|Spaltentyp|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|  
|-----------------|--------------------|--------------------------|-------------------------|--------------------------------------------------|  
|date|DBTYPE_WSTR|10|NULL|NULL|  
|time|DBTYPE_WSTR|8, 10..16|NULL|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 Die DBCOLUMNINFO-Struktur gibt die folgenden Informationen zurück:  
  
|Parametertyp|wType|ulColumnSize|bPrecision|bscale|  
|--------------------|-----------|------------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
### <a name="schema-rowsets"></a>Schemarowsets  
 In diesem Abschnitt werden Metadaten für Parameter, Ergebnisspalten und Schemarowsets für neue Datentypen beschrieben. Diese Informationen sind nützlich, da Sie einen [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clientanbieter mit Tools früher als Native Client entwickelt haben.  
  
#### <a name="columns-rowset"></a>COLUMNS-Rowset  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|date|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|datetime|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|NULL|  
  
#### <a name="procedure_parameters-rowset"></a>PROCEDURE_PARAMETERS-Rowset  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|date|DBTYPE_WSTR|10|20|date|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|datetime|DBTYPE_DBTIMESTAMP|NULL|NULL|datetime|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|datetimeoffset|  
  
#### <a name="provider_types-rowset"></a>PROVIDER_TYPES-Rowset  
 Die folgenden Zeilen werden für date/time-Typen zurückgegeben:  
  
|Eingeben von „->“<br /><br /> Column|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_WSTR|DBTYPE_WSTR|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_WSTR|DBTYPE_WSTR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_TRUE|VARIANT_FALSE|VARIANT_FALSE|  
|IS_FIXEDLENGTH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
  
## <a name="down-level-server-behavior"></a>Downlevelserver-Verhalten  
 Wenn eine Verbindung mit einem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]Server einer früheren Version als besteht, führt jeder Versuch, die neuen Servertypnamen zu verwenden (z. B. mit ICommandWithParameters::SetParameterInfo oder ITableDefinition::CreateTable), zu DB_E_BADTYPENAME.  
  
 Wenn neue Typen für Parameter oder Ergebnisse ohne Verwendung eines Typnamens gebunden werden, und entweder der neue Typ verwendet wird, um den Servertyp implizit festzulegen, oder keine gültige Konvertierung vom Servertyp zum Clienttyp vorhanden ist, wird DB_E_ERRORSOCCURRED zurückgegeben, und DBBINDSTATUS_UNSUPPORTED_CONVERSION wird als Bindungsstatus für den bei der Ausführung verwendeten Accessor festgelegt.  
  
 Alle Clientpuffertypen können verwendet werden, wenn eine Clientkonvertierung vom Puffertyp zum Servertyp für die Serverversion dieser Verbindung unterstützt wird. In diesem Zusammenhang bezeichnet *der Servertyp* den von ICommandWithParameters::SetParameterInfo angegebenen Typ oder impliziert durch den Puffertyp, wenn ICommandWithParameters::SetParameterInfo nicht aufgerufen wurde. Das bedeutet, dass DBTYPE_DBTIME2 und DBTYPE_DBTIMESTAMPOFFSET mit Servern früherer Versionen verwendet werden können, wenn DataTypeCompatibility auf 80 festgelegt und die Clientkonvertierung zu einem unterstützten Servertyp erfolgreich ist. Wenn der Servertyp inkorrekt ist, gibt der Server einen Fehler zurück, wenn er eine implizite Konvertierung in den tatsächlichen Servertyp nicht durchführen kann.  
  
## <a name="ssprop_init_datatypecompatibility-behavior"></a>SSPROP_INIT_DATATYPECOMPATIBILITY-Verhalten  
 Wenn SSPROP_INIT_DATATYPECOMPATIBILITY auf SSPROPVAL_DATATYPECOMPATIBILITY_SQL2000 festgelegt ist, werden die neuen Datums-/Uhrzeittypen und zugehörigen Metadaten für Clients so angezeigt, wie unter [Massenkopieränderungen für erweiterte Datums- und Uhrzeittypen &#40;OLE DB und ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)beschrieben.  
  
## <a name="comparability-for-irowsetfind"></a>Vergleichbarkeit für 'IRowsetFind'  
 Alle Vergleichsoperatoren sind für die neuen Datums-/Uhrzeittypen zulässig, da Sie als Zeichenfolgetypen anstatt als Datums-/Uhrzeittypen angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
