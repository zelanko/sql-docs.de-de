---
title: SQLGetFunctions (Cursor Bibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1497a7d2ec5951feedb36831ab541413e57152f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073918"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLGetFunctions** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLGetFunctions**finden Sie unter [SQLGetFunctions-Funktion](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 Wenn Sie **SQLGetFunctions**aufrufen, gibt die Cursor Bibliothek zusätzlich zu den vom Treiber unterstützten Funktionen zurück, dass **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**und **SQLSetScrollOptions**unterstützt werden.
