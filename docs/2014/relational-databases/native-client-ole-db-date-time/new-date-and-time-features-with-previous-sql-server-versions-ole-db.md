---
title: Neue Uhrzeitfunktionen zu Datum und mit früheren SQL Server-Versionen (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], enhanced behavior with earlier SQL Server versions
ms.assetid: 96976bac-018c-47cc-b1b2-fa9605eb55e5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc810ced25733ce77d80c7bec38b03e3aaf3753a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233078"
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>Neue Funktionen für Datum und Uhrzeit bei früheren SQL Server-Versionen (OLE DB)
  Dieses Thema beschreibt das erwartete Verhalten, bei der Kommunikation einer Clientanwendung, die verbesserte Datums- und Uhrzeitfunktionen verwendet eine Version von zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], und wenn ein Client mit einer Version kompiliert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client älter als [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sendet Befehle an einen Server, der verbesserte Datums- und Uhrzeitfunktionen unterstützt.  
  
## <a name="down-level-client-behavior"></a>Downlevelclient-Verhalten  
 Clientanwendungen, die eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Version vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] verwenden, betrachten die neuen Datum-/Uhrzeittypen als `nvarchar`-Spalten. Die Spalten enthalten literale Darstellungen. Weitere Informationen finden Sie unter der "Datenformate: Zeichenfolgen und Literale"unter [Datentypunterstützung für OLE DB-Datum und Uhrzeit-Verbesserungen](data-type-support-for-ole-db-date-and-time-improvements.md). Die Spaltengröße ist die maximale Literallänge für die Genauigkeit, die für die Spalte festgelegt wurde.  
  
 Katalog-APIs geben Metadaten zurück, die mit dem an den Client zurückgegebenen Datentypcode früherer Versionen (z. B. `nvarchar`) und der zugeordneten Darstellung früherer Versionen (z.  B. das entsprechende Literalformat) übereinstimmt. Der zurückgegebene Datentypname ist jedoch der echte [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Typname.  
  
 Wenn eine kompatibler Client-Anwendung ausgeführt wird, für eine [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) Server, an dem schemaänderungen an Datums-/Uhrzeittypen vorgenommen wurden, das erwartete Verhalten ist wie folgt:  
  
|OLE DB-Clienttyp|SQL Server 2005-Typ|SQL Server 2008 (oder höher)-Typ|Ergebniskonvertierung (Server zu Client)|Parameterkonvertierung (Client zu Server)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|DATETIME|date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Zeitfelder werden auf 0 (Null) festgelegt.|IRowsetChange schlägt auch fehl, weil die Zeichenfolge abgeschnitten, wenn das Zeitfeld ungleich NULL ist.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Datumsfelder werden auf das aktuelle Datum festgelegt.|IRowsetChange schlägt auch fehl, weil die Zeichenfolge abgeschnitten, wenn Sekundenbruchteile ungleich NULL sind.<br /><br /> Datum wird ignoriert.|  
|DBTYPE_DBTIME||Time(7)|Ein Fehler auftritt – Ungültiges Zeitliteral.|OK|  
|DBTYPE_DBTIMESTAMP|||Ein Fehler auftritt – Ungültiges Zeitliteral.|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2(3)|OK|OK|  
|DBTYPE_DBTIMESTAMP||datetime2(7)|OK|OK|  
|DBTYPE_DBDATE|Smalldatetime|date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Zeitfelder werden auf 0 (Null) festgelegt.|IRowsetChange schlägt auch fehl, weil die Zeichenfolge abgeschnitten, wenn das Zeitfeld ungleich NULL ist.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Datumsfelder werden auf das aktuelle Datum festgelegt.|IRowsetChange schlägt auch fehl, weil die Zeichenfolge abgeschnitten, wenn Sekundenbruchteile ungleich NULL sind.<br /><br /> Datum wird ignoriert.|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|OK|OK|  
  
 'OK' bedeutet, dass sich die Funktionsweise von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) nicht unterscheidet.  
  
 Nur die folgenden allgemeinen Schemaänderungen wurden berücksichtigt:  
  
-   Verwenden eines neuen Typs, wenn eine Anwendung logisch nur einen Datums- oder Zeitwert erfordert. Die Anwendung musste jedoch `datetime` oder `smalldatetime` verwenden, da separate Datums- und Zeittypen nicht zur Verfügung standen.  
  
-   Verwenden eines neuen Typs, um zusätzliche Genauigkeit in Sekundenbruchteilen zu erzielen.  
  
-   Wechseln zu `datetime2`, da dies der bevorzugte Datentyp für Datum und Uhrzeit ist.  
  
 Anwendungen, die über ICommandWithParameters:: GetParameterInfo oder Schema Rowsets erhaltenen Metadaten zu verwenden, um Informationen zum Parametertyp über ICommandWithParameters:: SetParameterInfo festzulegen werden schlagen bei clientkonvertierungen fehl, in dem die Zeichenfolge Darstellung der Quelltyp ist größer als die Zeichenfolgendarstellung des Zieltyps. Wenn eine Clientbindung DBTYPE_DBTIMESTAMP verwendet und die Serverspalte Date, beispielsweise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client wandelt den Wert in "Yyyy-Dd-mm-ss.fff", aber die Metadaten werden als zurückgegeben `nvarchar(10)`. Der resultierende Überlauf löst DBSTATUS_E_CATCONVERTVALUE aus. Ähnliche Probleme treten bei datenkonvertierungen durch IRowsetChange, da die rowsetmetadaten von den resultsetmetadaten festgelegt ist.  
  
### <a name="parameter-and-rowset-metadata"></a>Metadaten für Parameter und Rowsets  
 Dieser Abschnitt beschreibt die Metadaten für Parameter, Ergebnisspalten und Schemarowsets für Clients, die mit einer Version kompiliert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Die DBPARAMINFO-Struktur gibt die folgende Informationen über die *PrgParamInfo* Parameter:  
  
|Parametertyp|wType|ulParamSize|bPrecision|bscale|  
|--------------------|-----------|-----------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
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
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 Die DBCOLUMNINFO-Struktur gibt Folgendes zurück:  
  
|Parametertyp|wType|ulColumnSize|bPrecision|bscale|  
|--------------------|-----------|------------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
### <a name="schema-rowsets"></a>Schemarowsets  
 In diesem Abschnitt werden Metadaten für Parameter, Ergebnisspalten und Schemarowsets für neue Datentypen beschrieben. Diese Informationen sind hilfreich ist, Sie verfügen über einen Clientanbieter entwickelt wurde, mithilfe von Tools vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
#### <a name="columns-rowset"></a>COLUMNS-Rowset  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|date|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|NULL|  
  
#### <a name="procedureparameters-rowset"></a>PROCEDURE_PARAMETERS-Rowset  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|date|DBTYPE_WSTR|10|20|date|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|DATETIME|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|datetimeoffset|  
  
#### <a name="providertypes-rowset"></a>PROVIDER_TYPES-Rowset  
 Die folgenden Zeilen werden für date/time-Typen zurückgegeben:  
  
|Typ -><br /><br /> Spalte|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
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
|LOCAL_TYPE_NAME|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_TRUE|VARIANT_FALSE|VARIANT_FALSE|  
|IS_FIXEDLENGTH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
  
## <a name="down-level-server-behavior"></a>Downlevelserver-Verhalten  
 Beim Verbinden mit einem Server, der eine früheren Version als [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], jeder Versuch, verwenden Sie die neuen servertypnamen (z. B. mit ICommandWithParameters:: SetParameterInfo oder itabledefinition:: CreateTable) führt db_e_badtypename.  
  
 Wenn neue Typen für Parameter oder Ergebnisse ohne Verwendung eines Typnamens gebunden werden, und entweder der neue Typ verwendet wird, um den Servertyp implizit festzulegen, oder keine gültige Konvertierung vom Servertyp zum Clienttyp vorhanden ist, wird DB_E_ERRORSOCCURRED zurückgegeben, und DBBINDSTATUS_UNSUPPORTED_CONVERSION wird als Bindungsstatus für den bei der Ausführung verwendeten Accessor festgelegt.  
  
 Alle Clientpuffertypen können verwendet werden, wenn eine Clientkonvertierung vom Puffertyp zum Servertyp für die Serverversion dieser Verbindung unterstützt wird. In diesem Kontext *Servertyp* bedeutet, dass den Typ von ICommandWithParameters:: SetParameterInfo angegeben oder von dem Puffertyp impliziert wird, wenn ICommandWithParameters:: SetParameterInfo nicht aufgerufen wurde. Das bedeutet, dass DBTYPE_DBTIME2 und DBTYPE_DBTIMESTAMPOFFSET mit Servern früherer Versionen verwendet werden können, wenn DataTypeCompatibility auf 80 festgelegt und die Clientkonvertierung zu einem unterstützten Servertyp erfolgreich ist. Wenn der Servertyp inkorrekt ist, gibt der Server einen Fehler zurück, wenn er eine implizite Konvertierung in den tatsächlichen Servertyp nicht durchführen kann.  
  
## <a name="sspropinitdatatypecompatibility-behavior"></a>SSPROP_INIT_DATATYPECOMPATIBILITY-Verhalten  
 Wenn SSPROP_INIT_DATATYPECOMPATIBILITY auf SSPROPVAL_DATATYPECOMPATIBILITY_SQL2000 festgelegt ist, die neuen Datums-/Uhrzeittypen und die zugeordneten Metadaten angezeigt werden für Clients wie für Downlevelclients, siehe [Massenkopieränderungen für Verbesserte Datums- und Uhrzeittypen &#40;OLE DB- und ODBC-&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
## <a name="comparability-for-irowsetfind"></a>Vergleichbarkeit für 'IRowsetFind'  
 Alle Vergleichsoperatoren sind für die neuen Datums-/Uhrzeittypen zulässig, da Sie als Zeichenfolgetypen anstatt als Datums-/Uhrzeittypen angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](date-and-time-improvements-ole-db.md)  
  
  
