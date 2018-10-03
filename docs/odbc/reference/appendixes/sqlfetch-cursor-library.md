---
title: SQLFetch (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 487a6b357d21ee675fa9594d32c7a2bb7c66e400
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809328"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLFetch** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLFetch**, finden Sie unter [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Wenn die Cursorbibliothek verwendet wird, Aufrufe von **SQLFetch** können nicht kombiniert werden, mit Aufrufen von entweder **SQLFetchScroll** oder **SQLExtendedFetch**.  
  
 Wenn **SQLFetch** wird aufgerufen, mit dem SQL_ATTR_ROW_ARRAY_SIZE auf einen Wert größer als 1 festgelegt, wird die Cursorbibliothek den Aufruf an den Treiber übergeben. Wenn der Treiber eine ODBC-2 ist. *x* -Treiber verwenden, die Größe des Rowsets werden ignoriert und der Aufruf von **SQLFetch** eine einzelne Zeile mit Daten zurück.  
  
 Wenn die Cursor-Bibliothek mit einer ODBC 2. verwendet wird. *x* Treiber, eine Bindung mit dem offset (wie durch das Anweisungsattribut SQL_ATTR_ROW_BIND_OFFSET_PTR definiert) ist nicht verwendet werden, wenn **SQLFetch** aufgerufen wird.  
  
 Eine Anwendung kann nicht aufgerufen, wenn die Cursorbibliothek geladen ist, **SQLFetch** Lesezeichenspalten abgerufen. Die Cursorbibliothek übergibt den Aufruf von **SQLFetch** über den Treiber, aber die Funktion Aufrufe zum Aktivieren von Lesezeichen und binden die Lesezeichenspalte abgefangen werden von der Cursorbibliothek.
