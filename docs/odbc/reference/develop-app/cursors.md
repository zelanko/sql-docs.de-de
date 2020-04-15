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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305291"
---
# <a name="cursors"></a>Cursor
Eine Anwendung ruft Daten mit einem *Cursor*ab. Ein Cursor unterscheidet sich von einem Resultset: Ein Resultset ist der Satz von Zeilen, der bestimmten Suchkriterien entspricht, während ein Cursor die Software ist, die diese Zeilen an die Anwendung zurückgibt. Der *Namenscursor,* wie er für Datenbanken gilt, stammt wahrscheinlich vom blinkenden Cursor auf einem Computerterminal. Genauso wie dieser Cursor die aktuelle Position auf dem Bildschirm angibt und wo die eingegebenen Wörter als nächstes angezeigt werden, zeigt ein Cursor eines Resultsets die aktuelle Position im Resultset an und welche Zeile als nächstes zurückgegeben wird.  
  
 Das Cursormodell in ODBC basiert auf dem Cursormodell in Embedded SQL. Ein bemerkenswerter Unterschied zwischen diesen Modellen ist die Art und Weise, wie Cursor geöffnet werden. In Embedded SQL muss ein Cursor explizit deklariert und geöffnet werden, bevor er verwendet werden kann. In ODBC wird ein Cursor implizit geöffnet, wenn eine Anweisung ausgeführt wird, die ein Resultset erstellt. Wenn der Cursor geöffnet wird, wird er vor der ersten Zeile des Resultsets positioniert. Sowohl in Embedded SQL als auch in ODBC muss ein Cursor geschlossen werden, nachdem die Anwendung ihn verwendet hat.  
  
 Verschiedene Cursor haben unterschiedliche Eigenschaften. Der häufigste Cursortyp, der als Vorwärtscursor bezeichnet *wird,* kann nur durch das Resultset vorwärts bewegt werden. Um zu einer vorherigen Zeile zurückzukehren, muss die Anwendung den Cursor schließen und erneut öffnen und dann Zeilen vom Anfang des Resultsets lesen, bis sie die erforderliche Zeile erreicht. Vorwärtscursor bieten einen schnellen Mechanismus, um einen einzelnen Durchgang durch ein Resultset zu machen.  
  
 Vorwärtscursor sind weniger nützlich für bildschirmbasierte Anwendungen, bei denen der Benutzer durch die Daten hin- und herscrollt. Solche Anwendungen können einen Vorwärtscursor verwenden, indem sie das Resultset einmal lesen, die Daten lokal zwischenspeichern und selbst einen Bildlauf durchführen. Dies funktioniert jedoch nur bei kleinen Datenmengen. Eine bessere Lösung besteht darin, einen *scrollbaren Cursor* zu verwenden, der zufälligen Zugriff auf das Resultset bietet. Solche Anwendungen können auch die Leistung erhöhen, indem sie mehr als eine Zeile daten gleichzeitig abrufen, indem sie einen so genannten *Blockcursor verwenden.* Weitere Informationen zu Blockcursorn finden Sie unter [Verwenden von Blockcursors](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Der Forward-Only-Cursor ist der Standardcursortyp in ODBC und wird in den folgenden Abschnitten erläutert. Weitere Informationen zu Blockcursorn und scrollbaren Cursorn finden Sie unter [Blockcursor und](../../../odbc/reference/develop-app/block-cursors.md) [Scrollable Cursors](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
> [!IMPORTANT]  
>  Das Commit oder Rollback einer Transaktion, entweder durch explizites Aufrufen von **SQLEndTran** oder durch Ausführen von AutoCommit-Modus, bewirkt, dass einige Datenquellen alle Cursor für alle Anweisungen für eine Verbindung schließen. Weitere Informationen finden Sie in den SQL_CURSOR_COMMIT_BEHAVIOR- und SQL_CURSOR_ROLLBACK_BEHAVIOR-Attributen in der [SQLGetInfo-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetinfo-function.md)
