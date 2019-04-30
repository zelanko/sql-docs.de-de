---
title: Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- cursors [ODBC], transaction commits or roll backs
- prepared statements [ODBC]
- transactions [ODBC], cursors
ms.assetid: 523e22a2-7b53-4c25-97c1-ef0284aec76e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41c2c6b06744965144ca9d5feb27e9ea16d9903c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63305715"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen
Durch Commit oder Rollback wurde eine Transaktion folgende Auswirkungen auf Cursor und Zugriffspläne auf:  
  
-   Alle Cursor geschlossen werden, und Access-Pläne für vorbereitete Anweisungen für diese Verbindung werden gelöscht.  
  
-   Alle Cursor geschlossen werden, und Access-Pläne für vorbereitete Anweisungen für diese Verbindung erhalten bleiben.  
  
-   Alle Cursor geöffnet bleiben, und Zugriffspläne für vorbereitete Anweisungen für diese Verbindung erhalten bleiben.  
  
 Nehmen wir beispielsweise an, dass eine Datenquelle die erste Verhalten in dieser Liste, die die restriktivste dieser Verhalten zeigt. Jetzt nehmen wir an eine Anwendung, die wie folgt vorgeht:  
  
1.  Legt den Commit-Modus auf Manualcommit-fest.  
  
2.  Erstellt ein Resultset von Verkaufsaufträgen in 1-Anweisung.  
  
3.  Erstellt ein Resultset Zeilen in einem Verkaufsauftrag in 2-Anweisung ein, wenn der Benutzer mit dieser Reihenfolge werden hervorgehoben.  
  
4.  Aufrufe **SQLExecute** eine positioniertes Update-Anweisung, die vorbereitet wurde auf 3,-Anweisung ausgeführt wird, wenn der Benutzer eine Zeile aktualisiert.  
  
5.  Aufrufe **SQLEndTran** um die positionierte Update-Anweisung zu übernehmen.  
  
 Aufgrund der Datenquelle des Verhaltens der Aufruf von **SQLEndTran** in Schritt 5 bewirkt, dass beim Löschen des Zugriffsplans für alle Anweisungen und schließen Sie den Cursor auf 1 und 2-Anweisungen. Die Anwendung muss but Sätze von Anweisungen, 1 und 2, um das Ergebnis erneut zu erstellen und die Anweisung für Anweisung 3 reprepare.  
  
 Im Autocommit-Modus Funktionen anderen Funktionen als **SQLEndTran** commit der Transaktionen:  
  
-   **SQLExecute** oder **SQLExecDirect** im vorherigen Beispiel der Aufruf von **SQLExecute** in Schritt 4 führt einen Commit für eine Transaktion. Dies bewirkt, dass die Datenquelle zum Schließen der Cursor auf 1 und 2-Anweisungen und den Zugriffsplan für alle Anweisungen für diese Verbindung löschen.  
  
-   **SQLBulkOperations** oder **SQLSetPos** im vorherigen Beispiel nehmen wir an, dass in Schritt 4 die Anwendung ruft **SQLSetPos** mit der Option SQL_UPDATE auf 2,-Anweisung anstelle der Ausführung ein positioniertes Update-Anweisung für Anweisung 3. Dies führt einen Commit für eine Transaktion und führt dazu, dass die Datenquelle aus, um den Cursor auf 1 und 2-Anweisungen zu schließen, und verwirft alle Access-Pläne für die Verbindung.  
  
-   **SQLCloseCursor** im vorherigen Beispiel nehmen wir an, dass wenn der Benutzer auf einen anderen Auftrag highlights, die Anwendung ruft **SQLCloseCursor** in 2-Anweisung vor dem Erstellen ein Ergebnis der Zeilen für die neue Umsätze die Reihenfolge. Der Aufruf von **SQLCloseCursor** führt einen Commit für die **wählen** Anweisung, erstellt das Resultset Zeilen und bewirkt, dass die Datenquelle zum Schließen des Cursors in 1-Anweisung, und klicken Sie dann verwirft alle Access-Pläne auf, die, die Verbindung.  
  
 Anwendungen, vor allem bildschirmbasierte Anwendungen in der der Benutzer einen Bildlauf durchführt, um die Resultsets und Updates, oder löscht Zeilen, müssen darauf achten, dass Code, um dieses Problem sein.  
  
 Um zu bestimmen, wie eine Datenquelle verhält, wenn eine Transaktion ein Commit oder Rollback ist, eine Anwendung ruft **SQLGetInfo** mit den Optionen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR.
