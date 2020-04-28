---
title: Sqlsettenvattr und die Cursor Bibliothek | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300520"
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr und die Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **sqlsettenvattr** -Funktion mit der Cursor Bibliothek erläutert. Allgemeine Informationen zu **sqlsertenvattr**finden Sie unter [sqlsettenvattr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 Die Cursor Bibliothek ist von der Einstellung des SQL_ATTR_ODBC_VERSION Environment-Attributs unabhängig von der Anwendungs Version oder Treiber Version nicht betroffen.
