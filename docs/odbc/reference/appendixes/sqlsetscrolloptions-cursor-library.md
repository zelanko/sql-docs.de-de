---
title: SQLSetScrollOptions (Cursor Bibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18a0bc111f6b4e8d82d0ed353837b499f920479e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68023357"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetScrollOptions** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLSetScrollOptions**finden Sie unter [SQLSetScrollOptions-Funktion](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Die Cursor Bibliothek unterstützt **SQLSetScrollOptions** nur aus Gründen der Abwärtskompatibilität. Anwendungen sollten stattdessen die Attribute SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE und SQL_ATTR_ROW_ARRAY_SIZE-Anweisung verwenden.
