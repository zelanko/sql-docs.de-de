---
title: Konformität der Kernschnittstelle | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302132"
---
# <a name="core-interface-conformance"></a>Schnittstellenübereinstimmung auf Kernebene
Alle ODBC-Treiber müssen mindestens eine Schnittstellen Übereinstimmung auf Kern Ebene aufweisen. Da die Features in der kernstufe diejenigen sind, die für die meisten generischen interoperablen Anwendungen erforderlich sind, kann der Treiber mit solchen Anwendungen arbeiten. Die Features auf der kernstufe entsprechen auch den in der ISO CLI-Spezifikation definierten Features und den nicht optionalen Features, die in der CLI-Spezifikation der Open-Gruppe definiert sind. Mit einem Schnittstellen kompatiblen ODBC-Treiber auf Kern Ebene kann die Anwendung Folgendes ausführen:  
  
-   Sie können alle Arten von Handles zuordnen und freigeben, indem Sie **SQLAllocHandle** und **SQLFreeHandle**aufrufen.  
  
-   Verwenden Sie alle Formen der **SQLFreeStmt** -Funktion.  
  
-   Binden von Resultsetspalten durch Aufrufen von **SQLBindCol**.  
  
-   Behandeln von dynamischen Parametern, einschließlich Arrays von Parametern, in der Eingabe Richtung nur durch Aufrufen von **SQLBindParameter** und **sqlnumparameterams**. (Parameter in der Ausgabe Richtung sind die Funktion 203 in der [Schnittstellen Konformität der Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Geben Sie einen Bindungs Offset an.  
  
-   Verwenden Sie das Dialogfeld Data-at-Execution mit Aufrufen von **SQLParamData** und **SQLPutData**.  
  
-   Verwalten von Cursorn und Cursor Namen durch Aufrufen von **SQLCloseCursor**, **SQLGetCursorName**und **SQLSetCursorName**.  
  
-   Durch den Aufruf von **SQLColAttribute**, **SQLDescribeCol**, **SQLNumResultCols**und **SQLRowCount**erhalten Sie Zugriff auf die Beschreibung (Metadaten) von Resultsets. (Die Verwendung dieser Funktionen für die Spaltennummer 0 zum Abrufen von Lesezeichen Metadaten ist die Funktion 204 in der [Schnittstellen Konformität der Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Fragen Sie das Datenwörterbuch ab, indem Sie die Katalog Funktionen **SQLColumns**, **SQLGetTypeInfo**, **SQLStatistics**und **SQLTables**aufrufen.  
  
     Der Treiber ist nicht erforderlich, um mehrteilige Namen von Datenbanktabellen und-Sichten zu unterstützen. (Weitere Informationen finden Sie unter Feature 101 in der Schnittstellen Konformität der [Ebene 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md) und Feature 201 in der [Schnittstellen Konformität der Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).) Bestimmte Funktionen der SQL-92-Spezifikation, wie z. b. die Spalten Qualifizierung und Namen von Indizes, sind jedoch syntaktisch mit der mehrteiligen Benennung vergleichbar. Die aktuelle Liste der ODBC-Funktionen ist nicht für die Einführung neuer Optionen in diese Aspekte von SQL-92 gedacht.  
  
-   Verwalten von Datenquellen und Verbindungen durch Aufrufen von **SQLCONNECT**, **SQLDataSources**, **SQLDisconnect**und **SQLDriverConnect**. Abrufen von Informationen zu Treibern, unabhängig davon, welche ODBC-Ebene Sie unterstützen, durch Aufrufen von **SQLDrivers**.  
  
-   Vorbereiten und Ausführen von SQL-Anweisungen durch Aufrufen von **SQLExecDirect**, **SQLExecute**und **SQLPrepare**.  
  
-   Abrufen einer Zeile eines Resultsets oder mehrerer Zeilen in Vorwärtsrichtung, durch Aufrufen von **SQLFetch** oder durch Aufrufen von **SQLFetchScroll** , wobei das *FetchOrientation* -Argument auf SQL_FETCH_NEXT festgelegt ist.  
  
-   Abrufen einer ungebundenen Spalte in Teilen, indem **SQLGetData**aufgerufen wird.  
  
-   Rufen Sie die aktuellen Werte aller Attribute durch Aufrufen von **SQLGetConnectAttr**, **SQLGetEnvAttr**und **SQLGetStmtAttr**ab, legen Sie alle Attribute auf ihre Standardwerte fest, und legen Sie bestimmte Attribute auf nicht standardmäßige Werte fest, indem Sie **SQLSetConnectAttr**, **SQLSetEnvAttr**und **sqlsetstmt**  
  
-   Bearbeiten bestimmter Deskriptorfelder durch Aufrufen von **SQLCopyDesc**, **SQLGetDescField**, **SQLGetDescRec**, **SQLSetDescField**und **SQLSetDescRec**.  
  
-   Rufen Sie Diagnoseinformationen ab, indem Sie **SQLGetDiagField** und **SQLGetDiagRec**aufrufen.  
  
-   Erkennen von Treiberfunktionen durch Aufrufen von **SQLGetFunctions** und **SQLGetInfo**. Sie können auch das Ergebnis von Text Ersetzungen ermitteln, die vor dem Senden an die Datenquelle durch Aufrufen von **SQLNativeSql**an eine SQL-Anweisung vorgenommen wurden.  
  
-   Verwenden Sie die Syntax von **SQLEndTran** , um einen Commit für eine Transaktion durchführen. Ein Treiber auf Kern Ebene muss keine echten Transaktionen unterstützen. Daher kann die Anwendung weder SQL_ROLLBACK noch SQL_AUTOCOMMIT_OFF für das SQL_ATTR_AUTOCOMMIT Connection-Attribut angeben. (Weitere Informationen finden Sie unter Feature 109 in der [Schnittstellen Konformität der Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Rufen Sie **SQLCancel** auf, um das Dialogfeld Data-at-Execution abzubrechen und in Multithreadumgebungen eine ODBC-Funktion abzubrechen, die in einem anderen Thread ausgeführt wird. Die Schnittstellen Konformität auf Kern Ebene unterstützt weder die asynchrone Ausführung von Funktionen noch die Verwendung von **SQLCancel** , um eine asynchrone Ausführung einer ODBC-Funktion abzubrechen. Weder die Plattform noch der ODBC-Treiber benötigen Multithread, damit der Treiber unabhängige Aktivitäten gleichzeitig durchführen muss. In Umgebungen mit mehreren Threads muss der ODBC-Treiber jedoch Thread sicher sein. Die Serialisierung von Anforderungen von der Anwendung ist eine konforme Methode zur Implementierung dieser Spezifikation, auch wenn Sie schwerwiegende Leistungsprobleme verursachen kann.  
  
-   Rufen Sie die SQL_BEST_ROWID Zeilen identifizierende Spalte der Tabellen ab, indem Sie **SQLSpecialColumns**aufrufen. (Unterstützung für SQL_ROWVER ist die Funktion 208 in der [Schnittstellen Konformität der Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
    > [!IMPORTANT]  
    >  ODBC-Treiber müssen die Funktionen in der Kern Schnittstellen-Konformitäts Ebene implementieren.
