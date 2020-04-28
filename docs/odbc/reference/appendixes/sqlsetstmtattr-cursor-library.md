---
title: SQLSetStmtAttr (Cursor Bibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtAttr function [ODBC], Cursor Library
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bdd9b3b559d5cc78a0d44f5280aae347bc8996a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300490"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetStmtAttr** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLSetStmtAttr**finden Sie unter [SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 Die Cursor Bibliothek unterstützt die folgenden Anweisungs Attribute mit **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 Die Cursor Bibliothek unterstützt nur die SQL_CURSOR_FORWARD_ONLY und SQL_CURSOR_STATIC Werte des Attributs der SQL_ATTR_CURSOR_TYPE Anweisung.  
  
 Für Vorwärts Cursor unterstützt die Cursor Bibliothek den SQL_CONCUR_READ_ONLY Wert des Attributs der SQL_ATTR_CONCURRENCY Anweisung. Bei statischen Cursorn unterstützt die Cursor Bibliothek die SQL_CONCUR_READ_ONLY und SQL_CONCUR_VALUES Werte des Attributs der SQL_ATTR_CONCURRENCY Anweisung.  
  
 Die Cursor Bibliothek unterstützt nur den SQL_SC_NON_UNIQUE Wert des Attributs der SQL_ATTR_SIMULATE_CURSOR Anweisung.  
  
 Obwohl die ODBC-Spezifikation Aufrufe von **SQLSetStmtAttr** mit den SQL_ATTR_PARAM_BIND_TYPE-oder SQL_ATTR_ROW_BIND_TYPE-Attributen unterstützt, nachdem **SQLFetch** oder **SQLFetchScroll** aufgerufen wurde, wird die Cursor Bibliothek nicht verwendet. Bevor der Bindungstyp in der Cursor Bibliothek geändert werden kann, muss der Cursor von der Anwendung geschlossen werden. Die Cursor Bibliothek unterstützt das Ändern der SQL_ATTR_ROW_BIND_OFFSET_PTR-, SQL_ATTR_PARAM_BIND_OFFSET_PTR-, SQL_ATTR_ROWS_FETCHED_PTR-und SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungs Attribute, wenn ein Cursor geöffnet ist.  
  
 Eine Anwendung kann **SQLSetStmtAttr** mit einem **Attribut** von SQL_ATTR_ROW_ARRAY_SIZE aufrufen, um die Rowsetgröße zu ändern, während ein Cursor geöffnet ist. Die neue Rowsetgröße wird beim nächsten Aufrufen von **SQLFetchScroll** oder **SQLFetch** wirksam.  
  
 Die Cursor Bibliothek unterstützt das Festlegen des SQL_ATTR_PARAM_BIND_OFFSET_PTR oder SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisungs Attributs, um Bindungs Offsets zu aktivieren. Der Bindungs Offset wird nicht für Aufrufe von **SQLFetch** verwendet, wenn die Cursor Bibliothek mit einem ODBC 2 verwendet wird. *x* -Treiber  
  
 Die Cursor Bibliothek unterstützt das Festlegen des SQL_ATTR_USE_BOOKMARKS Anweisungs Attributs auf SQL_UB_VARIABLE.
