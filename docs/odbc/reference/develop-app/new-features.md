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
ms.openlocfilehash: 74c9a97c2511bc9c9a738b9e63548a9179552489
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086341"
---
# <a name="new-features"></a>Neue Funktionen
Die folgenden neuen Funktionen wurden in ODBC *3. x*eingeführt. Eine ODBC *3. x* -Anwendung, die mit einem ODBC *2. x* -Treiber arbeitet, kann diese Funktion nicht verwenden. Der Treiber-Manager von ODBC *3. x* ordnet diese Features bei der Arbeit mit einem ODBC *2. x* -Treiber nicht zu.  
  
-   Funktionen, die ein Deskriptorhandle als Argument annehmen: **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**und **SQLCopyDesc**.  
  
-   Die Funktionen **sqlsettenvattr** und **SQLGetEnvAttr**.  
  
-   Die Verwendung von **SQLAllocHandle** zum Zuordnen eines Deskriptorhandles. (Die Verwendung von **SQLAllocHandle** , um Umgebungs-, Verbindungs-und Anweisungs Handles zuzuordnen, ist dupliziert, und es werden keine neuen Funktionen verwendet.)  
  
-   Die Verwendung von **SQLGetConnectAttr** , um die SQL_ATTR_AUTO_IPD Verbindungs Attribute zu erhalten. (Durch die Verwendung von **SQLSetConnectAttr** zum Festlegen von und **SQLGetConnectAttr** zum Aufrufen von werden andere Verbindungs Attribute dupliziert, nicht neu.)  
  
-   Die Verwendung von **SQLSetStmtAttr** zum Festlegen von und **SQLGetStmtAttr** , um die folgenden Anweisungs Attribute zu erhalten. (Die Verwendung von **SQLSetStmtAttr** zum Festlegen von und **SQLGetStmtAttr** zum Aufrufen von, andere Anweisungs Attribute werden dupliziert, nicht die neue Funktionalität.)  
  
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
  
-   Die Verwendung von **SQLGetStmtAttr** , um die folgenden Anweisungs Attribute zu erhalten. (Die Verwendung von **SQLGetStmtAttr** , um andere Anweisungs Attribute zu erhalten, ist die doppelte Funktionalität, nicht die neue Funktionalität.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Verwendung des Datentyps Interval c, des Intervalls von SQL-Datentypen, der bigint-c-Datentypen und der SQL_C_NUMERIC Datenstruktur.  
  
-   Zeilenweise Bindung von Parametern.  
  
-   Offset basiertes Lesezeichen abrufen, z. b. das Aufrufen von **SQLFetchScroll** mit einem *FetchOrientation* -Argument von SQL_FETCH_BOOKMARK und das Angeben eines anderen Offsets als 0.  
  
-   **SQLFetch** gibt das Zeilen Status Array, die Anzahl der abgerufenen Zeilen, das Abrufen mehrerer Zeilen, das interagieren von Aufrufen mit **SQLFetchScroll**und das Mischen von Aufrufen mit **SQLBulkOperations** oder **SQLSetPos**zurück. Weitere Informationen finden Sie im nächsten Abschnitt, [Blockcursorn, scrollfähige Cursor und Abwärtskompatibilität für ODBC 3. x-Anwendungen](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Benannte Parameter.  
  
-   Alle ODBC *3. x*-spezifischen **SQLGetInfo** -Optionen. (Wenn eine ODBC *3. x* -Anwendung, die mit einem ODBC *2. x* -Treiber arbeitet, die SQL_XXX_CURSOR_ATTRIBUTES1 Informationstypen aufruft, die mehrere ODBC *2. x* -Informationstypen ersetzt haben, sind einige der Informationen möglicherweise zuverlässig, aber einige sind möglicherweise unzuverlässig. Weitere Informationen finden Sie unter [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Bindungs Offsets.  
  
-   Aktualisieren, aktualisieren und Löschen von Lesezeichen (durch einen **SQLBulkOperations**-Befehl).  
  
-   Aufrufen von ' **SQLBulkOperations** ' oder ' **SQLSetPos** ' im Status ' S5 '.  
  
-   Die Felder ROW_NUMBER und COLUMN_NUMBER im Diagnosedaten Satz (die von den Ersetzungs Funktionen **SQLGetDiagField** oder **SQLGetDiagRec**abgerufen werden müssen).  
  
-   Ungefähre Zeilen Anzahl.  
  
-   Warn Informationen (SQL_ROW_SUCCESS_WITH_INFO von **SQLFetchScroll**).  
  
-   Lesezeichen mit variabler Länge.  
  
-   Erweiterte Fehlerinformationen für Parameter Arrays.  
  
-   Alle neuen Spalten in den Resultsets, die von den-Katalog Funktionen zurückgegeben werden.  
  
-   Verwendung von **SQLDescribeCol** und **SQLColAttribute** für Spalte 0.  
  
-   Verwendung von ODBC *3. x*-spezifischen Spalten Attributen in einem Befehl von **SQLColAttribute**.  
  
-   Verwendung mehrerer Umgebungs Handles.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x-Anwendungen](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)
