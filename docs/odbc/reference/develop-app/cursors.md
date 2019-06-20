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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91765f0572d8c880f7505948f7756b373fe28f62
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042126"
---
# <a name="cursors"></a>Cursor
Eine Anwendung ruft Daten mit einem *Cursor*. Ein Cursor unterscheidet sich aus einem Resultset: Ein Resultset ist die Menge der Zeilen, die bestimmten Suchkriterien entspricht, während ein Cursor, die Software ist, die diese Zeilen an die Anwendung zurückgibt. Der Name *Cursor* angewendet auf Datenbanken, wahrscheinlich des blinkenden Cursors auf einem Terminalserver Computer stammt. Genau wie dem Cursor gibt an, die aktuelle Position auf dem Bildschirm und, wo die eingegebene Wörter weiter angezeigt wird, gibt einen Cursor in einem Resultset die aktuelle Position im Resultset und welche Zeile neben zurückgegeben werden soll an.  
  
 Das Cursormodell in ODBC basiert auf das Cursormodell in embedded SQL. Ein deutlicher Unterschied zwischen diesen Modellen ist, dass die Möglichkeit Cursor geöffnet werden. In embedded SQL muss ein Cursor explizit deklariert und geöffnet werden, bevor sie verwendet werden kann. In ODBC ist ein Cursor implizit geöffnet, wenn eine Anweisung, die ein Resultset erstellt ausgeführt wird. Wenn der Cursor geöffnet wird, wird es vor der ersten Zeile des Resultsets positioniert. In embedded SQL und ODBC muss ein Cursor geschlossen werden, nach die Anwendung verwenden.  
  
 Verschiedene Cursors haben unterschiedliche Eigenschaften. Die am häufigsten verwendete Typ des Cursors, der aufgerufen wird, eine *Vorwärtscursor,* können über das Resultset nur vorwärts verschoben. Um an einer vorherigen Zeile zurückzugeben, die Anwendung schließen und öffnen den Cursor und liest dann Zeilen vom Anfang des Resultsets, bis sie die erforderliche Zeile erreicht. Vorwärtscursor bieten einen schnellen Mechanismus zum Erstellen von einem einzelnen Durchlauf durch ein Resultset.  
  
 Vorwärtscursor sind weniger nützlich für bildschirmbasierte Anwendungen, in denen der Benutzer rückwärts verschiebt und durch die Daten weiterleiten. Solche Anwendungen können einen Vorwärtscursor verwenden, lesen Sie das Resultset einmal die Daten lokal zwischenspeichern und ausführen, Durchführen eines Bildlaufs selbst. Dies funktioniert jedoch auch nur mit geringen Umfang an Daten. Eine bessere Lösung ist die Verwendung einer *bildlauffähigen Cursor* die wahlfreien Zugriff auf das Resultset bereitstellt. Solche Anwendungen können zu erhöhter Leistung durch Abrufen von mehr als eine Zeile mit Daten zu einem Zeitpunkt mithilfe von sogenannten eine *Blockcursor.* Weitere Informationen zu Blockcursor, finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Die Vorwärtscursor ist der Standardtyp der Cursor in ODBC und wird in den folgenden Abschnitten erläutert. Weitere Informationen zu Blockcursor und bildlauffähigen Cursorn finden Sie unter [Blockcursor](../../../odbc/reference/develop-app/block-cursors.md) und [scrollfähige Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
> [!IMPORTANT]  
>  Ein Commit oder Rollback einer Transaktion, entweder durch explizites Aufrufen von **SQLEndTran** oder indem im Autocommit-Modus ausgeführt wird, bewirkt, dass einige Datenquellen, um alle Cursor für alle Anweisungen für eine Verbindung zu schließen. Weitere Informationen finden Sie auf die SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Attribute in der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung.
