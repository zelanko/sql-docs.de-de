---
title: Unterstützt ODBC-API-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC, API functions
- ODBC SQL grammar, API functions mapped to driver (table) [ODBC]
ms.assetid: b28a8ed6-09b1-4acf-bf3e-f90bb32422de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 460b1cb00f68e9b1940a1680625a173bc92e6f84
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633400"
---
# <a name="supported-odbc-api-functions"></a>Unterstützte ODBC-API-Funktionen
Der Zweck der Lastenausgleich ist auf die Anwendung zu informieren, welche Features, aus dem Treiber verfügbar sind. Der Microsoft ODBC Desktop-Datenbanktreiber unterstützt alle Funktionen von Core und Ebene 1.  
  
 Weitere Informationen zu den Ebenen der schnittstellenübereinstimmung für Funktionen und -Grammatik finden Sie unter [Übereinstimmungsebenen](../../odbc/reference/develop-app/conformance-levels.md) in die *ODBC Programmer's Reference*.  
  
 Unterstützung für ODBC API-Funktionen kann abhängig von der Treiber verwendet werden. Die folgende Tabelle enthält die Unterstützung für Funktionen. Die äußerste linke Spalte enthält einen Link zu der Seite "Allgemeine Referenz" für jede Funktion. Diese Referenzseiten werden in alphabetischer Reihenfolge aufgeführt der [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md) -Abschnitt unter [ODBC Programmer's Reference](../../odbc/reference/odbc-programmer-s-reference.md). Die Spalten aus, die Links rechts geben Driver-spezifischen Anmerkungen zu dieser zu den einzelnen unterstützten Funktionen. Diese Treiber-spezifische Themen finden Sie im Abschnitt "Weitere Informationen zur Programmierung von" für jeden Treiber. Auch wenn die gleichen Hinweise zu einer Funktion auf alle ODBC-Desktop-Datenbanktreiber anwenden zu können, enthält die Spalte ganz rechts, einen Link an ein Thema, das die Desktop-Datenbanktreiber-Unterstützung für diese Funktion zusammenfasst. In diesen Themen finden Sie am Ende der aktuelle Abschnitt ("unterstützt ODBC-API-Funktionen").  
  
|ODBC-Funktion|Access-Treiber-spezifische Notizen|dBASE-Treiber-spezifische Notizen|Paradox-Treiber-spezifische Notizen|Treiber-spezifischen Anmerkungen|Excel-Treiber-spezifische Notizen|Anmerkungen zu dieser Version für alle Treiber|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Zugriff](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[dBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Zugriff](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[dBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[Zugriff](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[dBASE](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[Zugriff](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[dBASE](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[Zugriff](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[dBASE](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)|
|[SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)|  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[Zugriff](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[dBASE](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[Zugriff](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)||||||  
|[SQLProcedures](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[Zugriff](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[dBASE](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[SQLSetPos](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|[SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|[SQLStatistics](../../odbc/reference/syntax/sqlstatistics-function.md)|[Zugriff](../../odbc/microsoft/sqlstatistics-access-driver.md)|[dBASE](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[Zugriff](../../odbc/microsoft/sqltables-access-driver.md)|[dBASE](../../odbc/microsoft/sqltables-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqltables-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)|  
|[SQLTransact](../../odbc/reference/syntax/sqltransact-function.md)|[Zugriff](../../odbc/microsoft/sqltransact-access-driver.md)|[dBASE](../../odbc/microsoft/sqltransact-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqltransact-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 Die folgenden Themen enthalten Hinweise zum ODBC-Funktionen. Diese Hinweise gelten für alle ODBC-Desktop-Datenbanktreiber.  
  
-   [SQLGetData (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)  
  
-   [SQLGetStmtOption (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)  
  
-   [SQLMoreResults (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)  
  
-   [SQLPrepare (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)  
  
-   [SQLProcedures (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)  
  
-   [SQLSetCursorName (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)  
  
-   [SQLSetPos (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)  
  
-   [SQLSetScrollOptions (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)  
  
-   [SQLSetStmtOption (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)  
  
-   [SQLSpecialColumns (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)
