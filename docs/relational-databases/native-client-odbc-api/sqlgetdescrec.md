---
description: SQLGetDescRec
title: Sqlgetdebug | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 04c209c9a9795e832648f91e52f1ee35f8f0db3c
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91811021"
---
# <a name="sqlgetdescrec"></a>SQLGetDescRec
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  In diesem Thema werden die SQLGetDescRec-Funktionalität erläutert, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client spezifisch ist.  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a>SQLGetDescRec und Tabellenwertparameter  
 SQLGetDescRec kann verwendet werden, um Werte für Attribute von Tabellenwert Parametern und Tabellenwert Parameter-Spalten zu erhalten. Der *RecNumber* -Parameter von sqlgetdebug entspricht dem *ParameterNumber* -Parameter von SQLBindParameter.  
  
 Tabellenwertparameter-Spalten sind nur verfügbar, wenn das Deskriptorheaderfeld SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Datensatzes festgelegt ist, für den SQL_DESC_TYPE auf SQL_SS_TABLE eingestellt ist. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS von finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Sqlgetdebug gibt die folgenden Daten zurück:  
  
|Parameter|Tabellenwertparameter|Tabellenwertparameter-Spalten und andere Parameter|  
|---------------|-----------------------------|----------------------------------------------------------|  
|*Name*|Der formale Parametername für einen Aufruf einer gespeicherten Prozedur; andernfalls eine Zeichenfolge mit der Länge 0.|Der Tabellenwertparameter-Spaltenname.|  
|*Typeptr*|SQL_DESC_TYPE. Bei Tabellenwertparametern ist dies SQL_SS_TABLE.|SQL_DESC_TYPE|  
|*Subtypeptr*|Nicht definiert|SQL_DESC_DATETIME_INTERVAL_CODE (für Datensätze vom Typ SQL_DATETIME oder SQL_INTERVAL)|  
|*Verlängert*|0|SQL_DESC_OCTET_LENGTH|  
|*"Precisionptr"*|0|SQL_DESC_PRECISION|  
|*Scaleptr*|0|SQL_DESC_SCALE|  
|*Nullableptr*|1|SQL_DESC_NULLABLE|  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a>SQLGetDescRec-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die für Datums-/Uhrzeittypen zurückgegebenen Werte lauten wie folgt:  
  
| attribute | *Typeptr* | *Subtypeptr* | *Verlängert* | *"Precisionptr"* | *Scaleptr* |  
| --------- | --------- | ------------ | ----------- | -------------- | ---------- |  
|datetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|date|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a>SQLGetDescRec-Unterstützung für große CLR-UDTs  
 **Sqlgetdebug** unterstützt große benutzerdefinierte CLR-Typen (User-Defined Types, UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLGetDescRec](../../odbc/reference/syntax/sqlgetdescrec-function.md)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
