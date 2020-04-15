---
title: Header-Dateien | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 62364d828e7b1f1ed8c70cae7ae1fc7dc3bc33fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300190"
---
# <a name="header-files"></a>Headerdateien
Die Sql.h-Headerdatei enthält Prototypen für die Funktionen und Features in der Core ODBC Interface-Konformitätsebene. Die Sqlext.h-Headerdatei enthält Prototypen für die Funktionen und Funktionen in den API-Konformitätsstufen Level 1 und Level 2. Die Sqltypes.h-Headerdatei enthält Typdefinitionen und Indikatoren für die SQL-Datentypen.  
  
 Die Headerdateien enthalten alle einen **#define**, ODBCVER, den eine Anwendung oder ein Treiber so einstellen kann, dass sie für verschiedene Versionen von ODBC kompiliert werden.  
  
 Um an der ISO CLI und der Open Group CLI auszurichten, enthalten die Headerdateien Aliase für die Informationstypen, die in Aufrufen von **SQLGetInfo**verwendet werden. In der folgenden Tabelle gibt die Spalte "ODBC name" den ODBC-Namen für den Informationstyp in [ODBC API Reference](../../../odbc/reference/syntax/odbc-api-reference.md)an. Die Spalte "Alias in Headerdatei" gibt den Namen an, der in der ISO CLI und der Open Group CLI verwendet wird. Der tatsächliche numerische Wert dieser Manifestnamen ist sowohl in ODBC als auch in den Standard-CLIs identisch. Diese Aliase ermöglichen es einer standardkonformen Anwendung oder einem Treiber, mit den ODBC *3.x-Headerdateien* zu kompilieren.  
  
 Diese Aliase enthalten Erweiterungen von Abkürzungen in den ODBC-Namen, sodass die Namen verständlicher sind. "MAX" wird auf "MAXIMUM", "LEN" auf "LENGTH", "MULT" bis "MULTIPLE", "OJ" auf "OUTER_JOIN" und "TXN" auf "TRANSACTION" erweitert.  
  
|ODBC-Name|Alias in der Headerdatei|  
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
