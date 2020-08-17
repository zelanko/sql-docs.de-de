---
description: SQLSetPos (Cursorbibliothek)
title: SQLSetPos (Cursor Bibliothek) | Microsoft-Dokumentation
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
ms.openlocfilehash: d35f1461f6a5da3ee894d9275c6ca112bfabab44
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339236"
---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetPos** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLSetPos**finden Sie unter [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 Die Cursor Bibliothek unterstützt den SQL_POSITION Vorgang nur für das *Vorgangs* Argument in **SQLSetPos**. Der SQL_LOCK_NO_CHANGE Wert wird nur für das *LockType* -Argument unterstützt.  
  
 Wenn der Treiber keine Massen Vorgänge unterstützt, gibt die Cursor Bibliothek SQLSTATE HYC00 (Treiber nicht fähig) zurück, wenn **SQLSetPos** mit *RowNumber* gleich 0 aufgerufen wird. Dieses Treiber Verhalten wird nicht empfohlen.  
  
 Die Cursor Bibliothek unterstützt die SQL_UPDATE-und SQL_DELETE Vorgänge in einem-Befehl von **SQLSetPos**nicht. Die Cursor Bibliothek implementiert eine positionierte UPDATE-oder DELETE-SQL-Anweisung, indem eine gesuchte Update-oder DELETE-Anweisung mit einer WHERE-Klausel erstellt wird, die die im Cache gespeicherten Werte für jede gebundene Spalte auflistet. Weitere Informationen finden Sie unter [Verarbeiten von positionierten Update-und DELETE-Anweisungen](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md).  
  
 Wenn der Treiber keine statischen Cursor unterstützt, sollte eine Anwendung, die mit der Cursor Bibliothek arbeitet, **SQLSetPos** nur für ein Rowset aufrufen, das von **SQLExtendedFetch** oder **SQLFetchScroll**abgerufen wurde, nicht von **SQLFetch**. Die Cursor Bibliothek implementiert **SQLExtendedFetch** und **SQLFetchScroll** durch wiederholte Aufrufe von **SQLFetch** (mit einer Rowsetgröße von 1) im Treiber. Die Cursor Bibliothek übergibt Aufrufe von **SQLFetch**auf der anderen Seite an den Treiber. Wenn **SQLSetPos** für ein mehr zeiliges Rowset aufgerufen wird, das von **SQLFetch** abgerufen wird, wenn der Treiber keine statischen Cursor unterstützt, schlägt der Aufruf fehl, da **SQLSetPos** nicht mit Vorwärts Cursor funktioniert. Dies geschieht auch, wenn eine Anwendung **SQLSetStmtAttr** erfolgreich aufgerufen hat, um SQL_ATTR_CURSOR_TYPE auf SQL_CURSOR_STATIC festzulegen, die von der Cursor Bibliothek unterstützt wird, auch wenn der Treiber keine statischen Cursor unterstützt.
