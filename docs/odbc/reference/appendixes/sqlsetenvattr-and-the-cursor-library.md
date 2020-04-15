---
title: SQLSetEnvAttr und die Cursorbibliothek | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 42d6804bf8a3544de44c03266ce28712e1b04d90
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300520"
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr und die Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetEnvAttr-Funktion** mit der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLSetEnvAttr**finden Sie unter [SQLSetEnvAttr Function](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 Die Cursorbibliothek ist unabhängig von der Anwendungsversion oder Treiberversion nicht von der Einstellung des SQL_ATTR_ODBC_VERSION Umgebungsattributs betroffen.
