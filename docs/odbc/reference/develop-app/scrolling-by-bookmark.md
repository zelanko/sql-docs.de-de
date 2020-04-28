---
title: Scrollen nach Lesezeichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 454e29abdf848fdf4f4eaae090e7cc326f0048df
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304191"
---
# <a name="scrolling-by-bookmark"></a>Scrollen durch Textmarken
Beim Abrufen von Zeilen mit **SQLFetchScroll**kann eine Anwendung ein Lesezeichen als Grundlage für die Auswahl der Anfangs Zeile verwenden. Dies ist eine Form der absoluten Adressierung, da sie nicht von der aktuellen Cursorposition abhängt. Um einen Bildlauf zu einer mit einem Lesezeichen markierten Zeile durchführen zu können, ruft die Anwendung **SQLFetchScroll** mit der *FetchOrientation* SQL_FETCH_BOOKMARK auf. Dieser Vorgang verwendet das Lesezeichen, auf das das SQL_ATTR_FETCH_BOOKMARK_PTR Statement-Attribut verweist. Es gibt das Rowset zurück, das mit der Zeile beginnt, die von diesem Lesezeichen identifiziert wird. Eine Anwendung kann einen Offset für diesen Vorgang im *FetchOffset* -Argument des Aufrufens von **SQLFetchScroll**angeben. Wenn ein Offset angegeben wird, wird die erste Zeile des zurückgegebenen Rowsets festgelegt, indem die Zahl im *FetchOffset* -Argument der Nummer der Zeile, die durch das Lesezeichen identifiziert wird, hinzugefügt wird. Diese Verwendung des *FetchOffset* -Arguments wird bei Verwendung mit ODBC 2 nicht unterstützt. *x* -Treiber; Wenn eine Anwendung **SQLFetchScroll** in einem ODBC 2 aufruft. *x* -Treiber, bei dem *FetchOrientation* auf SQL_FETCH_BOOKMARK festgelegt ist, muss das *FetchOffset* -Argument auf 0 festgelegt werden.
