---
title: SQLSetStmtAttr (Cursorbibliothek) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300490"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetStmtAttr-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLSetStmtAttr**finden Sie unter [SQLSetStmtAttr Function](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 Die Cursorbibliothek unterstützt die folgenden Anweisungsattribute mit **SQLSetStmtAttr:**  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 Die Cursorbibliothek unterstützt nur die SQL_CURSOR_FORWARD_ONLY- und SQL_CURSOR_STATIC Werte des Attributs SQL_ATTR_CURSOR_TYPE..  
  
 Bei Vorwärtscursorn unterstützt die Cursorbibliothek den SQL_CONCUR_READ_ONLY Wert des Attributs SQL_ATTR_CONCURRENCY.. Bei statischen Cursorn unterstützt die Cursorbibliothek die SQL_CONCUR_READ_ONLY- und SQL_CONCUR_VALUES Werte des Attributs SQL_ATTR_CONCURRENCY..  
  
 Die Cursorbibliothek unterstützt nur den SQL_SC_NON_UNIQUE Wert des SQL_ATTR_SIMULATE_CURSOR-Anweisungsattributs.  
  
 Obwohl die ODBC-Spezifikation Aufrufe von **SQLSetStmtAttr** mit den SQL_ATTR_PARAM_BIND_TYPE oder SQL_ATTR_ROW_BIND_TYPE Attributen unterstützt, nachdem **SQLFetch** oder **SQLFetchScroll** aufgerufen wurde, ist die cursorbibliothek dies nicht. Bevor der Bindungstyp in der Cursorbibliothek geändert werden kann, muss die Anwendung den Cursor schließen. Die Cursorbibliothek unterstützt das Ändern der SQL_ATTR_ROW_BIND_OFFSET_PTR-, SQL_ATTR_PARAM_BIND_OFFSET_PTR-, SQL_ATTR_ROWS_FETCHED_PTR- und SQL_ATTR_PARAMS_PROCESSED_PTR Anweisungsattribute, wenn ein Cursor geöffnet ist.  
  
 Eine Anwendung kann **SQLSetStmtAttr** mit einem **Attribut** von SQL_ATTR_ROW_ARRAY_SIZE aufrufen, um die Rowsetgröße zu ändern, während ein Cursor geöffnet ist. Die neue Rowsetgröße wird beim nächsten Aufruf von **SQLFetchScroll** oder **SQLFetch** wirksam.  
  
 Die Cursorbibliothek unterstützt das Festlegen des SQL_ATTR_PARAM_BIND_OFFSET_PTR oder SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisungsattributs, um Bindungsoffsets zu aktivieren. Der Bindungsoffset wird nicht für Aufrufe von **SQLFetch** verwendet, wenn die Cursorbibliothek mit einem ODBC 2 verwendet wird. *x-Treiber.*  
  
 Die Cursorbibliothek unterstützt das Festlegen des Attributs SQL_ATTR_USE_BOOKMARKS-Anweisung auf SQL_UB_VARIABLE.
