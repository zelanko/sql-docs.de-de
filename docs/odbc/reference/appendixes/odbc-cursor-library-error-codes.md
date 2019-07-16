---
title: ODBC Cursor Library-Fehlercodes | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100670"
---
# <a name="odbc-cursor-library-error-codes"></a>ODBC-Cursorbibliothek – Fehlercodes
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Microsoft Data Access Component entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Verwenden Sie stattdessen die Treiber und Server-Cursor.  
  
 Die ODBC-Cursorbibliothek gibt die folgenden SQLSTATEs neben den aufgeführten [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
> [!NOTE]  
>  Die Cursorbibliothek sortiert nicht Statusdatensätze; der Treiber-Manager und die ODBC-3. *x* Treiber sind verantwortlich für die Sortierung der Statusdatensätze.  
  
|SQLSTATE|Beschreibung|Kann von zurückgegeben werden|  
|--------------|-----------------|--------------------------|  
|01000|Cursor kann nicht aktualisiert werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Die Cursorbibliothek nicht verwendet. Fehler beim Laden.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Die Cursorbibliothek nicht verwendet. Nicht genügend treiberunterstützung.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Die Cursorbibliothek nicht verwendet. Versionskonflikt mit Treiber-Manager.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Treiber hat SQL_SUCCESS_WITH_INFO zurückgegeben. Die Warnmeldung ist verloren gegangen.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Allgemeiner Fehler: Erstellen des Dateipuffers nicht möglich.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: Kann nicht aus Dateipuffer gelesen werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: Schreiben in Dateipuffer kann nicht ausgeführt werden.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Allgemeiner Fehler: Kann nicht zu schließen, oder Entfernen des Dateipuffers.|**SQLFreeHandle**<br /><br /> **SQLFreeStmt**|  
|SL001|Positionierte Anforderung kann nicht ausgeführt werden, da keine durchsuchbaren Spalten gebunden wurden.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Positionierte Anforderung konnte nicht ausgeführt werden, da Resultset mit einer Join-Bedingung erstellt wurde.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Gebundenen Puffer überschreitet die maximale Segmentgröße.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Resultset wurde nicht generiert, indem eine **wählen** Anweisung.|**SQLGetData**|  
|SL005|**Wählen Sie** -Anweisung enthält eine GROUP BY-Klausel.|**SQLGetData**|  
|SL006|Parameter-Arrays werden nicht mit positionierte Anforderungen unterstützt.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData** ist nicht in einem Vorwärtscursor (gepuffertes) Cursor zulässig.|**SQLGetData**|  
|SL009|Keine Spalten gebunden wurden, vor dem Aufruf **SQLFetch** oder **SQLFetchScroll**.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** SQL_ERROR zurückgegeben, während der Versuch zum Binden an einen internen Puffer.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|Option-Anweisung ist gültig, nur nach dem Aufruf **SQLFetch** oder **SQLFetchScroll**.|**SQLGetStmtAttr**|  
|SL012|Parameterbindungen Anweisung können nicht geändert werden, während ein Cursor geöffnet ist.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Eine positionierte Anforderung ausgestellt wurde, und nicht alle Spaltenfelder Anzahl gepuffert wurden.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** und **SQLFetchScroll** können nicht kombiniert werden.|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
