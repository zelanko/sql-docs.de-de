---
title: Verbessertes Verhalten des Datums-und Uhrzeittyps mit früheren SQL Server Versionen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC], enhanced behavior with earlier SQL Server versions
ms.assetid: cd4e137f-dc5e-4df7-bc95-51fe18c587e0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44ac9cecce81f7873ca5ef42ba414bd4528e05b4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63140633"
---
# <a name="enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc"></a>Verbessertes Verhalten des Datums- und Uhrzeittyps bei früheren Versionen von SQL Server (ODBC)
  In diesem Thema wird das erwartete Verhalten beschrieben, wenn eine Clientanwendung, die verbesserte Datums- und Uhrzeitfunktionen verwendet, mit einer Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] kommuniziert und wenn eine Clientanwendung, die Microsoft Data Access Components, Windows Data Access Components oder eine Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] verwendet, Befehle an einen Server sendet, der verbesserte Datums- und Uhrzeitfunktionen unterstützt.  
  
## <a name="down-level-client-behavior"></a>Downlevelclient-Verhalten  
 Clientanwendungen, die mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Version vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] kompiliert wurden, erkennen die neuen Datums-/Uhrzeittypen als nvarchar-Spalten. Der Spalten Inhalt ist die literaldarstellungen, wie im Abschnitt "Datenformate: Zeichen folgen und Literale" der [Datentyp Unterstützung für ODBC-Datums-und Uhrzeit Verbesserungen](data-type-support-for-odbc-date-and-time-improvements.md)beschrieben. Die Spaltengröße ist die maximale literale Länge mit der für die Spalte angegebenen Genauigkeit in Bruchteilen von Sekunden.  
  
 Katalog-APIs geben Metadaten zurück, die mit dem an den Client zurückgegebenen Datentypcode früherer Versionen (z. B. nvarchar) und der zugeordneten Darstellung früherer Versionen (z. B. das entsprechende literale Format) übereinstimmt. Der zurückgegebene Datentypname ist jedoch der echte [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Typname.  
  
 Anweisungs Metadaten, die von SQLDescribeCol, SQLDescribeParam, SQGetDescField und SQLColAttribute zurückgegeben werden, geben Metadaten zurück, die mit dem Typ der untergeordneten Ebene in jeder Hinsicht konsistent sind, einschließlich des Typnamens. `nvarchar` ist ein Beispiel für einen Downleveltyp dieser Art.  
  
 Wenn eine Client Anwendung auf einer höheren Ebene für einen [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] -Server (oder höher) ausgeführt wird, auf dem Schema Änderungen an Datums-/Uhrzeittypen vorgenommen wurden, sieht das erwartete Verhalten wie folgt aus:  
  
|SQL Server 2005-Typ|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher)-Typ|ODBC-Clienttyp|Ergebniskonvertierung (SQL zu C)|Parameterkonvertierung (C zu SQL)|  
|--------------------------|----------------------------------------------|----------------------|------------------------------------|---------------------------------------|  
|Datetime|Datum|SQL_C_TYPE_DATE|OK|OK (1)|  
|||SQL_C_TYPE_TIMESTAMP|Zeitfelder werden auf 0 (Null) festgelegt.|OK (2)<br /><br /> Fehler, wenn das Zeitfeld ungleich 0 (null) ist. Verwendet [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(0)|SQL_C_TYPE_TIME|OK|OK (1)|  
|||SQL_C_TYPE_TIMESTAMP|Datumsfelder werden auf das aktuelle Datum festgelegt.|OK (2)<br /><br /> Datum wird ignoriert. Fehler, wenn Sekundenbruchteile ungleich 0 sind. Verwendet [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(7)|SQL_C_TIME|Schlägt fehl-ungültiges Zeit Literale.|OK (1)|  
|||SQL_C_TYPE_TIMESTAMP|Schlägt fehl-ungültiges Zeit Literale.|OK (1)|  
||Datetime2 (3)|SQL_C_TYPE_TIMESTAMP|OK|OK (1)|  
||Datetime2 (7)|SQL_C_TYPE_TIMESTAMP|OK|Wert wird von Clientkonvertierung auf 1/300stel Sekunde gerundet.|  
|Smalldatetime|Datum|SQL_C_TYPE_DATE|OK|OK|  
|||SQL_C_TYPE_TIMESTAMP|Zeitfelder werden auf 0 (Null) festgelegt.|OK (2)<br /><br /> Fehler, wenn das Zeitfeld ungleich 0 (null) ist. Verwendet [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(0)|SQL_C_TYPE_TIME|OK|OK|  
|||SQL_C_TYPE_TIMESTAMP|Datumsfelder werden auf das aktuelle Datum festgelegt.|OK (2)<br /><br /> Datum wird ignoriert. Fehler, wenn Sekundenbruchteile ungleich 0 (null) sind.<br /><br /> Verwendet [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Datetime2(0)|SQL_C_TYPE_TIMESTAMP|OK|OK|  
  
## <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
|Symbol|Bedeutung|  
|------------|-------------|  
|1|Wenn es mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] funktioniert hat, sollte es auch mit einer neueren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funktionieren.|  
|2|Eine Anwendung, die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] funktiniert hat, kann mit einer neueren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fehlschlagen.|  
  
 Nur allgemeine Schemaänderungen wurden berücksichtigt. Dabei handelt es sich um die folgenden allgemeinen Änderungen:  
  
-   Verwenden eines neuen Typs, wenn eine Anwendung logisch nur einen Datums- oder Zeitwert erfordert. Die Anwendung musste jedoch datetime oder smalldatetime verwenden, da keine separaten Datums- und Zeittypen verfügbar waren.  
  
-   Verwenden eines neuen Typs, um zusätzliche Genauigkeit in Sekundenbruchteilen zu erzielen.  
  
-   Wechseln zu datetime2, da dies der bevorzugte Datentyp für Datum und Uhrzeit ist.  
  
### <a name="column-metadata-returned-by-sqlcolumns-sqlprocedurecolumns-and-sqlspecialcolumns"></a>Von 'SQLColumns', 'SQLProcedureColumns' und 'SWLSpecialColumns' zurückgegebene Spaltenmetadaten  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_WVARCHAR|SQL_WVARCHAR|  
|TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|COLUMN_SIZE|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|BUFFER_LENGTH|20|16, 20.. 32|16|16|38, 42.. 54|52, 56.. 68|  
|DECIMAL_DIGITS|NULL|NULL|0|3|NULL|NULL|  
|SQL_DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_DATETIME|SQL_DATETIME|SQL_WVARCHAR|SQL_WVARCHAR|  
|SQL_DATETIME_SUB|NULL|NULL|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|NULL|NULL|  
|CHAR_OCTET_LENGTH|NULL|NULL|NULL|NULL|NULL|NULL|  
|SS_DATA_TYPE|0|0|111|111|0|0|  
  
 SQLSpecialColumns gibt weder SQL_DATA_TYPE noch SQL_DATETIME_SUB, CHAR_OCTET_LENGTH oder SS_DATA_TYPE zurück.  
  
### <a name="data-type-metadata-returned-by-sqlgettypeinfo"></a>Von 'SQLGetTypeInfo' zurückgegebene Datentypmetadaten  
 Die folgenden Spaltenwerte werden für date/time-Typen zurückgegeben:  
  
|Spaltentyp|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_WVARCHAR|SQL_WVARCHAR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|  
|CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|AUTO_UNIQUE_VALUE|NULL|NULL|NULL|NULL|NULL|NULL|  
|LOCAL_TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|0|3|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|0|3|NULL|NULL|  
|SQL_DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_DATETIME|SQL_DATETIME|SQL_WVARCHAR|SQL_WVARCHAR|  
|SQL_DATETIME_SUB|NULL|NULL|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|NULL|NULL|  
|NUM_PREC_RADIX|NULL|NULL|NULL|NULL|NULL|NULL|  
|INTERVAL_PRECISION|NULL|NULL|NULL|NULL|NULL|NULL|  
|USERTYPE|0|0|12|22|0|0|  
  
## <a name="down-level-server-behavior"></a>Downlevelserver-Verhalten  
 Wenn bei der Verbindung mit einer Serverinstanz einer früheren Version von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] die neuen Servertypen oder zugehörige Metadatencodes und Deskriptorfelder verwendet werden, wird ein SQL_ERROR zurückgegeben. Es wird ein Diagnosedatensatz mit SQLSTATE HY004 und der Meldung "Ungültiger SQL-Datentyp für Serverversion in Verbindung" oder mit 07006 und der Meldung "Attributverletzung beschränkter Datentypen" zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datums-und Uhrzeit Verbesserungen &#40;ODBC-&#41;](date-and-time-improvements-odbc.md)  
  
  
