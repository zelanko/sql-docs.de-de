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
ms.openlocfilehash: 71afc3c0bac0ea64285c450640d96fe5f5d709b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064973"
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLBindCol** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLBindCol**, finden Sie unter [SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
 Ordnet eine oder mehrere Puffer für die Cursorbibliothek zum Zurückgeben des aktuellen Rowsets in die Anwendung. Ruft **SQLBindCol** einmal oder mehrmals, um diese Puffer auf das Resultset zu binden.  
  
 Kann eine Anwendung aufrufen **SQLBindCol** Ergebnis erneut binden Resultsetspalten nach aufgerufen wurde **SQLExtendedFetch**, **SQLFetch**, oder **SQLFetchScroll**, solange die C-Datentyp, die Spaltengröße und die Dezimalstellen der gebundenen Spalte unverändert bleiben. Die Anwendung muss den Cursor zum Binden von Spalten in anderen Adressen nicht geschlossen.  
  
 Die Cursorbibliothek unterstützt das Festlegen der SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut Bindung Offsets zu verwenden. (**SQLBindCol** muss nicht aufgerufen werden, für diese erneute Bindung stattfinden.) Wenn die Cursorbibliothek verwendet wird, mit einer ODBC- *3.x* Treiber, der Offset für die Bindung ist nicht verwendet werden, wenn **SQLFetch** aufgerufen wird. Der Offset für die Bindung wird verwendet, wenn **SQLFetch** wird aufgerufen, wenn die Cursorbibliothek verwendet wird, mit einer ODBC- *2.x* Treiber da **SQLFetch** dann zugeordnet  **SQLExtendedFetch**.  
  
 Die Cursorbibliothek unterstützt Aufrufen **SQLBindCol** die Lesezeichenspalte zu binden.  
  
 Beim Arbeiten mit ODBC *2.x* -Treiber verwenden, gibt die Cursorbibliothek SQLSTATE HY090 zurück (ungültige Zeichenfolgen- oder Pufferlänge.) Wenn **SQLBindCol** wird aufgerufen, um die Länge des Puffers für eine Lesezeichenspalte nicht auf einen Wert festgelegt gleich 4. Beim Arbeiten mit ODBC *3.x* -Treiber die Cursorbibliothek ermöglicht den Puffer, in eine beliebige Größe aufweisen.
