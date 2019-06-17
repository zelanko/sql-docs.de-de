---
title: Neue Features | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], new features in release
- ODBC drivers [ODBC], backward compatibility
- new features [ODBC]
- compatibility [ODBC], new features in release
- ODBC [ODBC], new features
ms.assetid: a8fcdd00-6cb3-4871-9489-6018b3d0d65f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d425a6896a64f06bf1610ed8f6be87dd60af25d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62658183"
---
# <a name="new-features"></a>Neue Funktionen
Die folgende neue Funktionen wurde in ODBC 3. eingeführt. *x*. Eine ODBC-3.*x* Anwendung mit einer ODBC 2 *.x* Treiber werden nicht in der Lage, diese Funktion zu verwenden. Der ODBC-3.*x* -Treiber-Manager lässt diese Funktionen nicht zuordnen, bei der Arbeit mit einer ODBC 2 *.x* Treiber.  
  
-   Funktionen, die einen Deskriptor akzeptieren behandeln, als Argument: **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**, und **SQLCopyDesc**.  
  
-   Die Funktionen **SQLSetEnvAttr** und **SQLGetEnvAttr**.  
  
-   Die Verwendung von **SQLAllocHandle** ein Deskriptorhandle zuordnen. (Die Verwendung von **SQLAllocHandle** Umgebung, Verbindung und Anweisung Handles zuordnen ist nicht für neue, doppelte Funktionen.)  
  
-   Die Verwendung von **SQLGetConnectAttr** um die Verbindungsattribute SQL_ATTR_AUTO_IPD zu erhalten. (Die Verwendung von **SQLSetConnectAttr** zum Festlegen und **SQLGetConnectAttr** rufen Sie weiteren Verbindungsattributen doppelt vorhandenen, nicht für neue, Funktionalität ist.)  
  
-   Die Verwendung von **SQLSetStmtAttr** zum Festlegen und **SQLGetStmtAttr** zu erhalten, die folgenden Anweisungsattribute. (Die Verwendung von **SQLSetStmtAttr** zum Festlegen und **SQLGetStmtAttr** um erhalten, andere Anweisungsattribute doppelt vorhandenen, nicht für neue, Funktionalität ist.)  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_ENABLE_AUTO_IPD  
  
     SQL_ATTR_FETCH_BOOKMARK_PTR  
  
     SQL_ATTR_BIND_OFFSET  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     SQL_DESC_PARAM_STATUS_PTR  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR  
  
     SQL_ATTR_PARAMSET_SIZE  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_ROW_ARRAY_SIZE  
  
-   Die Verwendung von **SQLGetStmtAttr** um die folgenden Anweisungsattribute abzurufen. (Die Verwendung von **SQLGetStmtAttr** andere Anweisung abzurufenden Attribute doppelte Funktionen, die keine neuen Funktionen ist.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Verwendung von der C-Intervall-Datentyp, der Interval-SQL-Datentypen, die BIGINT-C-Datentypen und die Datenstruktur SQL_C_NUMERIC.  
  
-   Die zeilenweise Bindung von Parametern.  
  
-   Offset-basierte Lesezeichen abruft, wie ein Aufruf **SQLFetchScroll** mit einem *FetchOrientation* Argument von SQL_FETCH_BOOKMARK und Angeben eines Offsets als 0.  
  
-   **SQLFetch** Zurückgeben der zeilenstatusarray, Anzahl der Zeilen abgerufen, Abrufen mehrerer Zeilen, die Vermischung Aufrufe mit **SQLFetchScroll**, und die Vermischung Aufrufe mit **SQLBulkOperations** oder **SQLSetPos**. Weitere Informationen finden Sie im nächsten Abschnitt [Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x-Anwendungen](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Benannte Parameter.  
  
-   Alle von der ODBC-3. *x*-spezifische **SQLGetInfo** Optionen. (Bei einer ODBC-3.*x* Anwendung mit einer ODBC 2.*x* ruft der Treiber die SQL_XXX_CURSOR_ATTRIBUTES1 Informationstypen, die mehrere ODBC 2. ersetzt haben. *X* Informationstypen, einige der Informationen sind möglicherweise in der zuverlässigen, aber einige möglicherweise unzuverlässig. Weitere Informationen finden Sie unter [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Binden Sie Offsets an.  
  
-   Aktualisieren, aktualisieren und Löschen von Lesezeichen (durch einen Aufruf von **SQLBulkOperations**).  
  
-   Aufrufen von **SQLBulkOperations** oder **SQLSetPos** im Zustand "S5".  
  
-   Die ROW_NUMBER und Zeile/relative-Felder, in dem Diagnosedatensatz (die von den Ersatzfunktionen abgerufen werden müssen **SQLGetDiagField** oder **SQLGetDiagRec**).  
  
-   Ungefähre Zeilenanzahl.  
  
-   Warnung (SQL_ROW_SUCCESS_WITH_INFO aus **SQLFetchScroll**).  
  
-   Lesezeichen mit variabler Länge.  
  
-   Erweiterte Fehlerinformationen für Arrays von Parametern.  
  
-   Alle neuen Spalten in den Resultsets, die durch die Katalogfunktionen zurückgegeben.  
  
-   Verwenden von **SQLDescribeCol** und **SQLColAttribute** für die Spalte 0.  
  
-   Verwendung von jeder ODBC 3. *x*-spezifische Spaltenattribute in einem Aufruf von **SQLColAttribute**.  
  
-   Verwendung von mehreren Umgebungshandles.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x-Anwendungen](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)
