---
title: Scrollen durch Lesezeichen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90ba6ed3a6feb163fbe1eaf39cce14ae501c232e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468376"
---
# <a name="scrolling-by-bookmark"></a>Scrollen durch Textmarken
Beim Abrufen von Zeilen mit **SQLFetchScroll**, eine Anwendung kann ein Lesezeichen als Basis für die Auswahl der Startzeile verwenden. Dies ist eine Form der absoluten Adressierung, da sie nicht von der aktuellen Cursorposition abhängt. Um einen Bildlauf zu einer mit Lesezeichen versehenen Zeile, die Anwendung ruft **SQLFetchScroll** mit einem *FetchOrientation* von sql_fetch_bookmark auf. Dieser Vorgang verwendet das Lesezeichen, das das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungsattribut verweist. Es gibt das Rowset zurück, das mit der Zeile beginnt, die von diesem Lesezeichen identifiziert wird. Eine Anwendung kann einen Offset für diesen Vorgang im Angeben der *FetchOffset* Argument des Methodenaufrufs **SQLFetchScroll**. Wenn ein Offset angegeben wird, richtet sich die erste Zeile des zurückgegebenen Rowsets durch Hinzufügen der Zahl in die *FetchOffset* Argument für die Anzahl der Zeilen, die vom Lesezeichen identifiziert. Diese Verwendung von der *FetchOffset* Argument wird nicht unterstützt, bei der Verwendung mit ODBC 2. *X* Treiber; Wenn eine Anwendung ruft **SQLFetchScroll** in einer ODBC 2. *X* Treiber mit *FetchOrientation* festgelegt sql_fetch_bookmark auf, die *FetchOffset* Argument muss auf 0 festgelegt werden.
