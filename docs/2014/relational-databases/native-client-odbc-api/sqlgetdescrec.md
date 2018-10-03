---
title: SQLGetDescRec | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51f83f4bc0cfc60a2e8137407a7efc9635dd9f70
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48229220"
---
# <a name="sqlgetdescrec"></a>SQLGetDescRec
  SQLGetDescRec-Funktion, die spezifisch für ist in diesem Thema [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a>SQLGetDescRec und Tabellenwertparameter  
 SQLGetDescRec kann verwendet werden, um Werte für Attribute von Tabellenwertparametern und Tabellenwertparameter-Spalten zu erhalten. Die *RecNumber* Parameter des SQLGetDescRec entspricht der *ParameterNumber* -Parameter von SQLBindParameter.  
  
 Tabellenwertparameter-Spalten sind nur verfügbar, wenn das Deskriptorheaderfeld SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Datensatzes festgelegt ist, für den SQL_DESC_TYPE auf SQL_SS_TABLE eingestellt ist. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS zu finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 SQLGetDescRec gibt die folgenden Daten zurück:  
  
|Parameter|Tabellenwertparameter|Tabellenwertparameter-Spalten und andere Parameter|  
|---------------|-----------------------------|----------------------------------------------------------|  
|*Name*|Der formale Parametername für einen Aufruf einer gespeicherten Prozedur; andernfalls eine Zeichenfolge mit der Länge 0.|Der Tabellenwertparameter-Spaltenname.|  
|*TypePtr*|SQL_DESC_TYPE. Bei Tabellenwertparametern ist dies SQL_SS_TABLE.|SQL_DESC_TYPE|  
|*SubTypePtr*|Nicht definiert|SQL_DESC_DATETIME_INTERVAL_CODE (für Datensätze vom Typ SQL_DATETIME oder SQL_INTERVAL)|  
|*LengthPtr*|0|SQL_DESC_OCTET_LENGTH|  
|*PrecisionPtr*|0|SQL_DESC_PRECISION|  
|*ScalePtr*|0|SQL_DESC_SCALE|  
|*NullablePtr*|1|SQL_DESC_NULLABLE|  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a>SQLGetDescRec-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die für Datums-/Uhrzeittypen zurückgegebenen Werte lauten wie folgt:  
  
||*TypePtr*|*SubTypePtr*|*LengthPtr*|*PrecisionPtr*|*ScalePtr*|  
|-|---------------|------------------|-----------------|--------------------|----------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|date|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|Uhrzeit|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a>SQLGetDescRec-Unterstützung für große CLR-UDTs  
 `SQLGetDescRec` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLGetDescRec](http://go.microsoft.com/fwlink/?LinkId=80707)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
