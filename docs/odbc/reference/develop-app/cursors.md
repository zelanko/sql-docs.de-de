---
title: Cursors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- forward-only cursors [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], about cursors
- cursors [ODBC]
- fetches [ODBC], cursors
- result sets [ODBC], fetching
- block cursors [ODBC]
ms.assetid: 0b114352-3c63-4d33-9220-182ede90e4aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da899e4dc47daff03c31277b3edd4d9c642b87cb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305291"
---
# <a name="cursors"></a>Cursor
Eine Anwendung ruft Daten mit einem *Cursor*ab. Ein Cursor unterscheidet sich von einem Resultset: ein Resultset ist der Satz von Zeilen, der bestimmte Suchkriterien erfüllt, wohingegen es sich bei einem Cursor um die Software handelt, die diese Zeilen an die Anwendung zurückgibt. Der namens *Cursor,* wie er auf Datenbanken angewendet wird, stammt wahrscheinlich vom blinkende Cursor auf einem Computerterminal. Ebenso wie dieser Cursor die aktuelle Position auf dem Bildschirm anzeigt und wo die typisierten Wörter als nächstes angezeigt werden, gibt ein Cursor in einem Resultset die aktuelle Position im Resultset an und welche Zeile als nächstes zurückgegeben wird.  
  
 Das Cursor Modell in ODBC basiert auf dem Cursor Modell in eingebettetem SQL. Ein wichtiger Unterschied zwischen diesen Modellen ist die Art und Weise, wie Cursor geöffnet werden. In eingebettetem SQL muss ein Cursor explizit deklariert und geöffnet werden, bevor er verwendet werden kann. In ODBC wird ein Cursor implizit geöffnet, wenn eine Anweisung ausgeführt wird, die ein Resultset erstellt. Wenn der Cursor geöffnet wird, wird er vor der ersten Zeile des Resultsets positioniert. In eingebetteten SQL und ODBC muss ein Cursor geschlossen werden, nachdem er von der Anwendung verwendet wurde.  
  
 Verschiedene Cursor haben unterschiedliche Eigenschaften. Der häufigste Cursortyp, der als *Vorwärts Cursor* bezeichnet wird, kann nur durch das Resultset vorwärts verschoben werden. Um zu einer vorherigen Zeile zurückzukehren, muss die Anwendung den Cursor schließen und erneut öffnen und dann Zeilen vom Anfang des Resultsets lesen, bis die erforderliche Zeile erreicht ist. Vorwärts Cursor bieten einen schnellen Mechanismus zum Durchführen eines einzelnen Durchlaufs eines Resultsets.  
  
 Vorwärts Cursor sind weniger nützlich für bildschirmbasierte Anwendungen, in denen der Benutzer einen rückwärts-und vorwärts Bildlauf durch die Daten ausführt. Solche Anwendungen können einen Vorwärts Cursor verwenden, indem Sie das Resultset einmal lesen, die Daten lokal zwischenspeichern und einen Bildlauf durchführen. Dies funktioniert jedoch nur mit kleinen Datenmengen. Eine bessere Lösung ist die Verwendung eines *scrollbaren Cursors,* der zufälligen Zugriff auf das Resultset bereitstellt. Solche Anwendungen können auch die Leistung erhöhen, indem Sie mehr als eine Zeile mit Daten gleichzeitig abrufen, indem Sie als *Block Cursor* bezeichnet werden. Weitere Informationen zu Blockcursorn finden [Sie unter Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Der Vorwärts Cursor ist der Standard Cursortyp in ODBC und wird in den folgenden Abschnitten erläutert. Weitere Informationen zu Blockcursorn und scrollfähigen Cursorn finden Sie unter [Blockieren von Cursorn](../../../odbc/reference/develop-app/block-cursors.md) und [scrollbaren Cursorn](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
> [!IMPORTANT]  
>  Das Ausführen eines Commits oder Rollbacks einer Transaktion durch explizites Aufrufen von **SQLEndTran** oder durch Betrieb im Autocommit-Modus bewirkt, dass einige Datenquellen alle Cursor in allen Anweisungen für eine Verbindung schließen. Weitere Informationen finden Sie in den SQL_CURSOR_COMMIT_BEHAVIOR-und SQL_CURSOR_ROLLBACK_BEHAVIOR-Attributen in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion.
