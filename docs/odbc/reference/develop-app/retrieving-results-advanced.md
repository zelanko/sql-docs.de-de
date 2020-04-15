---
title: Abrufen von Ergebnissen (Erweitert) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- offsets [ODBC]
- result sets [ODBC], about result sets
- bind offsets [ODBC]
ms.assetid: bc00c379-71a7-407a-975c-898243f39bb6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca02b4ff911c8edff06b38d5341eeaa288cc194c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294640"
---
# <a name="retrieving-results-advanced"></a>Abrufen von Ergebnissen (Erweitert)
Eine Anwendung kann angeben, dass ein Offset zu gebundenen Datenpufferadressen und den entsprechenden Längen-/Indikatorpufferadressen hinzugefügt wird, wenn **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos** aufgerufen werden. Die Ergebnisse dieser Ergänzungen bestimmen die Adressen, die in diesen Vorgängen verwendet werden.  
  
 Bindungsoffsets ermöglichen es einer Anwendung, Bindungen zu ändern, ohne **SQLBindCol** für zuvor gebundene Spalten aufzurufen. Ein Aufruf von **SQLBindCol** zum erneuten Binden von Daten ändert die Pufferadresse und den Längen-/Indikatorzeiger. Die Neubindung mit einem Offset hingegen fügt der vorhandenen gebundenen Datenpufferadresse und Längen-/Indikatorpufferadresse einfach einen Offset hinzu. Wenn Offsets verwendet werden, sind die Bindungen eine "Vorlage" dafür, wie die Anwendungspuffer angeordnet sind, und die Anwendung kann diese "Vorlage" in verschiedene Speicherbereiche verschieben, indem sie den Offset ändert. Ein neuer Offset kann jederzeit angegeben werden und wird immer zu den ursprünglich gebundenen Werten hinzugefügt.  
  
 Um einen Bindungsoffset anzugeben, legt die Anwendung das SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut auf die Adresse eines SQLINTEGER-Puffers fest. Bevor die Anwendung eine Funktion aufruft, die die Bindungen verwendet, z. B. **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**, platziert sie einen Offset in Bytes in diesem Puffer, solange weder die Datenpufferadresse noch die Length/Indicator-Pufferadresse 0 ist und die gebundene Spalte im Resultset ist. Die Summe der Adresse und des Offsets muss eine gültige Adresse sein. (Dies bedeutet, dass entweder der Offset oder die Adresse, der der Offset hinzugefügt wird, ungültig sein kann, solange ihre Summe eine gültige Adresse ist.) Das SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisungsattribut ist ein Zeiger, sodass der Offsetwert auf mehr als einen Satz von Bindungsdaten angewendet werden kann, die alle durch Ändern eines Offsetwerts geändert werden können. Eine Anwendung muss sicherstellen, dass der Zeiger gültig bleibt, bis der Cursor geschlossen wird.  
  
> [!NOTE]  
>  Bindungsoffsets werden von ODBC 2 nicht unterstützt. *x-Treiber.*  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Blockcursor](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [Scrollbare Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [Die ODBC-Cursorbibliothek](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md)
