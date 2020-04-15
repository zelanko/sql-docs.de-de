---
title: SQLFreeStmt (Cursor-Bibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d78075593926c15dbaeb1904603b08e990f64983
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302021"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLFreeStmt-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLFreeStmt**finden Sie unter [SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Wenn eine Anwendung **SQLFreeStmt** mit der Option SQL_UNBIND aufruft, nachdem sie **SQLExtendedFetch**, **SQLFetch**oder **SQLFetchScroll aufruft,** gibt die Cursorbibliothek einen Fehler zurück. Bevor die Bindung von Ergebnissatzspalten aufentschieden werden kann, muss eine Anwendung **SQLCloseCursor** oder **SQLFreeStmt** mit der Option SQL_CLOSE aufrufen.
