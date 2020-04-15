---
title: Neue Funktionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b40803dac6c9f296043a8dcac50f9bc69036875a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302398"
---
# <a name="new-features"></a>Neue Funktionen
Die folgende neue Funktionalität wurde in ODBC *3.x*eingeführt. Eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, kann diese Funktionalität nicht verwenden. Der ODBC *3.x* Treiber-Manager weist diese Features nicht zu, wenn er mit einem ODBC *2.x-Treiber* arbeitet.  
  
-   Funktionen, die ein Deskriptorhandle als Argument verwenden: **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**und **SQLCopyDesc**.  
  
-   Die Funktionen **SQLSetEnvAttr** und **SQLGetEnvAttr**.  
  
-   Die Verwendung von **SQLAllocHandle** zum Zuweisen eines Deskriptorhandles. (Die Verwendung von **SQLAllocHandle** zum Zuweisen von Umgebungs-, Verbindungs- und Anweisungshandles ist dupliziert, nicht neu.  
  
-   Die Verwendung von **SQLGetConnectAttr** zum Abrufen der SQL_ATTR_AUTO_IPD Verbindungsattribute. (Die Verwendung von **SQLSetConnectAttr** zum Festlegen und **SQLGetConnectAttr** zum Abrufen anderer Verbindungsattribute wird dupliziert, nicht neu, Funktionalität.)  
  
-   Die Verwendung von **SQLSetStmtAttr** zum Festlegen und **SQLGetStmtAttr** zum Abrufen der folgenden Anweisungsattribute. (Die Verwendung von **SQLSetStmtAttr** zum Festlegen und **SQLGetStmtAttr** zum Abrufen anderer Anweisungsattribute ist dupliziert, nicht neu, Funktionalität.)  
  
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
  
-   Die Verwendung von **SQLGetStmtAttr** zum Abrufen der folgenden Anweisungsattribute. (Die Verwendung von **SQLGetStmtAttr** zum Abrufen anderer Anweisungsattribute ist duplizierte Funktionalität, keine neue Funktionalität.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Verwendung des Intervall-C-Datentyps, des Intervalls SQL-Datentypen, der BIGINT C-Datentypen und der SQL_C_NUMERIC Datenstruktur.  
  
-   Zeilenweise Bindung von Parametern.  
  
-   Offset-basierte Lesezeichen-Abrufe, z. B. das Aufrufen von **SQLFetchScroll** mit einem *FetchOrientation-Argument* von SQL_FETCH_BOOKMARK und Angeben eines anderen Offsets als 0.  
  
-   **SQLFetch** gibt das Zeilenstatusarray, die Anzahl der abgerufenen Zeilen, das Abrufen mehrerer Zeilen, das Zusammenführen von Aufrufen mit **SQLFetchScroll**und das Mischen von Aufrufen mit **SQLBulkOperations** oder **SQLSetPos**zurück. Weitere Informationen finden Sie im nächsten Abschnitt [BlockCursors, Scrollable Cursors und Backward Compatibility for ODBC 3.x Applications](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Benannte Parameter.  
  
-   Alle ODBC *3.x*-spezifischen **SQLGetInfo-Optionen.** (Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, die SQL_XXX_CURSOR_ATTRIBUTES1-Informationstypen aufruft, die mehrere ODBC *2.x-Informationstypen* ersetzt haben, können einige der Informationen zuverlässig, aber einige möglicherweise unzuverlässig sein. Weitere Informationen finden Sie unter [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Binden Sie Offsets.  
  
-   Aktualisieren, Aktualisieren und Löschen nach Lesezeichen (durch Aufruf von **SQLBulkOperations**).  
  
-   Aufrufen von **SQLBulkOperations** oder **SQLSetPos** im S5-Status.  
  
-   Die ROW_NUMBER und COLUMN_NUMBER Felder im Diagnosedatensatz (die von den Ersatzfunktionen **SQLGetDiagField** oder **SQLGetDiagRec**abgerufen werden müssen).  
  
-   Ungefähre Zeilenanzahl.  
  
-   Warnungsinformationen (SQL_ROW_SUCCESS_WITH_INFO aus **SQLFetchScroll**).  
  
-   Lesezeichen variabler Länge.  
  
-   Erweiterte Fehlerinformationen für Arrays von Parametern.  
  
-   Alle neuen Spalten in den Resultsets, die von den Katalogfunktionen zurückgegeben werden.  
  
-   Verwendung von **SQLDescribeCol** und **SQLColAttribute** in Spalte 0.  
  
-   Verwendung beliebiger ODBC *3.x*-spezifischer Spaltenattribute in einem Aufruf von **SQLColAttribute**.  
  
-   Verwendung mehrerer Umgebungshandles.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x-Anwendungen](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)
