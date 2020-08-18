---
description: SQLSetScrollOptions (Cursorbibliothek)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f40e5cd3b62b91b1b0b832b9b8fcf36101487c10
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386556"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetScrollOptions** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLSetScrollOptions**finden Sie unter [SQLSetScrollOptions-Funktion](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Die Cursor Bibliothek unterstützt **SQLSetScrollOptions** nur aus Gründen der Abwärtskompatibilität. Anwendungen sollten stattdessen die Attribute SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE und SQL_ATTR_ROW_ARRAY_SIZE-Anweisung verwenden.
