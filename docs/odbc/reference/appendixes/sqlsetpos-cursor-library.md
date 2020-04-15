---
title: SQLSetPos (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Cursor Library
ms.assetid: 574399c3-2bb2-4d19-829c-7c77bd82858d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c46ef88075a5adbd96138d7d1f03c26712f7ea1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300510"
---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetPos-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLSetPos**finden Sie unter [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 Die Cursorbibliothek unterstützt den SQL_POSITION-Vorgang nur für das *Operation-Argument* in **SQLSetPos**. Es unterstützt den SQL_LOCK_NO_CHANGE-Wert nur für das *LockType-Argument.*  
  
 Wenn der Treiber keine Massenvorgänge unterstützt, gibt die Cursorbibliothek SQLSTATE HYC00 (Treiber nicht fähig) zurück, wenn **SQLSetPos** mit *RowNumber* gleich 0 aufgerufen wird. Dieses Treiberverhalten wird nicht empfohlen.  
  
 Die Cursorbibliothek unterstützt die SQL_UPDATE- und SQL_DELETE-Vorgänge in einem Aufruf von **SQLSetPos**nicht . Die Cursorbibliothek implementiert eine positionierte Aktualisierung oder löschen SQL-Anweisung, indem eine gesuchte Aktualisierungs- oder Löschanweisung mit einer WHERE-Klausel erstellt wird, die die im Cache gespeicherten Werte für jede gebundene Spalte aufzählt. Weitere Informationen finden Sie unter [Verarbeiten von positionierten Aktualisierungs- und Löschanweisungen](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md).  
  
 Wenn der Treiber keine statischen Cursor unterstützt, sollte eine Anwendung, die mit der Cursorbibliothek arbeitet, **SQLSetPos** nur für ein Rowset aufrufen, das von **SQLExtendedFetch** oder **SQLFetchScroll**abgerufen wird, nicht von **SQLFetch**. Die Cursorbibliothek implementiert **SQLExtendedFetch** und **SQLFetchScroll,** indem sie im Treiber wiederholt **SQLFetch** (mit einer Rowsetgröße von 1) aufruft. Die Cursorbibliothek übergibt hingegen Aufrufe an **SQLFetch**, an den Treiber. Wenn **SQLSetPos** für ein mehrreihiges Rowset aufgerufen wird, das von **SQLFetch** abgerufen wird, wenn der Treiber keine statischen Cursor unterstützt, schlägt der Aufruf fehl, da **SQLSetPos** nicht mit Vorwärtscursoren funktioniert. Dies tritt auch dann auf, wenn eine Anwendung **ERFOLGREICH SQLSetStmtAttr** aufgerufen hat, um SQL_ATTR_CURSOR_TYPE auf SQL_CURSOR_STATIC festzulegen, die von der Cursorbibliothek unterstützt wird, auch wenn der Treiber keine statischen Cursor unterstützt.
