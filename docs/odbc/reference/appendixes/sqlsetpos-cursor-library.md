---
title: SQLSetPos (Cursor Library) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b41fad0f609b16640bfa28ab36f29f364e067b73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622098"
---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLSetPos** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLSetPos**, finden Sie unter [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 Die Cursor-Bibliothek unterstützt den SQL_POSITION-Vorgang nur für die *Vorgang* -Argument in **SQLSetPos**. Es unterstützt die SQL_LOCK_NO_CHANGE Wert nur für die *LockType* Argument.  
  
 Wenn der Treiber Massenvorgänge nicht unterstützt, gibt die Cursorbibliothek SQLSTATE HYC00 zurück (nicht-Treiber) beim **SQLSetPos** aufgerufen wird und *' RowNumber '* gleich 0. Dieses Verhalten Treiber wird nicht empfohlen.  
  
 Die Cursorbibliothek unterstützt nicht die SQL_UPDATE und SQL_DELETE-Vorgänge in einem Aufruf von **SQLSetPos**. Der Cursor-Bibliothek implementiert eine positionierte aktualisieren oder Löschen von SQL-Anweisung durch das Erstellen einer komplexen aktualisieren oder delete-Anweisung mit einer WHERE-Klausel, die in seinem Cache für jede gebundene Spalte gespeicherten Werte auflistet. Weitere Informationen finden Sie unter [Verarbeitung positioniert Update- und Delete-Anweisungen](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md).  
  
 Wenn der Treiber keine statische Cursor unterstützt, sollte eine Anwendung mit der Cursorbibliothek Aufrufen **SQLSetPos** nur für ein Rowset, das abgerufen werden, indem **SQLExtendedFetch** oder **SQLFetchScroll** , nicht von **SQLFetch**. Die Cursorbibliothek implementiert **SQLExtendedFetch** und **SQLFetchScroll** durch wiederholte Aufrufe von **SQLFetch** (mit einer Rowsetgröße von 1) im Treiber. Die Cursorbibliothek übergibt Aufrufe **SQLFetch**, auf die andere hingegen mit dem Treiber. Wenn **SQLSetPos** wird aufgerufen, in einem mehrzeiligen Rowset abgerufen werden, indem **SQLFetch** , wenn der Treiber keine statische Cursor unterstützt, schlägt der Aufruf fehl, da **SQLSetPos** funktioniert nicht mit Vorwärtscursor. Dies geschieht auch, wenn eine Anwendung erfolgreich aufgerufen wurde **SQLSetStmtAttr** für SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, festzulegen, die die Cursorbibliothek unterstützt, auch wenn der Treiber keine statische Cursor unterstützt.
