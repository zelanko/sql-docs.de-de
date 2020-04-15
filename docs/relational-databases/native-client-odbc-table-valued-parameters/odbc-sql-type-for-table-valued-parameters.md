---
title: ODBC SQL-Typ für Tabellenwertparameter | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6aae522544f4d9532dbc2d71db1b3d55ebee3da5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297840"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>ODBC-SQL-Typ für Tabellenwertparameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Unterstützung für Tabellenwertparameter wird von einem neuen ODBC-SQL-Typ, SQL_SS_TABLE, bereitgestellt.  
  
## <a name="remarks"></a>Bemerkungen  
 SQL_SS_TABLE kann nicht in einen anderen ODBC- oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp konvertiert werden.  
  
 Wenn SQL_SS_TABLE als C-Datentyp im *ValueType-Parameter* von SQLBindParameter verwendet wird oder versucht wird, SQL_DESC_TYPE in einem APD-Eintrag (Application Parameter Descriptor) auf SQL_SS_TABLE festzulegen, wird SQL_ERROR zurückgegeben, und ein Diagnosedatensatz wird mit SQLSTATE=HY003, "Ungültiger Anwendungspuffertyp", generiert.  
  
 Wenn SQL_DESC_TYPE in einem IPD-Datensatz auf SQL_SS_TABLE festgelegt wird, und der entsprechende Anwendungsparameterdeskriptor-Datensatz nicht SQL_C_DEFAULT ist, wird SQL_ERROR zurückgegeben, und ein Diagnosedatensatz mit der Meldung SQLSTATE=HY003, "Ungültiger Anwendungspuffertyp" wird generiert. Dies kann mit dem *ParameterType* eines SQLSetDescField, SQLSetDescRec oder SQLBindParameter auftreten.  
  
 Wenn der *TargetType-Parameter* beim Aufrufen von SQLGetData SQL_SS_TABLE ist, wird SQL_ERROR zurückgegeben, und ein Diagnosedatensatz wird mit SQLSTATE=HY003, "Ungültiger Anwendungspuffertyp", generiert.  
  
 Eine Tabellenwertparameter-Spalte kann nicht als SQL_SS_TABLE-Datentyp gebunden werden. Wenn der **SQLBindParameter** -Parameter aufgerufen wird und *ParameterType* auf SQL_SS_TABLE festgelegt ist, wird SQL_ERROR zurückgegeben, und ein Diagnosedatensatz mit der Meldung SQLSTATE=HY004, "Ungültiger SQL-Datentyp" generiert. Dies kann auch mit SQLSetDescField und SQLSetDescRec auftreten.  
  
 Tabellenwertparameter-Spaltenwerte verfügen über dieselben Datenkonvertierungsoptionen wie Parameter und Ergebnisspalten.  
  
 Bei einem Tabellenwertparameter kann es sich nur um einen Eingabeparameter in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder höher handeln. Wenn versucht wird, SQL_DESC_PARAMETER_TYPE über SQLBindParameter oder SQLSetDescField auf einen anderen Wert als SQL_PARAM_INPUT festzulegen, wird SQL_ERROR zurückgegeben, und der Anweisung wird mit SQLSTATE=HY105 und der Meldung "Ungültiger Parametertyp" ein Diagnosedatensatz hinzugefügt.  
  
 Tabellenwertparameter-Spalten können SQL_DEFAULT_PARAM nicht in *StrLen_or_IndPtr*verwenden, da Standardwerte pro Zeile nicht mit Tabellenwertparametern unterstützt werden. Stattdessen kann eine Anwendung das Spaltenattribut SQL_CA_SS_COL_HAS_DEFAULT_VALUE auf 1 festlegen. Dies bedeutet, dass die Spalte Standardwerte für alle Zeilen aufweist. Wenn *StrLen_or_IndPtr* auf SQL_DEFAULT_PARAM festgelegt ist, gibt SQLExecute oder SQLExecDirect SQL_ERROR zurück, und der Anweisung wird ein Diagnosedatensatz mit SQLSTATE=HY090 und der Meldung "Ungültige Zeichenfolge oder Pufferlänge" hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenbewertete Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
