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
ms.openlocfilehash: f65c26e1c6b9588b770acf1a66409dfde8ea1072
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63188674"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
  SQLSetDescField kann verwendet werden, um Deskriptorfelder für Tabellenwert Parameter und Tabellenwert Parameter-Spalten festzulegen. Weitere Informationen zu den verfügbaren Feldern finden Sie unter [Tabellenwert Parameter-Deskriptorfelder](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) und [Deskriptorfelder für einzelne Tabellenwert Parameter-Spalten](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).  
  
## <a name="remarks"></a>Hinweise  
 Tabellenwertparameter-Spalten sind nur verfügbar, wenn das Deskriptorheaderfeld SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Datensatzes festgelegt ist, für den SQL_DESC_TYPE auf SQL_SS_TABLE eingestellt ist. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Wenn versucht wird, SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Parameters festzulegen, bei dem es sich nicht um einen Tabellenwert Parameter handelt, gibt SQLSetStmtAttr SQL_ERROR zurück, und es wird ein Diagnosedaten Satz mit SQLSTATE = HY024 und der Meldung "Ungültiger Attribut Wert" erstellt. SQL_SOPT_SS_PARAM_FOCUS wird nicht geändert, wenn SQL_ERROR zurückgegeben wird.  
  
 Durch das Festlegen von SQL_SOPT_SS_PARAM_FOCUS auf 0 (null) wird der Zugriff auf Deskriptordatensätze für Parameter wiederhergestellt.  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>SQLSetDescField-Unterstützung für erweiterte Funktionen zu Datum und Uhrzeit  
 Datum/Uhrzeit-Funktionen wurden in ODBC verbessert. Informationen über das für die neuen Datum/Uhrzeittypen verfügbare Deskriptorfeld finden Sie unter [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>SQLSetDescField-Unterstützung für große CLR-UDTs  
 SQLSetDescField unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>SQLSetDescField-Unterstützung für Spalten mit geringer Dichte  
 SQLSetDecField kann verwendet werden, um SQL_SOPT_SS_NAME_SCOPE im Anwendungsparameter Deskriptor (Application Parameter Deskriptor, APD) auf die Werte SQL_SS_NAME_SCOPE_EXTENDED und SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET festzulegen.  
  
 Weitere Informationen finden Sie [unter Unterstützung für sparsespalten &#40;ODBC-&#41;](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
