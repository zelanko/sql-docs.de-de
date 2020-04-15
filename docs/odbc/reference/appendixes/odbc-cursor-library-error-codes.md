---
title: ODBC Cursor Library Fehlercodes | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c263ce53c41546e63dc2a830d3db3b903e2e3515
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301431"
---
# <a name="odbc-cursor-library-error-codes"></a>ODBC-Cursorbibliothek – Fehlercodes
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Microsoft Data Access Component entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Verwenden Sie stattdessen Treiber- und Servercursor.  
  
 Die ODBC-Cursorbibliothek gibt zusätzlich zu den in [ODBC API Reference](../../../odbc/reference/syntax/odbc-api-reference.md)aufgeführten SQLSTATEs die folgenden SQLSTATEs zurück.  
  
> [!NOTE]  
>  Die Cursorbibliothek ordnet keine Statusdatensätze an. Treiber-Manager und ODBC 3. *x-Treiber* sind für die Reihenfolge von Statusdatensätzen verantwortlich.  
  
|SQLSTATE|Beschreibung|Kann von|  
|--------------|-----------------|--------------------------|  
|01000|Cursor ist nicht aufrüstbar.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Cursorbibliothek wird nicht verwendet. Die Last ist fehlgeschlagen.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Cursorbibliothek wird nicht verwendet. Unzureichende Treiberunterstützung.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Cursorbibliothek wird nicht verwendet. Versionskonflikt mit Driver Manager.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Der Fahrer gab SQL_SUCCESS_WITH_INFO zurück. Die Warnmeldung ist verloren gegangen.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Allgemeiner Fehler: Dateipuffer kann nicht erstellt werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: Aus dem Dateipuffer kann nicht gelesen werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: In den Dateipuffer kann nicht geschrieben werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: Dateipuffer kann nicht geschlossen oder entfernt werden.|**SQLFreeHandle**<br /><br /> **'SQLFreeStmt'**|  
|SL001|Positionierte Anforderung kann nicht ausgeführt werden, da keine durchsuchbaren Spalten gebunden waren.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Die positionierte Anforderung konnte nicht ausgeführt werden, da das Resultset durch eine Join-Bedingung erstellt wurde.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Der gebundene Puffer überschreitet die maximale Segmentgröße.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Das Resultset wurde nicht von einer **SELECT-Anweisung** generiert.|**SQLGetData**|  
|SL005|**SELECT-Anweisung** enthält eine GROUP BY-Klausel.|**SQLGetData**|  
|SL006|Parameterarrays werden bei positionierten Anforderungen nicht unterstützt.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData** ist für einen Vorwärtscursor (nicht gepuffert) nicht zulässig.|**SQLGetData**|  
|SL009|Vor dem Aufruf von **SQLFetch** oder **SQLFetchScroll**wurden keine Spalten gebunden.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** gab SQL_ERROR zurück, während versucht wurde, an einen internen Puffer zu binden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|Die Anweisungsoption ist nur nach dem Aufruf von **SQLFetch** oder **SQLFetchScroll**gültig.|**'SQLGetStmtAttr'**|  
|SL012|Anweisungsbindungen können nicht geändert werden, während ein Cursor geöffnet ist.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **'SQLFreeStmt'**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Eine positionierte Anforderung wurde ausgegeben, und nicht alle Spaltenanzahlfelder wurden gepuffert.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** und **SQLFetchScroll** können nicht gemischt werden.|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
