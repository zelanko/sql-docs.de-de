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
manager: craigg
ms.openlocfilehash: 600d90c14ae8b08a4860f3cff49c1615a9587063
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798218"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLExtendedFetch** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLExtendedFetch**, finden Sie unter [SQLExtendedFetch-Funktion](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Die Cursorbibliothek implementiert **SQLExtendedFetch** durch wiederholtes Aufrufen **SQLFetch** im Treiber.  
  
 Die Cursorbibliothek unterstützt Aufrufen **SQLExtendedFetch** mit einem *FetchOrientation* von sql_fetch_bookmark auf.  
  
 Wenn die Cursorbibliothek verwendet wird, Aufrufe von **SQLExtendedFetch** können nicht kombiniert werden, mit Aufrufen von entweder **SQLFetchScroll** oder **SQLFetch**.
