---
title: Fehler Codes der ODBC-Cursor Bibliothek | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], error codes
- error codes [ODBC], cursor library
- ODBC cursor library [ODBC], error codes
ms.assetid: 9713480e-8744-4f37-a630-20871590d4a1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a3fb86e1332e3b7e4d89003ccf6421151e5d9cec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100670"
---
# <a name="odbc-cursor-library-error-codes"></a>ODBC-Cursorbibliothek – Fehlercodes
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version der Microsoft Data Access-Komponente entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Verwenden Sie stattdessen Treiber-und Servercursorn.  
  
 Die ODBC-Cursor Bibliothek gibt zusätzlich zu den in der [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)aufgeführten Sqlstates die folgenden Sqlstates zurück.  
  
> [!NOTE]  
>  Die Cursor Bibliothek sortiert keine Statusdaten Sätze. Treiber-Manager und ODBC 3. *x* -Treiber sind für das Anordnen von Statusdaten Sätzen verantwortlich.  
  
|SQLSTATE|BESCHREIBUNG|Kann zurückgegeben werden von|  
|--------------|-----------------|--------------------------|  
|01000|Der Cursor kann nicht aktualisiert werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Die Cursor Bibliothek wird nicht verwendet. Fehler beim Laden.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Die Cursor Bibliothek wird nicht verwendet. Unzureichende Treiberunterstützung.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Die Cursor Bibliothek wird nicht verwendet. Versions Konflikt mit Treiber-Manager.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Der Treiber hat SQL_SUCCESS_WITH_INFO zurückgegeben. Die Warnmeldung ist verloren gegangen.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Allgemeiner Fehler: der Datei Puffer kann nicht erstellt werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: aus dem Datei Puffer konnte nicht gelesen werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: in den Datei Puffer kann nicht geschrieben werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: der Datei Puffer kann nicht geschlossen oder entfernt werden.|**SQLFreeHandle**<br /><br /> **'SQLFreeStmt'**|  
|SL001|Die positionierte Anforderung kann nicht ausgeführt werden, da keine durchsuchbaren Spalten gebunden wurden.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Die positionierte Anforderung konnte nicht ausgeführt werden, da das Resultset durch eine Joinbedingung erstellt wurde.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Der gebundene Puffer überschreitet die maximale Segmentgröße.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Das Resultset wurde nicht von einer **Select** -Anweisung generiert.|**SQLGetData**|  
|SL005|Die **Select** -Anweisung enthält eine Group By-Klausel.|**SQLGetData**|  
|SL006|Parameter Arrays werden bei positionierten Anforderungen nicht unterstützt.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData** ist für einen Vorwärts Cursor (nicht gepuffert) nicht zulässig.|**SQLGetData**|  
|SL009|Vor dem Aufrufen von **SQLFetch** oder **SQLFetchScroll**wurden keine Spalten gebunden.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** hat beim Versuch, eine Bindung an einen internen Puffer herzustellen, SQL_ERROR zurückgegeben.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|Die Anweisungs Option ist nur gültig, nachdem **SQLFetch** oder **SQLFetchScroll**aufgerufen wurde.|**'SQLGetStmtAttr'**|  
|SL012|Anweisungs Bindungen können nicht geändert werden, während ein Cursor geöffnet ist.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **'SQLFreeStmt'**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Eine positionierte Anforderung wurde ausgegeben, und es wurden nicht alle Felder der Spalten Anzahl gepuffert.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** und **SQLFetchScroll** können nicht gemischt werden.|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
