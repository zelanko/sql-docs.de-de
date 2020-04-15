---
title: SQLGetFunctions (Cursorbibliothek) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f993a08aae1656b8d373911299e75852de855419
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307821"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLGetFunctions-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLGetFunctions**finden Sie unter [SQLGetFunctions Function](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 Wenn Sie **SQLGetFunctions**aufrufen, gibt die Cursorbibliothek zurück, dass sie ZUSÄTZLICH zu den vom Treiber unterstützten Funktionen **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**und **SQLSetScrollOptions**unterstützt.
