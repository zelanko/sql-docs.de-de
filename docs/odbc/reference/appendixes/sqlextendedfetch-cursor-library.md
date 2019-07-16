---
title: SQLExtendedFetch (Cursor Library) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a3fd7d02d74b0e19d91871c5df7c9c5915d028f5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064455"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLExtendedFetch** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLExtendedFetch**, finden Sie unter [SQLExtendedFetch-Funktion](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Die Cursorbibliothek implementiert **SQLExtendedFetch** durch wiederholtes Aufrufen **SQLFetch** im Treiber.  
  
 Die Cursorbibliothek unterstützt Aufrufen **SQLExtendedFetch** mit einem *FetchOrientation* von sql_fetch_bookmark auf.  
  
 Wenn die Cursorbibliothek verwendet wird, Aufrufe von **SQLExtendedFetch** können nicht kombiniert werden, mit Aufrufen von entweder **SQLFetchScroll** oder **SQLFetch**.
