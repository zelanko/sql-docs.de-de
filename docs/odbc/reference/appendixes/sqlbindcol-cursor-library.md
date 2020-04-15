---
title: SQLBindCol (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocStmt function [ODBC], Cursor Library
ms.assetid: f4dd546a-0a6c-4397-8ee7-fafa6b9da543
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c29909a96f147a0f5ebc2140a68072dfe544255
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305471"
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLBindCol-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen **zu SQLBindCol**finden Sie unter [SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
 Eine Anwendung weist der Cursorbibliothek einen oder mehrere Puffer zu, um das aktuelle Rowset zurückzugeben. Es ruft **SQLBindCol** ein oder mehrere Male auf, um diese Puffer an das Resultset zu binden.  
  
 Eine Anwendung kann **SQLBindCol** aufrufen, um Resultsetspalten neu zu binden, nachdem sie **SQLExtendedFetch**, **SQLFetch**oder **SQLFetchScroll**aufgerufen hat, solange der C-Datentyp, die Spaltengröße und die Dezimalstellen der gebundenen Spalte gleich bleiben. Die Anwendung muss den Cursor nicht schließen, um Spalten an verschiedene Adressen neu zu binden.  
  
 Die Cursorbibliothek unterstützt das Festlegen des SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisungsattributs für die Verwendung von Bindungsoffsets. (**SQLBindCol** muss nicht aufgerufen werden, damit diese Neubindung erfolgt.) Wenn die Cursorbibliothek mit einem ODBC *3.x-Treiber* verwendet wird, wird der Bindungsoffset nicht verwendet, wenn **SQLFetch** aufgerufen wird. Der Bindungsoffset wird verwendet, wenn **SQLFetch** aufgerufen wird, wenn die Cursorbibliothek mit einem ODBC *2.x-Treiber* verwendet wird, da **SQLFetch** dann **SQLExtendedFetch**zugeordnet wird.  
  
 Die Cursorbibliothek unterstützt den Aufruf von **SQLBindCol** zum Binden der Lesezeichenspalte.  
  
 Wenn Sie mit einem ODBC *2.x-Treiber* arbeiten, gibt die Cursorbibliothek SQLSTATE HY090 (Ungültige Zeichenfolge oder Pufferlänge) zurück, wenn **SQLBindCol** aufgerufen wird, um die Pufferlänge für eine Lesezeichenspalte auf einen Wert festzulegen, der nicht gleich 4 ist. Wenn Sie mit einem ODBC *3.x-Treiber* arbeiten, lässt die Cursorbibliothek zu, dass der Puffer eine beliebige Größe hat.
