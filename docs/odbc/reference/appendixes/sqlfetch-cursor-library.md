---
title: SQLFetch (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bee83ccb5497888b57a45673599af6b92931a704
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298720"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLFetch-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen **zu SQLFetch**finden Sie unter [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Wenn die Cursorbibliothek verwendet wird, können Aufrufe von **SQLFetch** nicht mit Aufrufen von **SQLFetchScroll** oder **SQLExtendedFetch**gemischt werden.  
  
 Wenn **SQLFetch** aufgerufen wird, wobei SQL_ATTR_ROW_ARRAY_SIZE auf einen Wert größer als 1 festgelegt ist, übergibt die Cursorbibliothek den Aufruf an den Treiber. Wenn es sich bei dem Treiber um einen ODBC 2 handelt. *x-Treiber* wird die Rowset-Größe ignoriert, und der Aufruf von **SQLFetch** gibt eine einzelne Datenzeile zurück.  
  
 Wenn die Cursorbibliothek mit einem ODBC 2 verwendet wird. *x-Treiber* wird ein Bindungsoffset (wie durch das Attribut SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisung definiert) nicht verwendet, wenn **SQLFetch** aufgerufen wird.  
  
 Wenn die Cursorbibliothek geladen wird, kann eine Anwendung **SQLFetch** nicht aufrufen, um Lesezeichenspalten abzurufen. Die Cursorbibliothek übergibt den Aufruf von **SQLFetch** an den Treiber, aber die Funktionsaufrufe zum Aktivieren von Lesezeichen und binden der Lesezeichenspalte werden von der Cursorbibliothek abgefangen.
