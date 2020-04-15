---
title: SQLSetConnectAttr (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a87c85d727fb9eb2fc27613b9eecd3fe0ec51b58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300540"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetConnectAttr-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLSetConnectAttr**finden Sie unter [SQLSetConnectAttr Function](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Eine Anwendung ruft **SQLSetConnectAttr** mit dem attribut SQL_ATTR_ODBC_CURSORS auf, um anzugeben, ob die Cursorbibliothek immer verwendet, verwendet wird, wenn der Treiber keine scrollbaren Cursor unterstützt oder nie verwendet wird. Die Cursorbibliothek geht davon aus, dass ein Treiber scrollbare Cursor unterstützt, wenn er SQL_CA1_RELATIVE für den SQL_STATIC_CURSOR_ATTRIBUTES1-Informationstyp in **SQLGetInfo**zurückgibt.  
  
 Die Anwendung muss **SQLSetConnectAttr** aufrufen, um die Verwendung der Cursorbibliothek anzugeben, nachdem sie **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC, um die Verbindung zuzuweisen, und bevor sie eine Verbindung mit der Datenquelle herstellt. Wenn eine Anwendung **SQLSetConnectAttr** mit dem attribut SQL_ATTR_ODBC_CURSORS aufruft, während die Verbindung noch aktiv ist, gibt die Cursorbibliothek einen Fehler zurück.  
  
 Um ein Anweisungsattribut festzulegen, das von der Cursorbibliothek für alle Anweisungen festgelegt wird, die einer Verbindung zugeordnet sind, muss eine Anwendung **SQLSetConnectAttr** für dieses Anweisungsattribut aufrufen, nachdem sie eine Verbindung mit der Datenquelle hergestellt und den Cursor geöffnet hat. Wenn eine Anwendung **SQLSetConnectAttr** mit einem Anweisungsattribut aufruft und ein Cursor für eine Anweisung geöffnet ist, die der Verbindung zugeordnet ist, wird das Anweisungsattribut erst dann auf diese Anweisung angewendet, wenn der Cursor geschlossen und erneut geöffnet wird.
