---
title: Verarbeitung von positionierten Aktualisierungs- und Löschanweisungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- SQL statements [ODBC], cursor library
- ODBC cursor library [ODBC], positioned update or delete
- cursor library [ODBC], statement processing
ms.assetid: 2975dd97-48e6-4d0a-a9c7-40759a7d94c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b3f20da018bcd4e28e8ffca097fb5a4373d7f42
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81308021"
---
# <a name="processing-positioned-update-and-delete-statements"></a>Verarbeiten von positionierten UPDATE- und DELETE-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Die Cursorbibliothek unterstützt positionierte Aktualisierungs- und Löschanweisungen, indem sie die **WHERE CURRENT OF-Klausel** in solchen Anweisungen durch eine **WHERE-Klausel** ersetzt, die die im Cache gespeicherten Werte für jede gebundene Spalte aufzählt. Die Cursorbibliothek übergibt die neu erstellten **UPDATE-** und **DELETE-Anweisungen** zur Ausführung an den Treiber. Bei positionierten Aktualisierungsanweisungen aktualisiert die Cursorbibliothek dann ihren Cache von den Werten in den Rowset-Puffern und legt den entsprechenden Wert im Zeilenstatusarray auf SQL_ROW_UPDATED. Für positionierte löschanweisungen legt sie den entsprechenden Wert im Zeilenstatusarray auf SQL_ROW_DELETED fest.  
  
> [!CAUTION]  
>  Die **WHERE** WHERE-Klausel, die von der Cursorbibliothek erstellt wurde, um die aktuelle Zeile zu identifizieren, kann keine Zeilen identifizieren, eine andere Zeile identifizieren oder mehr als eine Zeile identifizieren. Weitere Informationen finden Sie unter [Erstellen von durchsuchten Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md)weiter unten in diesem Anhang.  
  
 Positionierte Aktualisierungs- und Löschanweisungen unterliegen den folgenden Einschränkungen:  
  
-   Positionierte Aktualisierungs- und Löschanweisungen können nur in den folgenden Fällen verwendet werden: Wenn eine **SELECT-Anweisung** das Resultset generiert hat; wenn die **SELECT-Anweisung** keine Join-, **UNION-Klausel** oder **GROUP BY-Klausel** enthielt; und wenn Spalten, die einen Alias oder Ausdruck in der Auswahlliste verwendet haben, nicht mit **SQLBindCol**gebunden waren.  
  
-   Wenn eine Anwendung eine positionierte Aktualisierungs- oder Löschanweisung vorbereitet, muss sie dies tun, nachdem sie **SQLFetch** oder **SQLFetchScroll**aufgerufen hat. Obwohl die Cursorbibliothek die Anweisung zur Vorbereitung an den Treiber sendet, schließt sie die Anweisung und führt sie direkt aus, wenn die Anwendung **SQLExecute**aufruft.  
  
-   Wenn der Treiber nur eine aktive Anweisung unterstützt, ruft die Cursorbibliothek den Rest des Resultsets ab und ruft dann das aktuelle Rowset aus dem Cache erneut ab, bevor eine positionierte Aktualisierungs- oder Löschanweisung ausgeführt wird. Wenn die Anwendung dann eine Funktion aufruft, die Metadaten in einem Resultset zurückgibt (z. B. **SQLNumResultCols** oder **SQLDescribeCol**), gibt die Cursorbibliothek einen Fehler zurück.  
  
-   Wenn eine positionierte Aktualisierungs- oder Löschanweisung für eine Spalte einer Tabelle ausgeführt wird, die eine Zeitstempelspalte enthält, die bei jeder Aktualisierung automatisch aktualisiert wird, schlagen alle nachfolgenden positionierten Aktualisierungs- oder Löschanweisungen fehl, wenn die Zeitstempelspalte gebunden ist. Dies liegt daran, dass die von der Cursorbibliothek erstellte Such- oder Löschanweisung die zu aktualisierende Zeile nicht genau identifiziert. Der Wert in der gesuchten Anweisung für die Spalte Zeitstempel stimmt nicht mit dem automatisch aktualisierten Wert der Zeitstempelspalte überein.
