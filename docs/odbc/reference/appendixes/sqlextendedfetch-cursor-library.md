---
title: SQLExtendedFetch (Cursor Bibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe39b2d2cbbaf72ce3844c35187040589d1dac58
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302061"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLExtendedFetch** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLExtendedFetch**finden Sie unter [SQLExtendedFetch-Funktion](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Die Cursor Bibliothek implementiert **SQLExtendedFetch** durch wiederholtes Aufrufen von **SQLFetch** im Treiber.  
  
 Die Cursor Bibliothek unterstützt das Aufrufen von **SQLExtendedFetch** mit der *FetchOrientation* -SQL_FETCH_BOOKMARK.  
  
 Wenn die Cursor Bibliothek verwendet wird, können Aufrufe von **SQLExtendedFetch** nicht mit Aufrufen von **SQLFetchScroll** oder **SQLFetch**gemischt werden.
