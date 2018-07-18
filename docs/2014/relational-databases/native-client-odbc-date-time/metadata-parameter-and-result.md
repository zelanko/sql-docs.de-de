---
title: Parameter- und Ergebnismetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f07127b8ae80ff212f671d94f55a311584552c58
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420185"
---
# <a name="parameter-and-result-metadata"></a>Parameter- und Ergebnismetadaten
  In diesem Thema wird beschrieben, was in den IPD- und IRD-Feldern (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) für Datums- und Uhrzeitdatentypen zurückgegeben wird.  
  
## <a name="information-returned-in-ipd-fields"></a>In IPD-Feldern zurückgegebene Informationen  
 Die folgende Informationen wird in den IPD-Feldern zurückgegeben:  
  
|Parametertyp|date|Uhrzeit|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|`date`|`time`|`smalldatetime` in IRD, `datetime2` in IPD|`datetime` in IRD, `datetime2` in IPD|`datetime2`|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|–|–|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|–|  
  
 Manchmal treten in Wertbereichen Diskontinuitäten auf. Zum Beispiel fehlt 9 in der Angabe 8,10..16. Der Grund dafür ist das Hinzufügen eines Dezimaltrennzeichens, wenn die Genauigkeit von Bruchteilen größer als 0 (NULL) ist.  
  
 `datetime2` wird als Typname für `smalldatetime` und `datetime` zurückgegeben, weil der Treiber dies als gemeinsamen Typen für die Übermittlung aller `SQL_TYPE_TIMESTAMP`-Werte an den Server verwendet.  
  
 SQL_CA_SS_VARIANT_SQL_TYPE ist ein neues Deskriptorfeld. Dieses Feld wurde IRD und IPD hinzugefügt, um es Anwendungen zu ermöglichen, den mit Spalten und Parametern des Typs `sqlvariant` (SQL_SSVARIANT) verknüpften Werttyp anzugeben.  
  
 SQL_CA_SS_SERVER_TYPE ist ein neues IPD-Feld, mit dem Anwendungen steuern können, wie Werte für Parameter, die als SQL_TYPE_TYPETIMESTAMP (oder als SQL_SS_VARIANT mit dem C-Typ SQL_C_TYPE_TIMESTAMP) gebunden sind, an den Server gesendet werden. Wenn SQL_DESC_CONCISE_TYPE SQL_TYPE_TIMESTAMP ist (oder gleich SQL_SS_VARIANT und der C-Typ ist SQL_C_TYPE_TIMESTAMP) Wenn SQLExecute oder SQLExecDirect aufgerufen wird, wird der Wert von SQL_CA_SS_SERVER_TYPE bestimmt, der tabular Data stream (TDS)-Typ des Parameterwerts , wie folgt:  
  
|Wert von SQL_CA_SS_SERVER_TYPE|Gültige Werte für SQL_DESC_PRECISION|Gültige Werte für SQL_DESC_LENGTH|TDS-Typ|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19, 21..27|`datetime2`|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|`smalldatetime`|  
|SQL_SS_TYPE_DATETIME|3|23|`datetime`|  
  
 Die Standardeinstellung von SQL_CA_SS_SERVER_TYPE ist SQL_SS_TYPE_DEFAULT. Die Einstellungen von SQL_DESC_PRECISION und SQL_DESC_LENGTH werden mit der Einstellung von SQL_CA_SS_SERVER_TYPE wie in der Tabelle oben beschrieben überprüft. Wenn diese Prüfung fehlschlägt, wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLState 07006 und der Meldung "Attributverletzung beschränkter Datentypen" protokolliert. Dieser Fehler wird auch zurückgegeben, wenn SQL_CA_SS_SERVER_TYPE auf einen anderen Wert als SQL_SS_TYPE DEFAULT festgelegt wird und DESC_CONCISE_TYPE nicht gleich SQL_TYPE_TIMESTAMP ist. Diese Überprüfungen werden im Rahmen der Prüfung der Deskriptorkonsistenz durchgeführt, beispielsweise:  
  
-   Wenn SQL_DESC_DATA_PTR geändert wird.  
  
-   Während der Vorbereitung oder Ausführung (wenn SQLExecute, SQLExecDirect, SQLSetPos oder SQLBulkOperations aufgerufen wird).  
  
-   Wenn Sie eine Anwendung erzwingt, dass eine nicht verzögerte Vorbereitung durch den Aufruf von SQLPrepare mit verzögerte Vorbereitung deaktiviert oder durch Aufrufen von SQLNumResultCols, SQLDescribeCol oder SQLDescribeParam für eine Anweisung, die aber nicht vorbereitet wird ausgeführt.  
  
 Wenn SQL_CA_SS_SERVER_TYPE durch einen Aufruf von SQLSetDescField festgelegt ist, muss sein Wert SQL_SS_TYPE_DEFAULT, SQL_SS_TYPE_SMALLDATETIME oder sql_ss_type_datetime lauten. Ist dies nicht der Fall, wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLState HY092 und der Meldung "Ungültiger Attribut-/Optionsbezeichner" protokolliert.  
  
 Das SQL_CA_SS_SERVER_TYPE-Attribut kann in Anwendungen verwendet werden, die von Funktionen abhängen, die von `datetime` und `smalldatetime`, nicht jedoch von `datetime2` unterstützt werden. Z. B. `datetime2` erfordert die Verwendung der `dateadd` und **Datediif** Funktionen, während die `datetime` und `smalldatetime` auch arithmetische Operatoren zulassen. Die meisten Anwendungen müssen dieses Attribut nicht verwenden, und seine Verwendung sollte vermieden werden.  
  
## <a name="information-returned-in-ird-fields"></a>In IRD-Feldern zurückgegebene Informationen  
 Die folgenden Informationen werden in IRD-Feldern zurückgegeben:  
  
|Spaltentyp|date|Uhrzeit|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|2|19, 21..27|26, 28..34|  
|SQL_DESC_LITERAL_PREFIX|‘|‘|‘|‘|‘|‘|  
|SQL_DESC_LITERAL_SUFFIX|‘|‘|‘|‘|‘|‘|  
|SQL_DESC_LOCAL_TYPE_NAME|`date`|`time`|`smalldatetime`|`datetime`|`datetime2`|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|`date`|`time`|`smalldatetime`|`datetime`|`datetime2`|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>Siehe auch  
 [Metadaten &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
  
  
