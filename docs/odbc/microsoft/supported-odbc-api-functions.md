---
description: Unterstützte ODBC-API-Funktionen
title: Unterstützte ODBC-API-Funktionen | Microsoft-Dokumentation
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
ms.openlocfilehash: 61dca7de4a9a532789a2b448fad812ae3daf76ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500093"
---
# <a name="supported-odbc-api-functions"></a>Unterstützte ODBC-API-Funktionen
Der Zweck der Durchsetzung besteht darin, die Anwendung darüber zu informieren, welche Features Ihnen vom Treiber zur Verfügung stehen. Die Microsoft ODBC Desktop-Datenbanktreiber unterstützen alle Kern-und Level 1-Funktionen.  
  
 Weitere Informationen zu den Konformitätsstufen für Funktionen und Grammatik finden Sie unter [Konformitätsstufen](../../odbc/reference/develop-app/conformance-levels.md) in der *ODBC-Programmier Referenz*.  
  
 Die Unterstützung von ODBC-API-Funktionen kann vom verwendeten Treiber abhängen. In der folgenden Tabelle wird die Unterstützung für-Funktionen zusammengefasst. Die Spalte ganz links enthält einen Link zur allgemeinen Verweisseite für jede Funktion. Diese Referenzseiten sind im Abschnitt [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md) unter [ODBC Programmer es Reference](../../odbc/reference/odbc-programmer-s-reference.md)alphabetisch aufgelistet. Die Spalten auf der rechten Seite enthalten Links zu treiberspezifischen Notizen zu den einzelnen unterstützten Funktionen. Diese treiberspezifischen Themen sind im Abschnitt "andere Programmier Details" für jeden Treiber aufgeführt. Wenn die gleichen Hinweise zu einer Funktion auf alle ODBC-Desktop-Datenbanktreiber zutreffen, bietet die Spalte ganz rechts einen Link zu einem Thema, das die Unterstützung der Desktop-Datenbanktreiber für diese Funktion zusammenfasst. Diese Themen sind am Ende des aktuellen Abschnitts ("unterstützte ODBC-API-Funktionen") aufgeführt.  
  
|ODBC-Funktion|Zugriff auf Treiber spezifische Notizen|dBase-Treiber spezifische Notizen|Paradox-Treiber spezifische Notizen|Treiber spezifische Hinweise zu Textdateien|Excel-Treiber spezifische Notizen|Hinweise, die für alle Treiber relevant sind|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)|[zugreifen](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[dBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[zugreifen](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[dBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[zugreifen](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[dBASE](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[zugreifen](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[dBASE](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[zugreifen](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[dBASE](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)|
|[SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)|  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[zugreifen](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[dBASE](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[zugreifen](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)||||||  
|['SQLProcedures'](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[zugreifen](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[dBASE](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[SQLSetPos](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|['SQLSpecialColumns'](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[Alle Treiber](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|['SQLStatistics'](../../odbc/reference/syntax/sqlstatistics-function.md)|[zugreifen](../../odbc/microsoft/sqlstatistics-access-driver.md)|[dBASE](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[zugreifen](../../odbc/microsoft/sqltables-access-driver.md)|[dBASE](../../odbc/microsoft/sqltables-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqltables-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)|  
|[SQLtransact](../../odbc/reference/syntax/sqltransact-function.md)|[zugreifen](../../odbc/microsoft/sqltransact-access-driver.md)|[dBASE](../../odbc/microsoft/sqltransact-dbase-driver.md)|[Gewissen](../../odbc/microsoft/sqltransact-paradox-driver.md)|[Textdatei](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 Die folgenden Themen enthalten Hinweise zu ODBC-Funktionen. Diese Hinweise gelten für alle ODBC Desktop-Datenbanktreiber.  
  
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
