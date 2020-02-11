---
title: Parameter-und Ergebnis Metadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f8f04d699c46c654290d1badc26de246a2d9125
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73783693"
---
# <a name="metadata---parameter-and-result"></a>Metadaten: Parameter und Ergebnis
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema wird beschrieben, was in den IPD- und IRD-Feldern (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) für Datums- und Uhrzeitdatentypen zurückgegeben wird.  
  
## <a name="information-returned-in-ipd-fields"></a>In IPD-Feldern zurückgegebene Informationen  
 Die folgenden Informationen werden in den IPD-Feldern zurückgegeben:  
  
|Parametertyp|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**date**|**time**|**smalldatetime** in IRD, **datetime2** in IPD|**DateTime** in IRD, **datetime2** in IPD|**datetime2**|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|–|–|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|–|  
  
 Manchmal treten in Wertbereichen Diskontinuitäten auf. Zum Beispiel fehlt 9 in der Angabe 8,10..16. Der Grund dafür ist das Hinzufügen eines Dezimaltrennzeichens, wenn die Genauigkeit von Bruchteilen größer als 0 (NULL) ist.  
  
 **datetime2** wird als typoame für **smalldatetime** und **DateTime** zurückgegeben, da der Treiber dies als allgemeinen Typ zum Übertragen aller **SQL_TYPE_TIMESTAMP** Werte an den Server verwendet.  
  
 SQL_CA_SS_VARIANT_SQL_TYPE ist ein neues Deskriptorfeld. Dieses Feld wurde zu IRD und IPD hinzugefügt, damit Anwendungen den Werttyp angeben können, der **sqlvariant** (SQL_SSVARIANT)-Spalten und-Parametern zugeordnet ist.  
  
 SQL_CA_SS_SERVER_TYPE ist ein neues IPD-Feld, mit dem Anwendungen steuern können, wie Werte für Parameter, die als SQL_TYPE_TYPETIMESTAMP (oder als SQL_SS_VARIANT mit dem C-Typ SQL_C_TYPE_TIMESTAMP) gebunden sind, an den Server gesendet werden. Wenn SQL_DESC_CONCISE_TYPE SQL_TYPE_TIMESTAMP (oder SQL_SS_VARIANT und der C-Typ SQL_C_TYPE_TIMESTAMP) ist, wenn SQLExecute oder SQLExecDirect aufgerufen wird, bestimmt der Wert von SQL_CA_SS_SERVER_TYPE den Tabular Data Stream (TDS)-Typ des Parameter Werts. , wie folgt:  
  
|Wert von SQL_CA_SS_SERVER_TYPE|Gültige Werte für SQL_DESC_PRECISION|Gültige Werte für SQL_DESC_LENGTH|TDS-Typ|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19, 21..27|**datetime2**|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|**smalldatetime**|  
|SQL_SS_TYPE_DATETIME|3|23|**datetime**|  
  
 Die Standardeinstellung von SQL_CA_SS_SERVER_TYPE ist SQL_SS_TYPE_DEFAULT. Die Einstellungen von SQL_DESC_PRECISION und SQL_DESC_LENGTH werden mit der Einstellung von SQL_CA_SS_SERVER_TYPE wie in der Tabelle oben beschrieben überprüft. Wenn diese Prüfung fehlschlägt, wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLState 07006 und der Meldung "Attributverletzung beschränkter Datentypen" protokolliert. Dieser Fehler wird auch zurückgegeben, wenn SQL_CA_SS_SERVER_TYPE auf einen anderen Wert als SQL_SS_TYPE DEFAULT festgelegt wird und DESC_CONCISE_TYPE nicht gleich SQL_TYPE_TIMESTAMP ist. Diese Überprüfungen werden im Rahmen der Prüfung der Deskriptorkonsistenz durchgeführt, beispielsweise:  
  
-   Wenn SQL_DESC_DATA_PTR geändert wird.  
  
-   Während der Vorbereitung oder Ausführung (wenn SQLExecute, SQLExecDirect, SQLSetPos oder SQLBulkOperations aufgerufen wird).  
  
-   Wenn eine Anwendung eine nicht verzögerte Vorbereitung durch Aufrufen von SQLPrepare mit der verzögerten Vorbereitung deaktiviert oder durch Aufrufen von SQLNumResultCols, SQLDescribeCol oder SQLDescribeParam für eine Anweisung erzwingt, die vorbereitet, aber nicht ausgeführt wird.  
  
 Wenn SQL_CA_SS_SERVER_TYPE durch einen Aufrufen von SQLSetDescField festgelegt wird, muss der Wert SQL_SS_TYPE_DEFAULT, SQL_SS_TYPE_SMALLDATETIME oder SQL_SS_TYPE_DATETIME sein. Ist dies nicht der Fall, wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLState HY092 und der Meldung "Ungültiger Attribut-/Optionsbezeichner" protokolliert.  
  
 Das SQL_CA_SS_SERVER_TYPE-Attribut kann von Anwendungen verwendet werden, die von Funktionen abhängen, die von **DateTime** und **smalldatetime**unterstützt werden, jedoch nicht von **datetime2**. **Datetime2** erfordert beispielsweise die Verwendung der Funktionen **DateAdd** und **datediif** , während **DateTime** und **smalldatetime** auch arithmetische Operatoren zulassen. Die meisten Anwendungen müssen dieses Attribut nicht verwenden, und seine Verwendung sollte vermieden werden.  
  
## <a name="information-returned-in-ird-fields"></a>In IRD-Feldern zurückgegebene Informationen  
 Die folgenden Informationen werden in IRD-Feldern zurückgegeben:  
  
|Spaltentyp|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8, 10.. 16|16|2|19, 21..27|26, 28..34|  
|SQL_DESC_LITERAL_PREFIX|'|'|'|'|'|'|  
|SQL_DESC_LITERAL_SUFFIX|'|'|'|'|'|'|  
|SQL_DESC_LOCAL_TYPE_NAME|**date**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**date**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Metadaten &#40;ODBC-&#41;](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
  
  
