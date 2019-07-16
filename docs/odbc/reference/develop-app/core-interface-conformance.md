---
title: Core-Schnittstellenübereinstimmung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 02e8aabf808ebf11f2e241fc7d330f794dbb0112
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002116"
---
# <a name="core-interface-conformance"></a>Schnittstellenübereinstimmung auf Kernebene
Alle ODBC-Treiber müssen mindestens ein Kernebenen-aufweisen schnittstellenübereinstimmung. Da die Funktionen der Kernebene diejenigen, die durch die meisten generischen interoperablen Anwendungen erforderlich sind, kann solche Anwendungen der Treiber verwenden. Die Funktionen der Kernebene entsprechen auch auf die Funktionen, die in der ISO-CLI-Spezifikation definiert und auf die nonoptional Funktionen, die in der Open Group-CLI-Spezifikation definiert. Ein Kernebenen-Schnittstelle-konformen ODBC-Treiber kann die Anwendung Folgendes tun:  
  
-   Zuordnen und freigeben aller Arten von Handles, durch den Aufruf **SQLAllocHandle** und **SQLFreeHandle**.  
  
-   Verwenden Sie alle Arten von der **SQLFreeStmt** Funktion.  
  
-   Binden von Resultsetspalten, durch den Aufruf **SQLBindCol**.  
  
-   Behandeln von dynamischen Parametern, einschließlich der Arrays von Parametern, die in der Eingabe-Richtung nur durch den Aufruf **SQLBindParameter** und **SQLNumParams**. (Parameter in der Ausgabe Richtung sind 203 in feature [Ebene-2-Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Geben Sie einen Bind-Offset.  
  
-   Verwenden Sie das Data-at-Execution-Dialogfeld, das im Zusammenhang mit Aufrufen von **SQLParamData** und **SQLPutData**.  
  
-   Verwalten von Cursorn und Cursornamen, durch den Aufruf **SQLCloseCursor**, **SQLGetCursorName**, und **SQLSetCursorName**.  
  
-   Erhalten Sie Zugriff auf die Beschreibung (Metadaten) des Resultsets, durch den Aufruf **SQLColAttribute**, **SQLDescribeCol**, **SQLNumResultCols**, und **SQLRowCount** . (Verwendung dieser Funktionen auf Spaltennummer 0 zum Abrufen von Metadaten für Lesezeichen 204 in Features sind [Ebene-2-Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Wörterbuch mit den Daten, Abfragen, durch den Aufruf der Katalogfunktionen **SQLColumns**, **SQLGetTypeInfo**, **SQLStatistics**, und **SQLTables**.  
  
     Der Treiber ist nicht für die Unterstützung von mehrteiliger Namen der Datenbanktabellen und-Sichten erforderlich. (Weitere Informationen finden Sie unter 101-Feature in [Ebene-1-Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/level-1-interface-conformance.md) und Funktionen Sie 201 in [Ebene-2-Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/level-2-interface-conformance.md).) Es gibt jedoch bestimmte Funktionen der SQL-92-Spezifikation, z. B. Spalte Qualifikation und Namen von Indizes, syntaktisch mit mehrteiligen Namen. Die vorhandene Liste der ODBC-Funktionen ist nicht vorgesehen, neue Optionen in dieser Aspekte der SQL-92 einführen.  
  
-   Verwalten von Datenquellen und Verbindungen durch den Aufruf **SQLConnect**, **SQLDataSources**, **SQLDisconnect**, und **SQLDriverConnect**. Abrufen von Informationen auf den Treiber, unabhängig davon, welche ODBC level sie, durch den Aufruf unterstützen **SQLDrivers**.  
  
-   Vorbereiten und Ausführen von SQL-Anweisungen, durch den Aufruf **SQLExecDirect**, **SQLExecute**, und **SQLPrepare**.  
  
-   Rufen Sie eine Zeile eines Resultsets oder mehrere Zeilen, nur vorwärts durch Aufrufen von **SQLFetch** oder durch Aufrufen von **SQLFetchScroll** mit der *FetchOrientation* Argument Legen Sie auf SQL_FETCH_NEXT.  
  
-   Abrufen eine ungebundene Spalte in Teilen, durch den Aufruf **SQLGetData**.  
  
-   Abrufen der aktuellen Werte aller Attribute, durch Aufrufen von **SQLGetConnectAttr**, **SQLGetEnvAttr**, und **SQLGetStmtAttr**, und legen Sie alle Attribute auf ihre Standardwerte zurück und bestimmte Attribute auf benutzerdefinierte Werte festlegen, durch den Aufruf **SQLSetConnectAttr**, **SQLSetEnvAttr**, und **SQLSetStmtAttr**.  
  
-   Bearbeiten von bestimmten Feldern der Deskriptoren, durch den Aufruf **SQLCopyDesc**, **SQLGetDescField**, **SQLGetDescRec**, **SQLSetDescField**, und **SQLSetDescRec**.  
  
-   Abrufen von Diagnoseinformationen, durch den Aufruf **SQLGetDiagField** und **SQLGetDiagRec**.  
  
-   Treiber-Funktionen, durch den Aufruf erkennt **SQLGetFunctions** und **SQLGetInfo**. Darüber hinaus erkennt das Ergebnis Ersetzungen, die an eine SQL-Anweisung vorgenommen werden, bevor sie mit der Datenquelle, durch den Aufruf gesendet wird **SQLNativeSql**.  
  
-   Verwenden Sie die Syntax der **SQLEndTran** Commit eine Transaktion. Ein Kernebenen-Treiber muss "true" Transaktionen nicht unterstützt; die Anwendung kann nicht aus diesem Grund für das SQL_ATTR_AUTOCOMMIT-Verbindungsattribut SQL_ROLLBACK noch SQL_AUTOCOMMIT_OFF angeben. (Weitere Informationen finden Sie unter Feature 109 [Ebene-2-Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Rufen Sie **SQLCancel** um das Dialogfeld "Data-at-Execution" abzubrechen und im multithread-Umgebungen zum Abbrechen einer ODBC-Ausführung in einem anderen Thread. Unterstützung für asynchrone Ausführung von Funktionen noch die Verwendung des Core-Level-Interface-Standards nicht anordnet **SQLCancel** zum Abbrechen von einer ODBC-Funktion, die asynchron ausgeführt wird. Weder für die Plattform als auch für den ODBC-Treiber muss für den Treiber voneinander unabhängige Aktivitäten zur gleichen Zeit durchführen multithread sein. Allerdings muss der ODBC-Treiber in multithread-Umgebungen threadsicher sein. Serialisierung von Anforderungen aus der Anwendung ist eine konforme Möglichkeit zum Implementieren dieser Spezifikation ist, obwohl es schwerwiegende Leistungsprobleme erstellen kann.  
  
-   Abrufen der SQL_BEST_ROWID Zeile identifizieren-Spalte mit Tabellen, durch den Aufruf **SQLSpecialColumns**. (Unterstützung für SQL_ROWVER 208 in Features sind [Ebene-2-Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
    > [!IMPORTANT]  
    >  ODBC-Treiber müssen die Funktionen in der Konformitätsgrad des Core-Schnittstelle implementieren.
