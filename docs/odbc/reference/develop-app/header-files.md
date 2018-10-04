---
title: Headerdateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- header files [ODBC]
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e6d0806a7c3eabd1c6f4cd1836308eba99a6d5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656738"
---
# <a name="header-files"></a>Headerdateien
Die Headerdatei Sql.h enthält Prototypen für die Funktionen und Funktionen in der Konformitätsgrad des Core-ODBC-Schnittstelle. Die Headerdatei Sqlext.h enthält Prototypen für die Funktionen und Funktionen in der Ebene 1 und Level 2-API-Konformitätsgrad. Die Headerdatei Sqltypes.h enthält Typdefinitionen und Indikatoren für die SQL-Datentypen.  
  
 Die Headerdateien enthalten eine **#define**, ODBCVER, die eine Anwendung oder ein Treiber festlegen können, für verschiedene Versionen von ODBC kompiliert werden.  
  
 Um mit dem ISO-CLI und Open Group CLI auszurichten, die Headerdateien enthalten Aliase für den Informationstypen, die in Aufrufen verwendet **SQLGetInfo**. In der folgenden Tabelle gibt die Spalte "ODBC-Name" an den ODBC-Namen für den Informationstyp im [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md). Die Spalte "Alias in der Headerdatei" gibt an, den Namen, der in der ISO-CLI und die Open Group-CLI verwendet wird. Der tatsächliche numerische Wert dieser manifest Namen ist in ODBC und die standard-CLIs identisch. Diese Aliase zu ermöglichen, eine Standards kompatible Anwendung oder den Treiber mit der ODBC 3. Kompilieren *.x* Headerdateien.  
  
 Diese Aliase enthalten Erweiterungen der Abkürzungen in den ODBC-Namen, sodass die Namen der leichter verständlich sind. "MAX" wird zu "MAXIMUM", "LEN", "LENGTH", "MULT" auf "MULTIPLE", "ABl.", "OUTER_JOIN" und "Transaktionsvorgänge", "Transaction". erweitert  
  
|ODBC-name|Alias in der Headerdatei.|  
|---------------|--------------------------|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAXIMUM_CATALOG_NAME_LENGTH|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAXIMUM_COLUMN_NAME_LENGTH|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAXIMUM_COLUMNS_IN_GROUP_BY|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAXIMUM_COLUMNS_IN_ORDER_BY|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAXIMUM_COLUMNS_IN_SELECT|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAXIMUM_COLUMNS_IN_TABLE|  
|SQL_MAX_CONCURRENT_ACTIVITIES|SQL_MAXIMUM_CONCURRENT_ACTIVITIES|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAXIMUM_CURSOR_NAME_LENGTH|  
|SQL_MAX_DRIVER_CONNECTIONS|SQL_MAXIMUM_DRIVER_CONNECTIONS|  
|SQL_MAX_IDENTIFIER_LEN|SQL_MAXIMUM_IDENTIFIER_LENGTH|  
|SQL_MAX_SCHEMA_NAME_LEN|SQL_MAXIMUM_SCHEMA_NAME_LENGTH|  
|SQL_MAX_STATEMENT_LEN|SQL_MAXIMUM_STATEMENT_LENGTH|  
|SQL_MAX_TABLE_NAME_LEN|SQL_MAXIMUM_TABLE_NAME_LENGTH|  
|SQL_MAX_TABLES_IN_SELECT|SQL_MAXIMUM_TABLES_IN_SELECT|  
|SQL_MAX_USER_NAME_LEN|SQL_MAXIMUM_USER_NAME_LENGTH|  
|SQL_MULT_RESULT_SETS|SQL_MULTIPLE_RESULT_SETS|  
|SQL_OJ_CAPABILITIES|SQL_OUTER_JOIN_CAPABILITIES|  
|SQL_TXN_CAPABLE|SQL_TRANSACTION_CAPABLE|  
|SQL_TXN_ISOLATION_OPTION|SQL_TRANSACTION_ISOLATION_OPTION|
