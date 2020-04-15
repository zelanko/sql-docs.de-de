---
title: Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef3cb4095410b8ccb03b0a138f65b8df2cfb1a4b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300470"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen
Das Übertragen oder Zurücksetzen einer Transaktion hat folgende Auswirkungen auf Cursor und Zugriffspläne:  
  
-   Alle Cursor werden geschlossen, und Zugriffspläne für vorbereitete Anweisungen für diese Verbindung werden gelöscht.  
  
-   Alle Cursor werden geschlossen, und Zugriffspläne für vorbereitete Anweisungen für diese Verbindung bleiben intakt.  
  
-   Alle Cursor bleiben geöffnet, und Zugriffspläne für vorbereitete Anweisungen für diese Verbindung bleiben intakt.  
  
 Angenommen, eine Datenquelle weist das erste Verhalten in dieser Liste auf, das restriktivste dieser Verhaltensweisen. Angenommen, eine Anwendung führt die folgenden Schritte aus:  
  
1.  Legt den Commit-Modus auf manuellen Commit fest.  
  
2.  Erstellt eine Ergebnismenge von Aufträgen für Auszug 1.  
  
3.  Erstellt eine Ergebnismenge der Positionen in einem Auftrag in Auszug 2, wenn der Benutzer diesen Auftrag hervorhebt.  
  
4.  Ruft **SQLExecute** auf, um eine positionierte Updateanweisung auszuführen, die für Anweisung 3 vorbereitet wurde, wenn der Benutzer eine Zeile aktualisiert.  
  
5.  Ruft **SQLEndTran** auf, um die positionierte Updateanweisung zu übertragen.  
  
 Aufgrund des Verhaltens der Datenquelle bewirkt der Aufruf von **SQLEndTran** in Schritt 5, dass die Cursor für die Anweisungen 1 und 2 geschlossen und der Zugriffsplan für alle Anweisungen gelöscht wird. Die Anwendung muss die Anweisungen 1 und 2 erneut ausführen, um die Resultsets neu zu erstellen und die Anweisung für Anweisung 3 neu vorzubereiten.  
  
 Im Autocommit-Modus werden andere Funktionen als **SQLEndTran-Commit-Transaktionen** ausgeführt:  
  
-   **SQLExecute** oder **SQLExecDirect** Im vorherigen Beispiel überträgt der Aufruf von **SQLExecute** in Schritt 4 eine Transaktion. Dies bewirkt, dass die Datenquelle die Cursor für die Anweisungen 1 und 2 schließt und den Zugriffsplan für alle Anweisungen in dieser Verbindung löscht.  
  
-   **SQLBulkOperations** oder **SQLSetPos** Im vorherigen Beispiel wird angenommen, dass die Anwendung in Schritt 4 **SQLSetPos** mit der Option SQL_UPDATE für Anweisung 2 aufruft, anstatt eine positionierte Updateanweisung für Anweisung 3 auszuführen. Dadurch wird eine Transaktion übertragen, und die Datenquelle schließt die Cursor für die Anweisungen 1 und 2 und verwirft alle Zugriffspläne für diese Verbindung.  
  
-   **SQLCloseCursor** Angenommen, wenn der Benutzer einen anderen Auftrag hervorhebt, ruft die Anwendung **SQLCloseCursor** auf Anweisung 2 auf, bevor ein Ergebnis der Zeilen für den neuen Auftrag erstellt wird. Der Aufruf von **SQLCloseCursor** überträgt die **SELECT-Anweisung,** die den Ergebnissatz von Zeilen erstellt hat, und bewirkt, dass die Datenquelle den Cursor in Anweisung 1 schließt, und verwirft dann alle Zugriffspläne für diese Verbindung.  
  
 Anwendungen, insbesondere bildschirmbasierte Anwendungen, bei denen der Benutzer einen Bildlauf durch das Resultset führt und Zeilen aktualisiert oder löscht, müssen darauf achten, dieses Verhalten zu codieren.  
  
 Um zu bestimmen, wie sich eine Datenquelle verhält, wenn eine Transaktion festgeschrieben oder zurückgesetzt wird, ruft eine Anwendung **SQLGetInfo** mit den SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Optionen auf.
