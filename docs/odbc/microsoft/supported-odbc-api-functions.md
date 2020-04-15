---
title: Unterstützte ODBC-API-Funktionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec6ceaf57d8fe3c5325f85a9644cf4c8016663e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304101"
---
# <a name="supported-odbc-api-functions"></a>Unterstützte ODBC-API-Funktionen
Der Zweck des Abgleichs besteht darin, die Anwendung darüber zu informieren, welche Funktionen dem Treiber vom Treiber zur Verfügung stehen. Die Microsoft ODBC Desktop-Datenbanktreiber unterstützen alle Core- und Level 1-Funktionen.  
  
 Weitere Informationen zu Konformitätsstufen für Funktionen und Grammatik finden Sie unter [Konformitätsstufen](../../odbc/reference/develop-app/conformance-levels.md) in der *ODBC-Programmiererreferenz*.  
  
 Die Unterstützung von ODBC-API-Funktionen kann vom verwendeten Treiber abhängen. Die folgende Tabelle fasst die Unterstützung für Funktionen zusammen. Die linke Spalte stellt einen Link zur allgemeinen Referenzseite für jede Funktion bereit. Diese Referenzseiten werden alphabetisch im Abschnitt [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md) unter [ODBC Programmer es Reference](../../odbc/reference/odbc-programmer-s-reference.md)aufgelistet. Die Spalten auf der rechten Seite enthalten Links zu treiberspezifischen Hinweisen zu jeder unterstützten Funktion. Diese treiberspezifischen Themen sind im Abschnitt "Andere Programmierdetails" für jeden Treiber aufgeführt. Wenn die gleichen Bemerkungen zu einer Funktion für alle ODBC Desktop-Datenbanktreiber gelten, stellt die rechte Spalte einen Link zu einem Thema bereit, das die Unterstützung der Desktopdatenbanktreiber für diese Funktion zusammenfasst. Diese Themen werden am Ende des aktuellen Abschnitts ("Unterstützte ODBC-API-Funktionen") aufgeführt.  
  
|ODBC-Funktion|Zugriff auf treiberspezifische Hinweise|dBASE Treiberspezifische Hinweise|Paradox Driver-spezifische Hinweise|Textdateitreiberspezifische Notizen|Excel-Treiberspezifische Notizen|Hinweise, die für alle Fahrer relevant sind|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)|[zugreifen](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[Dbase](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[zugreifen](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[Dbase](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[zugreifen](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[Dbase](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[zugreifen](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[Dbase](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[zugreifen](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[Dbase](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)|
|[SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)|  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[zugreifen](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[Dbase](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[zugreifen](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)||||||  
|['SQLProcedures'](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[zugreifen](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[Dbase](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[SQLSetPos](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[SQLSetScrollOptionen](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|['SQLSpecialColumns'](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|['SQLStatistics'](../../odbc/reference/syntax/sqlstatistics-function.md)|[zugreifen](../../odbc/microsoft/sqlstatistics-access-driver.md)|[Dbase](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[zugreifen](../../odbc/microsoft/sqltables-access-driver.md)|[Dbase](../../odbc/microsoft/sqltables-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqltables-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)|  
|[SQLTransact](../../odbc/reference/syntax/sqltransact-function.md)|[zugreifen](../../odbc/microsoft/sqltransact-access-driver.md)|[Dbase](../../odbc/microsoft/sqltransact-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqltransact-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 Die folgenden Themen enthalten Anmerkungen zu ODBC-Funktionen. Diese Bemerkungen gelten für alle ODBC Desktop-Datenbanktreiber.  
  
-   [SQLGetData (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)  
  
-   [SQLGetStmtOption(Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)  
  
-   [SQLMoreResults (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)  
  
-   [SQLPrepare (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)  
  
-   [SQLProcedures (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)  
  
-   [SQLSetCursorName (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)  
  
-   [SQLSetPos (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)  
  
-   [SQLSetScrollOptions (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)  
  
-   [SQLSetStmtOption (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)  
  
-   [SQLSpecialColumns (Desktop-Datenbanktreiber)](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)
