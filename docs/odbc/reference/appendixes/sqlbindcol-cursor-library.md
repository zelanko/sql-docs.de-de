---
title: SQLBindCol (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocStmt function [ODBC], Cursor Library
ms.assetid: f4dd546a-0a6c-4397-8ee7-fafa6b9da543
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e9e1018754977ee73ecdc21db30b3d8c2aae8b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692208"
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLBindCol** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLBindCol**, finden Sie unter [SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
 Ordnet eine oder mehrere Puffer für die Cursorbibliothek zum Zurückgeben des aktuellen Rowsets in die Anwendung. Ruft **SQLBindCol** einmal oder mehrmals, um diese Puffer auf das Resultset zu binden.  
  
 Kann eine Anwendung aufrufen **SQLBindCol** Ergebnis erneut binden Resultsetspalten nach aufgerufen wurde **SQLExtendedFetch**, **SQLFetch**, oder **SQLFetchScroll**, solange die C-Datentyp, die Spaltengröße und die Dezimalstellen der gebundenen Spalte unverändert bleiben. Die Anwendung muss den Cursor zum Binden von Spalten in anderen Adressen nicht geschlossen.  
  
 Die Cursorbibliothek unterstützt das Festlegen der SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut Bindung Offsets zu verwenden. (**SQLBindCol** muss nicht aufgerufen werden, für diese erneute Bindung stattfinden.) Wenn die Cursorbibliothek, mit einer ODBC 3. verwendet wird *.x* Treiber, der Offset für die Bindung ist nicht verwendet wird, wenn **SQLFetch** aufgerufen wird. Der Offset für die Bindung wird verwendet, wenn **SQLFetch** wird aufgerufen, wenn die Cursorbibliothek mit einer ODBC 2. verwendet wird. *X* Treiber da **SQLFetch** dann zugeordnet **SQLExtendedFetch**.  
  
 Die Cursorbibliothek unterstützt Aufrufen **SQLBindCol** die Lesezeichenspalte zu binden.  
  
 Wenn Sie mit einer ODBC 2. arbeiten zu können. *x* -Treiber verwenden, gibt die Cursorbibliothek SQLSTATE HY090 zurück (ungültige Zeichenfolgen- oder Pufferlänge.) Wenn **SQLBindCol** wird aufgerufen, um die Länge des Puffers für eine Lesezeichenspalte auf einen Wert festgelegt wird, der nicht gleich 4. Bei der Arbeit mit einer ODBC 3.*.x* -Treiber die Cursorbibliothek ermöglicht den Puffer, in eine beliebige Größe aufweisen.
