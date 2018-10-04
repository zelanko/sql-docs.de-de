---
title: SQLSetDescField | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64eb7b3dc6f058d5f061f4c015105ba4fc44f183
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206760"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
  SQLSetDescField kann verwendet werden, um deskriptorfelder für Tabellenwertparameter und Tabellenwertparameter-Spalten festzulegen. Weitere Informationen zu den verfügbaren Feldern finden Sie unter [Deskriptorfelder für Tabellenwertparameter-Parameter](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) und [Deskriptorfelder für Tabellenwertparameter-Parameter enthaltene Spalten](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).  
  
## <a name="remarks"></a>Hinweise  
 Tabellenwertparameter-Spalten sind nur verfügbar, wenn das Deskriptorheaderfeld SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Datensatzes festgelegt ist, für den SQL_DESC_TYPE auf SQL_SS_TABLE eingestellt ist. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Wenn es versucht wird, um SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Parameters festzulegen, die nicht auf einem Tabellenwertparameter ist SQLSetStmtAttr SQL_ERROR zurück gibt und ein Diagnosedatensatz mit SQLSTATE erstellt = HY024 und der Meldung "Ungültiger Attributwert". SQL_SOPT_SS_PARAM_FOCUS wird nicht geändert, wenn SQL_ERROR zurückgegeben wird.  
  
 Durch das Festlegen von SQL_SOPT_SS_PARAM_FOCUS auf 0 (null) wird der Zugriff auf Deskriptordatensätze für Parameter wiederhergestellt.  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>SQLSetDescField-Unterstützung für erweiterte Funktionen zu Datum und Uhrzeit  
 Datum/Uhrzeit-Funktionen wurden in ODBC verbessert. Informationen zu den für die neuen Datums-/Uhrzeittypen verfügbare Deskriptorfeld finden Sie unter [Parameter- und Ergebnismetadaten](../native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>SQLSetDescField-Unterstützung für große CLR-UDTs  
 SQLSetDescField unterstützt große CLR-benutzerdefinierte Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>SQLSetDescField-Unterstützung für Spalten mit geringer Dichte  
 SQLSetDecField kann verwendet werden, zum Festlegen von SQL_SOPT_SS_NAME_SCOPE im anweisungsparameterdeskriptor (APD) auf die Werte SQL_SS_NAME_SCOPE_EXTENDED und SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.  
  
 Weitere Informationen finden Sie unter [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLSetDescField](http://go.microsoft.com/fwlink/?LinkId=80705)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
