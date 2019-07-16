---
title: Verarbeitung positioniert, Update und Delete-Anweisungen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 41b4fe248f815e63c48a8da70edc88a1cc173667
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028436"
---
# <a name="processing-positioned-update-and-delete-statements"></a>Verarbeiten von positionierten UPDATE- und DELETE-Anweisungen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Der Cursor-Bibliothek unterstützt positioniert update und delete-Anweisungen durch Ersetzen der **WHERE CURRENT OF** -Klausel in eine solche Anweisungen mit einem **, in dem** -Klausel, die in seinem Cache nach gespeicherten Werte zählt jede gebundene Spalte. Die Cursorbibliothek übergibt das neu erstellte **UPDATE** und **löschen** Anweisungen an den Treiber für die Ausführung. Für positionierte Update-Anweisungen die Cursorbibliothek anschließend aktualisiert seinen Cache aus den Werten in den Puffern Rowset und den entsprechenden Wert in der zeilenstatusarray zu SQL_ROW_UPDATED. Für positionierte Delete-Anweisungen legt er den entsprechenden Wert im Array Zeile Status SQL_ROW_DELETED fest.  
  
> [!CAUTION]  
>  Die **, in denen** Klausel erstellt, die von der Cursorbibliothek zum Identifizieren der aktuellen Zeile kann möglicherweise keine Zeilen zu identifizieren, identifizieren eine andere Zeile oder mehr als eine Zeile zu identifizieren. Weitere Informationen finden Sie unter [durchsucht-Anweisungen konstruieren](../../../odbc/reference/appendixes/constructing-searched-statements.md)weiter unten in diesem Anhang.  
  
 Positioniert die Update- und Delete-Anweisungen sind jedoch mit folgenden Einschränkungen:  
  
-   Positioniert, Update- und Delete Anweisungen können nur in den folgenden Fällen verwendet werden: beim eine **wählen** -Anweisung generiert das Resultset auf; Wenn die **wählen** Anweisung enthielt keine Verknüpfung eine  **UNION** -Klausel oder eine **GROUP BY** -Klausel; und wenn alle Spalten, die einen Alias oder ein Ausdruck in der select-Liste verwendet, nicht mit gebunden wurden **SQLBindCol**.  
  
-   Wenn eine Anwendung ein positioniertes Update oder Delete-Anweisung vorbereitet, sie müssen dazu nach aufgerufen wurde **SQLFetch** oder **SQLFetchScroll**. Obwohl die Cursorbibliothek die Anweisung an den Treiber für die datenvorbereitung übermittelt, wird die Anweisung und führt ihn direkt, wenn die Anwendung aufruft **SQLExecute**.  
  
-   Wenn der Treiber nur eine aktive Anweisung unterstützt, wird der Cursor-Bibliothek Ruft, die der Rest des Ergebnisses wird festgelegt, und klicken Sie dann das aktuelle Rowset aus seinem Cache refetches, vor dem Ausführen einer positionierten, aktualisieren oder delete-Anweisung. Wenn die Anwendung dann eine Funktion aufruft, der Metadaten in einem Resultset zurückgibt (z. B. **SQLNumResultCols** oder **SQLDescribeCol**), die Cursorbibliothek gibt einen Fehler zurück.  
  
-   Wenn ein positioniertes Update oder Delete-Anweisung für eine Spalte einer Tabelle ausgeführt wird, die eine Timestamp-Spalte enthält, die automatisch aktualisiert wird, jedes Mal, wenn ein Update ausgeführt wird, werden alle nachfolgenden positionierte Update- oder Delete-Anweisungen fehl, wenn die Timestamp-Spalte ist gebunden. Dies tritt auf, wenn die gesuchten update oder delete-Anweisung, die Cursorbibliothek erstellt, nicht genau die zu aktualisierende Zeile identifiziert wird. Der Wert in der komplexen Anweisung für die Timestamp-Spalte entspricht nicht den automatisch aktualisierten Wert für die Timestamp-Spalte.
