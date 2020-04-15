---
title: SQLExtendedFetch (Cursorbibliothek) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302061"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLExtendedFetch-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLExtendedFetch**finden Sie unter [SQLExtendedFetch-Funktion](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Die Cursorbibliothek implementiert **SQLExtendedFetch,** indem **SQLFetch** wiederholt im Treiber aufgerufen wird.  
  
 Die Cursorbibliothek unterstützt das Aufrufen von **SQLExtendedFetch** mit einem *FetchOrientation* von SQL_FETCH_BOOKMARK.  
  
 Wenn die Cursorbibliothek verwendet wird, können Aufrufe von **SQLExtendedFetch** nicht mit Aufrufen von **SQLFetchScroll** oder **SQLFetch**gemischt werden.
