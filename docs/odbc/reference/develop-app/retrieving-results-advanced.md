---
title: Abrufen von Ergebnissen (erweitert) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22a88a96b856ba0976dcb8600d26f78b772654bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020503"
---
# <a name="retrieving-results-advanced"></a>Abrufen von Ergebnissen (Erweitert)
Eine Anwendung kann angeben, dass ein Offset zu gebundenen Datenpuffer Adressen und die entsprechenden Längen-/indikatorpufferadressen hinzugefügt werden, wenn **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos** aufgerufen wird. Die Ergebnisse dieser Ergänzungen bestimmen die Adressen, die in diesen Vorgängen verwendet werden.  
  
 Bindungs Offsets ermöglichen es einer Anwendung, Bindungen zu ändern, ohne dass **SQLBindCol** für zuvor gebundene Spalten aufgerufen wird. Beim Aufrufen von **SQLBindCol** zum erneuten Binden von Daten werden die Puffer Adresse und der Längen-/indikatorenzeiger geändert. Durch die erneute Bindung mit einem Offset wird hingegen einfach der vorhandene gebundene Datenpuffer Adresse und der Länge/Indikator-Puffer Adresse ein Offset hinzugefügt. Wenn Offsets verwendet werden, sind die Bindungen eine "Vorlage" für die Art und Weise, wie die Anwendungs Puffer angelegt werden, und die Anwendung kann diese "Vorlage" durch Ändern des Offsets in verschiedene Speicherbereiche verschieben. Ein neuer Offset kann jederzeit angegeben werden und wird immer den ursprünglich gebundenen Werten hinzugefügt.  
  
 Um einen Bindungs Offset anzugeben, legt die Anwendung das SQL_ATTR_ROW_BIND_OFFSET_PTR Statement-Attribut auf die Adresse eines SQLINTEGER-Puffers fest. Bevor die Anwendung eine Funktion aufruft, die die Bindungen verwendet, wie z. b. **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**, fügt Sie einen Offset in Bytes in diesem Puffer ein, solange weder die Datenpuffer Adresse noch die Länge/Indikator-Puffer Adresse 0 ist und die gebundene Spalte im Resultset ist. Die Summe der Adresse und des Offsets muss eine gültige Adresse sein. (Dies bedeutet, dass entweder der Offset und die Adresse, zu der der Offset hinzugefügt wird, ungültig sein können, solange die Summe eine gültige Adresse ist.) Das SQL_ATTR_ROW_BIND_OFFSET_PTR Statement-Attribut ist ein Zeiger, sodass der Offset Wert auf mehr als einen Satz von Bindungs Daten angewendet werden kann, die alle durch Ändern eines Offset Werts geändert werden können. Eine Anwendung muss sicherstellen, dass der Zeiger gültig bleibt, bis der Cursor geschlossen wird.  
  
> [!NOTE]  
>  Bindungs Offsets werden von ODBC 2 nicht unterstützt. *x* -Treiber.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Blockcursor](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [Scrollbare Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [Die ODBC-Cursorbibliothek](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md)
