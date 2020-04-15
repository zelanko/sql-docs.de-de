---
title: SQLSetDescRec | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescRec function
ms.assetid: 203d02a2-aa09-462b-a489-a2cdd6f6023b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a083aa6d17a84ff4c801ad5f5b270c7f0ddcb355
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301911"
---
# <a name="sqlsetdescrec"></a>SQLSetDescRec
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema wird die SQLSetDescRec-Funktionalität erläutert, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den systemeigenen Client spezifisch ist.  
  
## <a name="sqlsetdescrec-and-table-valued-parameters"></a>SQLSetDescRec und Tabellenwertparameter  
 SQLSetDescRec kann verwendet werden, um Deskriptorfelder für Tabellenparameter und Parameterspalten mit Tabellenwert festzulegen. Tabellenwertparameter-Spalten sind nur verfügbar, wenn das Deskriptorheaderfeld SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Datensatzes festgelegt ist, für den SQL_DESC_TYPE auf SQL_SS_TABLE eingestellt ist. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 In der folgenden Tabelle wird die Zuordnung zwischen Parametern und Deskriptorfeldern beschrieben.  
  
|Parameter|Zugehöriges Attribut für Nichttabellenwertparametertypen, einschließlich Tabellenwertparameterspalten|Verknüpftes Attribut für Tabellenwertparameter|  
|---------------|--------------------------------------------------------------------------------------------------------|----------------------------------------------------|  
|*Typ*|SQL_DESC_TYPE|SQL_SS_TABLE|  
|*Untertyp*|Wird ignoriert.|Für Datensätze des Typs SQL_DATETIME oder SQL_INTERVAL wird es auf SQL_DESC_DATETIME_INTERVAL_CODE festgelegt.|  
|*Länge*|SQL_DESC_OCTET_LENGTH|Die Länge des Typnamens des Tabellenwertparameters. Kann SQL_NTS sein, wenn der Typname NULL-termininiert ist, oder Null (0), wenn der Typname des Tabellenwertparameters nicht erforderlich ist.|  
|*Genauigkeit*|SQL_DESC_PRECISION|SQL_DESC_ARRAY_SIZE|  
|*Skalieren*|SQL_DESC_SCALE|Nicht verwendet. Dieser Parameter sollte 0 (null) sein.|  
|*DataPtr*|SQL_DESC_DATA_PTR in APD|SQL_CA_SS_TYPE_NAME<br /><br /> Dies ist ein optionaler Parameter für gespeicherte Prozeduren, und NULL kann angegeben werden, wenn er nicht erforderlich ist. Dieser Parameter muss für SQL-Anweisungen angegeben werden, die keine Prozeduraufrufe sind.<br /><br /> *DataPtr* dient auch als eindeutiger Wert, den die Anwendung verwenden kann, um diesen Parameter mit Tabellenwert zu identifizieren, wenn variable Zeilenbindung verwendet wird.|  
|*StringLengthPtr*|SQL_DESC_OCTET_LENGTH_PTR|SQL_DESC_OCTET_LENGTH_PTR<br /><br /> Bei einem Tabellenwertparameter ist dies die Anzahl der zu übertragenden Zeilen oder SQL_DATA_AT_EXEC. Dies ist ein Zeiger auf einen Wert, der die Anzahl der Zeilen enthält, die mit SQLExecDirect übertragen werden sollen.|  
|*IndikatorPtr*|SQL_DESC_INDICATOR_PTR|SQL_DESC_INDICATOR_PTR|  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescrec-support-for-enhanced-date-and-time-features"></a>SQLSetDescRec-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die für Datums-/Uhrzeittypen zulässigen Werte lauten wie folgt:  
  
||*Typ*|*Untertyp*|*Länge*|*Genauigkeit*|*Skalieren*|  
|-|------------|---------------|--------------|-----------------|-------------|  
|datetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|date|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Weitere Informationen finden Sie unter [Datums- und Zeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescrec-support-for-large-clr-udts"></a>SQLSetDescRec-Unterstützung für große CLR-UDTs  
 **SQLSetDescRec** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Große benutzerdefinierte CLR-Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLSetDescRec](https://go.microsoft.com/fwlink/?LinkId=80704)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
