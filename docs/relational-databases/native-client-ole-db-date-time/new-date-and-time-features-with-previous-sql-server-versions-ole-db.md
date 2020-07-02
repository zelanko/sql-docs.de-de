---
title: Datums-und Uhrzeit OLE DB Funktionen mit früheren SQL Server Versionen
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
ms.openlocfilehash: 08a88db90322a3618cc53e60113f5d17ce749ec9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773415"
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>Neue Funktionen für Datum und Uhrzeit bei früheren SQL Server-Versionen (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  In diesem Thema wird das erwartete Verhalten beschrieben, wenn eine Client Anwendung, die verbesserte Datums-und Uhrzeit Funktionen verwendet, mit einer früheren Version von kommuniziert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und wenn ein Client, der mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client als kompiliert wurde, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Befehle an einen Server sendet, der erweiterte Funktionen für Datum und Uhrzeit unterstützt.  
  
## <a name="down-level-client-behavior"></a>Downlevelclient-Verhalten  
 Bei Client Anwendungen, die eine frühere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client als verwenden, werden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] die neuen Datums-/Uhrzeittypen als **nvarchar** -Spalten angezeigt. Die Spalten enthalten literale Darstellungen. Weitere Informationen finden Sie im Abschnitt "Datenformate: Zeichen folgen und Literale" unter [Datentyp Unterstützung für OLE DB Datums-und Uhrzeit Verbesserungen](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md). Die Spaltengröße ist die maximale Literallänge für die Genauigkeit, die für die Spalte festgelegt wurde.  
  
 Katalog-APIs geben Metadaten zurück, die mit dem an den Client zurückgegebenen Datentyp Code auf der gleichen Ebene (z. b. **nvarchar**) und der zugeordneten Darstellung der untergeordneten Ebene (z. b. das entsprechende Literalformat) übereinstimmen. Der zurückgegebene Datentypname ist jedoch der echte [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Typname.  
  
 Wenn eine Client Anwendung auf einer höheren Ebene für einen- [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Server (oder höher) ausgeführt wird, auf dem Schema Änderungen an Datums-/Uhrzeittypen vorgenommen wurden, sieht das erwartete Verhalten wie folgt aus:  
  
|OLE DB-Clienttyp|SQL Server 2005-Typ|SQL Server 2008 (oder höher)-Typ|Ergebniskonvertierung (Server zu Client)|Parameterkonvertierung (Client zu Server)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|Datetime|Date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Zeitfelder werden auf 0 (Null) festgelegt.|IRowsetChange schlägt fehl, weil die Zeichenfolge abgeschnitten wird, wenn das Zeitfeld ungleich 0 (null) ist.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Datumsfelder werden auf das aktuelle Datum festgelegt.|IRowsetChange schlägt fehl, weil die Zeichenfolge abgeschnitten wird, wenn Sekundenbruchteile ungleich 0 (null) sind.<br /><br /> Das Datum wird ignoriert.|  
|DBTYPE_DBTIME||Time(7)|Schlägt fehl-ungültiges Zeit Literale.|OK|  
|DBTYPE_DBTIMESTAMP|||Schlägt fehl-ungültiges Zeit Literale.|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2 (3)|OK|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2 (7)|OK|OK|  
|DBTYPE_DBDATE|Smalldatetime|Date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Zeitfelder werden auf 0 (Null) festgelegt.|IRowsetChange schlägt fehl, weil die Zeichenfolge abgeschnitten wird, wenn das Zeitfeld ungleich 0 (null) ist.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Datumsfelder werden auf das aktuelle Datum festgelegt.|IRowsetChange schlägt fehl, weil die Zeichenfolge abgeschnitten wird, wenn Sekundenbruchteile ungleich 0 (null) sind.<br /><br /> Das Datum wird ignoriert.|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|OK|OK|  
  
 'OK' bedeutet, dass sich die Funktionsweise von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) nicht unterscheidet.  
  
 Nur die folgenden allgemeinen Schemaänderungen wurden berücksichtigt:  
  
-   Verwenden eines neuen Typs, wenn eine Anwendung logisch nur einen Datums- oder Zeitwert erfordert. Die Anwendung wurde jedoch gezwungen, **DateTime** oder **smalldatetime** zu verwenden, da separate Datums-und Uhrzeittypen nicht verfügbar waren.  
  
-   Verwenden eines neuen Typs, um zusätzliche Genauigkeit in Sekundenbruchteilen zu erzielen.  
  
-   Wechseln zu **datetime2** , da dies der bevorzugte Datentyp für Datum und Uhrzeit ist.  
  
 Anwendungen, die Server Metadaten verwenden, die über ICommandWithParameters:: GetParameterInfo oder Schemarowsets abgerufen werden, um Parametertyp Informationen über ICommandWithParameters:: SetParameterInfo festzulegen, schlagen bei Client Konvertierungen fehl, wenn die Zeichen folgen Darstellung eines Quell Typs größer als die Zeichen folgen Darstellung des Zieltyps ist. Wenn eine Client Bindung z. b. DBTYPE_DBTIMESTAMP verwendet und die Server Spalte Date lautet, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konvertiert Native Client den Wert in "yyyy-dd-mm hh: mm: SS. fff", aber Server Metadaten werden als **nvarchar (10)** zurückgegeben. Der resultierende Überlauf löst DBSTATUS_E_CATCONVERTVALUE aus. Ähnliche Probleme treten bei Datenkonvertierungen durch IRowsetChange auf, da die Rowsetmetadaten aus den Resultset-Metadaten festgelegt werden.  
  
### <a name="parameter-and-rowset-metadata"></a>Metadaten für Parameter und Rowsets  
 In diesem Abschnitt werden Metadaten für Parameter, Ergebnis Spalten und Schemarowsets für Clients beschrieben, die mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client als kompiliert werden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Die DBPARAMINFO-Struktur gibt die folgenden Informationen über den *prgParamInfo* -Parameter zurück:  
  
|Parametertyp|wType|ulParamSize|bPrecision|bscale|  
|--------------------|-----------|-----------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|~0|~0|  
  
 Beachten Sie, dass einige dieser Wertbereiche nicht fortlaufend sind; z. B. fehlt 9 in 8,10..16. Der Grund dafür ist das Hinzufügen eines Dezimaltrennzeichens, wenn die Genauigkeit von Bruchteilen größer als 0 (NULL) ist.  
  
#### <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Folgende Spalten werden zurückgegeben:  
  
|Spaltentyp|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|  
|-----------------|--------------------|--------------------------|-------------------------|--------------------------------------------------|  
|date|DBTYPE_WSTR|10|NULL|NULL|  
|time|DBTYPE_WSTR|8, 10..16|NULL|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 Die DBCOLUMNINFO-Struktur gibt die folgenden Informationen zurück:  
  
|Parametertyp|wType|ulColumnSize|bPrecision|bscale|  
|--------------------|-----------|------------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|~0|~0|  
  
### <a name="schema-rowsets"></a>Schemarowsets  
 In diesem Abschnitt werden Metadaten für Parameter, Ergebnisspalten und Schemarowsets für neue Datentypen beschrieben. Diese Informationen sind hilfreich, wenn Sie über einen Client Anbieter verfügen, der mit Tools vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client entwickelt wurde.  
  
#### <a name="columns-rowset"></a>COLUMNS-Rowset  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|date|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8, 10..16|16, 20.. 32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|datetime|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|38, 42.. 54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|52, 56.. 68|NULL|  
  
#### <a name="procedure_parameters-rowset"></a>PROCEDURE_PARAMETERS-Rowset  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|date|DBTYPE_WSTR|10|20|date|  
|time|DBTYPE_WSTR|8, 10..16|16, 20.. 32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|datetime|DBTYPE_DBTIMESTAMP|NULL|NULL|datetime|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|38, 42.. 54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|52, 56.. 68|datetimeoffset|  
  
#### <a name="provider_types-rowset"></a>PROVIDER_TYPES-Rowset  
 Die folgenden Zeilen werden für date/time-Typen zurückgegeben:  
  
|Eingeben von „->“<br /><br /> Spalte|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
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
 Wenn eine Verbindung mit einem Server einer früheren Version als hergestellt wird [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , führen alle Versuche, die neuen servertypnamen zu verwenden (z. b. mit ICommandWithParameters:: SetParameterInfo oder ITableDefinition:: aufatetable), zu DB_E_BADTYPENAME.  
  
 Wenn neue Typen für Parameter oder Ergebnisse ohne Verwendung eines Typnamens gebunden werden, und entweder der neue Typ verwendet wird, um den Servertyp implizit festzulegen, oder keine gültige Konvertierung vom Servertyp zum Clienttyp vorhanden ist, wird DB_E_ERRORSOCCURRED zurückgegeben, und DBBINDSTATUS_UNSUPPORTED_CONVERSION wird als Bindungsstatus für den bei der Ausführung verwendeten Accessor festgelegt.  
  
 Alle Clientpuffertypen können verwendet werden, wenn eine Clientkonvertierung vom Puffertyp zum Servertyp für die Serverversion dieser Verbindung unterstützt wird. In diesem Kontext bezeichnet der *Servertyp* den von ICommandWithParameters:: SetParameterInfo angegebenen Typ oder impliziert durch den Puffertyp, wenn ICommandWithParameters:: SetParameterInfo nicht aufgerufen wurde. Das bedeutet, dass DBTYPE_DBTIME2 und DBTYPE_DBTIMESTAMPOFFSET mit Servern früherer Versionen verwendet werden können, wenn DataTypeCompatibility auf 80 festgelegt und die Clientkonvertierung zu einem unterstützten Servertyp erfolgreich ist. Wenn der Servertyp inkorrekt ist, gibt der Server einen Fehler zurück, wenn er eine implizite Konvertierung in den tatsächlichen Servertyp nicht durchführen kann.  
  
## <a name="ssprop_init_datatypecompatibility-behavior"></a>SSPROP_INIT_DATATYPECOMPATIBILITY-Verhalten  
 Wenn SSPROP_INIT_DATATYPECOMPATIBILITY auf SSPROPVAL_DATATYPECOMPATIBILITY_SQL2000 festgelegt ist, werden die neuen Datums-/Uhrzeittypen und zugeordneten Metadaten den Clients so angezeigt, wie Sie für Downlevelclients angezeigt werden, wie unter [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeit Typen &#40;OLE DB und ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)beschrieben.  
  
## <a name="comparability-for-irowsetfind"></a>Vergleichbarkeit für 'IRowsetFind'  
 Alle Vergleichsoperatoren sind für die neuen Datums-/Uhrzeittypen zulässig, da Sie als Zeichenfolgetypen anstatt als Datums-/Uhrzeittypen angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
