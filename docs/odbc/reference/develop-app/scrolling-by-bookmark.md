---
title: Scrollen von Lesezeichen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304191"
---
# <a name="scrolling-by-bookmark"></a>Scrollen durch Textmarken
Beim Abrufen von Zeilen mit **SQLFetchScroll**kann eine Anwendung eine Textmarke als Grundlage für die Auswahl der Startzeile verwenden. Dies ist eine Form der absoluten Adressierung, da sie nicht von der aktuellen Cursorposition abhängt. Um zu einer mit Lesezeichen versehenen Zeile zu scrollen, ruft die Anwendung **SQLFetchScroll** mit einem *FetchOrientation* von SQL_FETCH_BOOKMARK auf. Dieser Vorgang verwendet die Textmarke, auf die das Attribut SQL_ATTR_FETCH_BOOKMARK_PTR Anweisung zeigt. Es gibt das Rowset zurück, das mit der Zeile beginnt, die von diesem Lesezeichen identifiziert wird. Eine Anwendung kann einen Offset für diesen Vorgang im *FetchOffset-Argument* des Aufrufs von **SQLFetchScroll**angeben. Wenn ein Offset angegeben wird, wird die erste Zeile des zurückgegebenen Rowsets bestimmt, indem die Zahl im *Argument FetchOffset* zur Nummer der Zeile hinzugefügt wird, die durch die Textmarke identifiziert wird. Diese Verwendung des *FetchOffset-Arguments* wird bei Verwendung mit ODBC 2 nicht unterstützt. *x-Treiber;* wenn eine Anwendung **SQLFetchScroll** in einem ODBC 2 aufruft. *x-Treiber,* bei *dem FetchOrientation* auf SQL_FETCH_BOOKMARK festgelegt ist, muss das *FetchOffset-Argument* auf 0 gesetzt sein.
