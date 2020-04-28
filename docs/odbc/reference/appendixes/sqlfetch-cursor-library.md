---
title: SQLFetch (Cursor Bibliothek) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298720"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLFetch** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLFetch**finden Sie unter [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Wenn die Cursor Bibliothek verwendet wird, können Aufrufe von **SQLFetch** nicht mit Aufrufen von **SQLFetchScroll** oder **SQLExtendedFetch**gemischt werden.  
  
 Wenn **SQLFetch** aufgerufen wird und SQL_ATTR_ROW_ARRAY_SIZE auf einen Wert größer als 1 festgelegt ist, übergibt die Cursor Bibliothek den Aufruf an den Treiber. , Wenn der Treiber ein ODBC 2 ist. *x* -Treiber, die Rowsetgröße wird ignoriert, und der **SQLFetch** -Befehl gibt eine einzelne Daten Zeile zurück.  
  
 , Wenn die Cursor Bibliothek mit ODBC 2 verwendet wird. der *x* -Treiber, ein Bindungs Offset (wie vom SQL_ATTR_ROW_BIND_OFFSET_PTR Statement-Attribut definiert) wird nicht verwendet, wenn **SQLFetch** aufgerufen wird.  
  
 Wenn die Cursor Bibliothek geladen wird, kann eine Anwendung **SQLFetch** nicht zum Abrufen von Lesezeichen Spalten aufzurufen. Die Cursor Bibliothek übergibt den Aufruf von **SQLFetch** durch an den Treiber, aber die Funktionsaufrufe zum Aktivieren von Lesezeichen und zum Binden der Lesezeichen Spalte werden von der Cursor Bibliothek abgefangen.
