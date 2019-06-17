---
title: SQLSetStmtAttr (Cursor Library) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d4e5bd6ec27891e80933dfcc42beec9056d2d3a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62735208"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLSetStmtAttr** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLSetStmtAttr**, finden Sie unter [SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 Die Cursorbibliothek unterstützt die folgenden Anweisungsattribute mit **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 Die Cursorbibliothek unterstützt nur die SQL_CURSOR_FORWARD_ONLY und SQL_CURSOR_STATIC Werte des Attributs SQL_ATTR_CURSOR_TYPE-Anweisung.  
  
 Für Vorwärtscursor unterstützt die Cursorbibliothek die SQL_CONCUR_READ_ONLY-Wert, der das SQL_ATTR_CONCURRENCY-Anweisungsattribut auf. Für statische Cursor unterstützt die Cursorbibliothek die SQL_CONCUR_READ_ONLY und SQL_CONCUR_VALUES-Werte, der das SQL_ATTR_CONCURRENCY-Anweisungsattribut auf.  
  
 Die Cursorbibliothek unterstützt nur den SQL_SC_NON_UNIQUE-Wert des Attributs SQL_ATTR_SIMULATE_CURSOR-Anweisung.  
  
 Obwohl die ODBC-Spezifikation Aufrufe unterstützt **SQLSetStmtAttr** mit den Attributen SQL_ATTR_PARAM_BIND_TYPE oder SQL_ATTR_ROW_BIND_TYPE nach **SQLFetch** oder **SQLFetchScroll**  aufgerufen wurde, den Cursor Library nicht. Bevor sie den Bindungstyp im die Cursorbibliothek ändern kann, muss die Anwendung den Cursor zu schließen. Die Cursorbibliothek unterstützt Ändern des SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR fest und Anweisungsattribute SQL_ATTR_PARAMS_PROCESSED_PTR, wenn ein Cursor geöffnet ist.  
  
 Kann eine Anwendung aufrufen **SQLSetStmtAttr** mit einer **Attribut** von SQL_ATTR_ROW_ARRAY_SIZE, um die Größe des Rowsets zu ändern, während ein Cursor geöffnet ist. Die neue Rowsetgröße werden wirksam, das nächste Mal **SQLFetchScroll** oder **SQLFetch** aufgerufen wird.  
  
 Die Cursorbibliothek unterstützt das Festlegen der SQL_ATTR_PARAM_BIND_OFFSET_PTR oder SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut, um die Bindung Offsets zu aktivieren. Der Offset für die Bindung wird nicht verwendet werden, für Aufrufe von **SQLFetch** Wenn mit einer ODBC 2. die Cursorbibliothek verwendet wird. *X* Treiber.  
  
 Die Cursorbibliothek unterstützt das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festlegen.
