---
title: SQLSetScrollOptions (Cursorbibliothek) | Microsoft Docs
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
ms.openlocfilehash: 0099ca5e9bcb3aefdd86e0132f52d110ab64e8a4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304911"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetScrollOptions-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLSetScrollOptions**finden Sie unter [SQLSetScrollOptions-Funktion](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Die Cursorbibliothek unterstützt **SQLSetScrollOptions** nur aus Gründen der Abwärtskompatibilität. Anwendungen sollten stattdessen die SQL_ATTR_CONCURRENCY-, SQL_ATTR_CURSOR_TYPE- und SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribute verwenden.
