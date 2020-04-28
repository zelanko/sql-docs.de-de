---
title: Header Dateien | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300190"
---
# <a name="header-files"></a>Headerdateien
Die Header Datei "SQL. h" enthält Prototypen für die Funktionen und Funktionen in der ODBC-Schnittstellen Übereinstimmungs Ebene "Core". Die Header Datei sqlext. h enthält Prototypen für die Funktionen und Features in den API-Konformitäts Ebenen der Ebene 1 und Ebene 2. Die Header Datei SqlTypes. h enthält Typdefinitionen und Indikatoren für die SQL-Datentypen.  
  
 Die Header Dateien enthalten alle ein **#define**(ODBCVer), das von einer Anwendung oder einem Treiber für die Kompilierung für verschiedene Versionen von ODBC festgelegt werden kann.  
  
 Die Header Dateien enthalten Aliase für die Informationstypen, die in Aufrufen von **SQLGetInfo**verwendet werden, um die ISO CLI und die Open Group-CLI auszurichten. In der folgenden Tabelle gibt die Spalte "ODBC Name" den ODBC-Namen für den Informationstyp in der [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)an. Die Spalte "Alias in Header Datei" gibt den Namen an, der in der ISO-CLI und in der Open-Group-CLI verwendet wird. Der tatsächliche numerische Wert dieser manifestressamen ist in ODBC und in den Standard-Clis identisch. Diese Aliase ermöglichen es einer Standard kompatiblen Anwendung oder einem Standardtreiber, mit den ODBC *3. x* -Header Dateien zu kompilieren.  
  
 Diese Aliase enthalten Erweiterungen von Abkürzungen in den ODBC-Namen, damit die Namen verständlicher werden. "Max" wird auf "Maximum", "len" bis "length", "mult" in "Multiple", "oj" auf "OUTER_JOIN" und "TXn" in "Transaction" erweitert.  
  
|ODBC-Name|Alias in Header Datei|  
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
