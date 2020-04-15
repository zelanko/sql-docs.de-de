---
title: Core-Schnittstellenkonformität | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- core-level interface conformance levels [ODBC]
ms.assetid: aaaa864a-6477-45ff-a50a-96d8db66a252
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 886ded1cd79b35488c0d47df3dbd8055dc6a8016
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302132"
---
# <a name="core-interface-conformance"></a>Schnittstellenübereinstimmung auf Kernebene
Alle ODBC-Treiber müssen mindestens eine Schnittstellenkonformität auf Core-Ebene aufweisen. Da die Funktionen in der Core-Ebene die Funktionen sind, die von den meisten generischen interoperablen Anwendungen benötigt werden, kann der Treiber mit solchen Anwendungen arbeiten. Die Features in der Core-Ebene entsprechen auch den in der ISO CLI-Spezifikation definierten Features und den nicht optionalen Features, die in der Open Group CLI-Spezifikation definiert sind. Ein Schnittstellenkonformer ODBC-Treiber auf Core-Ebene ermöglicht der Anwendung, folgendes zu tun:  
  
-   Zuweisen und Freiwerden aller Arten von Handles, indem Sie **SQLAllocHandle** und **SQLFreeHandle**aufrufen.  
  
-   Verwenden Sie alle Formen der **SQLFreeStmt-Funktion.**  
  
-   Binden Sie Resultsetspalten, indem Sie **SQLBindCol**aufrufen.  
  
-   Behandeln Sie dynamische Parameter, einschließlich Arrays von Parametern, nur in Eingaberichtung, indem Sie **SQLBindParameter** und **SQLNumParams**aufrufen. (Parameter in Ausgaberichtung sind Feature 203 in [Level 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Geben Sie einen Bindungsoffset an.  
  
-   Verwenden Sie das Dialogfeld "Data-at-Execution" mit Aufrufen von **SQLParamData** und **SQLPutData**.  
  
-   Verwalten von Cursorn und Cursornamen durch Aufrufen von **SQLCloseCursor**, **SQLGetCursorName**und **SQLSetCursorName**.  
  
-   Erhalten Sie Zugriff auf die Beschreibung (Metadaten) von Resultsets, indem Sie **SQLColAttribute**, **SQLDescribeCol**, **SQLNumResultCols**und **SQLRowCount**aufrufen. (Die Verwendung dieser Funktionen in der Spalte Nummer 0 zum Abrufen von Lesezeichenmetadaten ist Feature 204 in [Level 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Abfragen Sie das Datenwörterbuch, indem Sie die Katalogfunktionen **SQLColumns**, **SQLGetTypeInfo**, **SQLStatistics**und **SQLTables**aufrufen.  
  
     Der Treiber ist nicht erforderlich, um mehrteilige Namen von Datenbanktabellen und -ansichten zu unterstützen. (Weitere Informationen finden Sie unter Feature 101 in [Level 1 Interface Conformance](../../../odbc/reference/develop-app/level-1-interface-conformance.md) und Feature 201 in [Level 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).) Bestimmte Features der SQL-92-Spezifikation, wie die Spaltenqualifizierung und die Namen von Indizes, sind jedoch syntaktisch mit der mehrteiligen Benennung vergleichbar. Die aktuelle Liste der ODBC-Features ist nicht dazu gedacht, neue Optionen in diese Aspekte von SQL-92 einzuführen.  
  
-   Verwalten Sie Datenquellen und Verbindungen, indem Sie **SQLConnect**, **SQLDataSources**, **SQLDisconnect**und **SQLDriverConnect**aufrufen. Erhalten Sie Informationen zu Treibern, unabhängig davon, welche ODBC-Ebene sie unterstützen, indem Sie **SQLDrivers**aufrufen.  
  
-   Vorbereiten und Ausführen von SQL-Anweisungen durch Aufrufen von **SQLExecDirect**, **SQLExecute**und **SQLPrepare**.  
  
-   Rufen Sie eine Zeile eines Resultsets oder mehrere Zeilen nur in Vorwärtsrichtung ab, indem Sie **SQLFetch** aufrufen oder **SQLFetchScroll** aufrufen, wobei das *Argument FetchOrientation* auf SQL_FETCH_NEXT festgelegt ist.  
  
-   Abrufen einer ungebundenen Spalte in Teilen durch Aufrufen von **SQLGetData**.  
  
-   Rufen Sie aktuelle Werte aller Attribute ab, indem Sie **SQLGetConnectAttr**, **SQLGetEnvAttr**und **SQLGetStmtAttr**aufrufen, und legen Sie alle Attribute auf ihre Standardwerte fest, und legen Sie bestimmte Attribute auf nicht standardmäßige Werte fest, indem Sie **SQLSetConnectAttr**, **SQLSetEnvAttr**und **SQLSetStmtAttr**aufrufen.  
  
-   Bearbeiten Sie bestimmte Felder von Deskriptoren, indem Sie **SQLCopyDesc**, **SQLGetDescField**, **SQLGetDescRec**, **SQLSetDescField**und **SQLSetDescRec**aufrufen.  
  
-   Abrufen von Diagnoseinformationen durch Aufrufen von **SQLGetDiagField** und **SQLGetDiagRec**.  
  
-   Erkennen von Treiberfunktionen durch Aufrufen von **SQLGetFunctions** und **SQLGetInfo**. Erkennen Sie außerdem das Ergebnis von Textersetzungen, die an einer SQL-Anweisung vorgenommen wurden, bevor sie an die Datenquelle gesendet wird, indem Sie **SQLNativeSql**aufrufen.  
  
-   Verwenden Sie die Syntax von **SQLEndTran,** um eine Transaktion zu übertragen. Ein Core-Level-Treiber muss keine echten Transaktionen unterstützen. Daher kann die Anwendung weder SQL_ROLLBACK noch SQL_AUTOCOMMIT_OFF für das SQL_ATTR_AUTOCOMMIT-Verbindungsattribut angeben. (Weitere Informationen finden Sie unter Feature 109 in [Level 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Rufen Sie **SQLCancel auf,** um das Dialogfeld "Daten bei Ausführung" und in Multithreadumgebungen eine ODBC-Funktion abzubrechen, die in einem anderen Thread ausgeführt wird. Die Schnittstellenkonformität auf Core-Ebene erfordert weder Unterstützung für die asynchrone Ausführung von Funktionen noch die Verwendung von **SQLCancel,** um eine ODBC-Funktion abzubrechen, die asynchron ausgeführt wird. Weder die Plattform noch der ODBC-Treiber müssen Multithread sein, damit der Fahrer gleichzeitig unabhängige Aktivitäten durchführen kann. In Multithreadumgebungen muss der ODBC-Treiber jedoch threadsicher sein. Die Serialisierung von Anforderungen aus der Anwendung ist eine konforme Möglichkeit, diese Spezifikation zu implementieren, auch wenn dies zu schwerwiegenden Leistungsproblemen führen kann.  
  
-   Rufen Sie die SQL_BEST_ROWID Zeilenidentifizierende Spalte von Tabellen ab, indem Sie **SQLSpecialColumns**aufrufen. (Unterstützung für SQL_ROWVER ist Feature 208 in [Level 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
    > [!IMPORTANT]  
    >  ODBC-Treiber müssen die Funktionen in der Core-Schnittstellenkonformitätsebene implementieren.
