---
title: Auswirkung von Transaktionen auf Cursor und vorbereitete Anweisungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300470"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen
Das Ausführen eines Commits oder Rollbacks einer Transaktion hat die folgenden Auswirkungen auf Cursor und Zugriffs Pläne:  
  
-   Alle Cursor werden geschlossen, und Zugriffs Pläne für vorbereitete Anweisungen für diese Verbindung werden gelöscht.  
  
-   Alle Cursor werden geschlossen, und Zugriffs Pläne für vorbereitete Anweisungen für diese Verbindung bleiben intakt.  
  
-   Alle Cursor bleiben geöffnet, und Zugriffs Pläne für vorbereitete Anweisungen für diese Verbindung bleiben intakt.  
  
 Nehmen wir beispielsweise an, dass eine Datenquelle das erste Verhalten in dieser Liste, die restriktivste dieser Verhaltensweisen, aufweist. Angenommen, eine Anwendung führt Folgendes aus:  
  
1.  Legt den Commitmodus auf manuelles Commit fest.  
  
2.  Erstellt ein Resultset von Verkaufsaufträgen für Anweisung 1.  
  
3.  Erstellt ein Resultset der Zeilen in einem Verkaufsauftrag für Anweisung 2, wenn der Benutzer diese Bestellung hervorhebt.  
  
4.  Ruft **SQLExecute** auf, um eine positionierte UPDATE-Anweisung auszuführen, die auf Anweisung 3 vorbereitet wurde, wenn der Benutzer eine Zeile aktualisiert.  
  
5.  Ruft **SQLEndTran** auf, um die positionierte UPDATE-Anweisung zu übertragen.  
  
 Aufgrund des Verhaltens der Datenquelle bewirkt der **SQLEndTran** -Befehl in Schritt 5, dass die Cursor in den Anweisungen 1 und 2 geschlossen werden und der Zugriffs Plan für alle Anweisungen gelöscht wird. Die Anwendung muss die Anweisungen 1 und 2 erneut ausführen, um die Resultsets neu zu erstellen und die Anweisung für Anweisung 3 erneut vorzubereiten.  
  
 Im Autocommit-Modus sind andere Funktionen als **SQLEndTran** Commit-Transaktionen:  
  
-   **SQLExecute** oder **SQLExecDirect** im vorherigen Beispiel führt der **SQLExecute** -Befehl in Schritt 4 einen Commit für eine Transaktion aus. Dies bewirkt, dass die Datenquelle die Cursor in den Anweisungen 1 und 2 schließt und den Zugriffs Plan für alle Anweisungen über diese Verbindung löscht.  
  
-   **SQLBulkOperations** oder **SQLSetPos** im vorherigen Beispiel, angenommen, die Anwendung ruft **SQLSetPos** mit der Option SQL_UPDATE für Anweisung 2 auf, anstatt eine positionierte UPDATE-Anweisung für Anweisung 3 auszuführen. Dies führt einen Commit für eine Transaktion aus und bewirkt, dass die Datenquelle die Cursor in den Anweisungen 1 und 2 schließt und alle Zugriffs Pläne für diese Verbindung verwirft.  
  
-   **SQLCloseCursor** Angenommen, wenn der Benutzer einen anderen Verkaufsauftrag hervorhebt, ruft die Anwendung **SQLCloseCursor** für Anweisung 2 auf, bevor er ein Ergebnis der Zeilen für den neuen Verkaufsauftrag erstellt. Der **SQLCloseCursor** -Befehl führt einen Commit für die **Select** -Anweisung aus, die das Resultset von Zeilen erstellt hat, und bewirkt, dass die Datenquelle den Cursor in Anweisung 1 schließt und dann alle Zugriffs Pläne für diese Verbindung verwirft.  
  
 Anwendungen, insbesondere bildschirmbasierte Anwendungen, in denen der Benutzer einen Bildlauf um das Resultset durchführt und Zeilen aktualisiert oder löscht, müssen vorsichtig sein, um dieses Verhalten zu umgehen.  
  
 Um zu ermitteln, wie sich eine Datenquelle verhält, wenn für eine Transaktion ein Commit oder ein Rollback ausgeführt wird, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR auf.
