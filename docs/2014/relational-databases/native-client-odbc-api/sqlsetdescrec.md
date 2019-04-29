---
title: SQLSetDescRec | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescRec function
ms.assetid: 203d02a2-aa09-462b-a489-a2cdd6f6023b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d323b1b92ba02e55064d2f86c62ee36a4a38d904
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188780"
---
# <a name="sqlsetdescrec"></a>SQLSetDescRec
  SQLSetDescRec-Funktion, die spezifisch für ist in diesem Thema [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="sqlsetdescrec-and-table-valued-parameters"></a>SQLSetDescRec und Tabellenwertparameter  
 SQLSetDescRec kann verwendet werden, um deskriptorfelder für Tabellenwertparameter und Tabellenwertparameter-Spalten festzulegen. Tabellenwertparameter-Spalten sind nur verfügbar, wenn das Deskriptorheaderfeld SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Datensatzes festgelegt ist, für den SQL_DESC_TYPE auf SQL_SS_TABLE eingestellt ist. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 In der folgenden Tabelle wird die Zuordnung zwischen Parametern und Deskriptorfeldern beschrieben.  
  
|Parameter|Verknüpftes Attribut für nicht-Tabellenwertparameter-Typen, einschließlich Tabellenwertparameter-Spalten|Verknüpftes Attribut für Tabellenwertparameter|  
|---------------|--------------------------------------------------------------------------------------------------------|----------------------------------------------------|  
|*Typ*|SQL_DESC_TYPE|SQL_SS_TABLE|  
|*SubType*|Wird ignoriert.|Für Datensätze des Typs SQL_DATETIME oder SQL_INTERVAL wird es auf SQL_DESC_DATETIME_INTERVAL_CODE festgelegt.|  
|*Länge*|SQL_DESC_OCTET_LENGTH|Die Länge des Typnamens des Tabellenwertparameters. Kann SQL_NTS sein, wenn der Typname NULL-termininiert ist, oder Null (0), wenn der Typname des Tabellenwertparameters nicht erforderlich ist.|  
|*Genauigkeit*|SQL_DESC_PRECISION|SQL_DESC_ARRAY_SIZE|  
|*Dezimalstellen*|SQL_DESC_SCALE|Nicht verwendet. Dieser Parameter sollte 0 (null) sein.|  
|*DataPtr*|SQL_DESC_DATA_PTR in APD|SQL_CA_SS_TYPE_NAME<br /><br /> Dies ist ein optionaler Parameter für gespeicherte Prozeduren, und NULL kann angegeben werden, wenn er nicht erforderlich ist. Dieser Parameter muss für SQL-Anweisungen angegeben werden, die keine Prozeduraufrufe sind.<br /><br /> *DataPtr* dient auch als eindeutiger Wert, der die Anwendung verwenden kann, um diese Tabellenwertparameter zu identifizieren, wenn Variablen zeilenbindung verwendet wird.|  
|*StringLengthPtr*|SQL_DESC_OCTET_LENGTH_PTR|SQL_DESC_OCTET_LENGTH_PTR<br /><br /> Bei einem Tabellenwertparameter ist dies die Anzahl der zu übertragenden Zeilen oder SQL_DATA_AT_EXEC. Dies ist ein Zeiger auf einen Wert, der die Anzahl der Zeilen mit SQLExecDirect übertragen enthält.|  
|*IndicatorPtr*|SQL_DESC_INDICATOR_PTR|SQL_DESC_INDICATOR_PTR|  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescrec-support-for-enhanced-date-and-time-features"></a>SQLSetDescRec-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die für Datums-/Uhrzeittypen zulässigen Werte lauten wie folgt:  
  
||*Typ*|*SubType*|*Länge*|*Genauigkeit*|*Dezimalstellen*|  
|-|------------|---------------|--------------|-----------------|-------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|date|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescrec-support-for-large-clr-udts"></a>SQLSetDescRec-Unterstützung für große CLR-UDTs  
 `SQLSetDescRec` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLSetDescRec](https://go.microsoft.com/fwlink/?LinkId=80704)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
