---
title: Blockieren von Cursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 1a92b5d8-7c6e-4ce5-8c99-600a387026aa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc62e7b5225c434bac33630f2f0cf8f39c72bfc9
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52504677"
---
# <a name="block-cursors"></a>Blockcursor
Viele Anwendungen verbringen viel Zeit, die Daten über das Netzwerk eingebunden. Teil dieser Zeit aufgewendet tatsächlich die Daten über das Netzwerk eingebunden und Teil davon ist für die netzwerkbelastung, aufgewendet, z. B. des Aufrufs durch den Treiber, um eine Zeile mit Daten anzufordern. Die letztere Zeit reduziert werden kann, wenn die Anwendung effizient nutzt *Block* oder *Fat,* *Cursorn* die kann mehr als eine Zeile zurückgeben, zu einem Zeitpunkt.  
  
 Eine Anwendung immer aufweist die Möglichkeit, mithilfe eines Blockcursors Für Datenquellen, die von denen nur eine Zeile zu einem Zeitpunkt abgerufen werden kann, müssen die Blockcursor im Treiber simuliert werden. Dies kann durch Ausführen von mehreren einzelnen Zeile ruft erfolgen. Obwohl dies Leistungssteigerungen bieten wahrscheinlich ist, wird er Möglichkeiten für Anwendungen geöffnet. Solche Anwendungen treten klicken Sie dann eine Steigerung der Leistung eines DBMS implementieren Blockcursor nativ und Verfügbarmachen der Treiber die DBMS-Systeme zugeordnet.  
  
 In einer einzigen Abfrage mit einem Blockcursor zurückgegebenen Zeilen heißen die *Rowset*. Es ist wichtig, nicht das Rowset mit dem Resultset zu verwechseln. Das Resultset wird in der Datenquelle beibehalten, während das Rowset Anwendungspuffer beibehalten wird. Obwohl Resultset behoben ist, das Rowset wird nicht: Es ändert seine Position und Inhalt jedes Mal, wenn eine neue Gruppe von Zeilen abgerufen werden. Nur als einzelne Zeile Cursor wie z. B. die herkömmlichen SQL-Vorwärtscursor-verweist auf eine aktuelle Zeile als Blockcursor verweist, auf das Rowset, das als vorstellen kann *aktuelle Zeilen*.  
  
 Für die Durchführung einer einzelnen Zeile Vorgänge, die ausgeführt werden, wenn mehrere Zeilen abgerufen wurden, muss die Anwendung zuerst angeben, welche Zeile der aktuellen Zeile ist. Die aktuelle Zeile muss durch Aufrufe von **SQLGetData** positioniert Update und delete-Anweisungen. Wenn einem Blockcursor ein Rowset zuerst zurückgegeben wird, ist die aktuelle Zeile die erste Zeile des Rowsets. So ändern Sie die aktuelle Zeile, die Anwendung ruft **SQLSetPos** oder **SQLBulkOperations** (zum Aktualisieren von Lesezeichen). Die folgende Abbildung zeigt die Beziehung zwischen der Resultset-Rowset, aktuelle Zeile, Rowset-Cursor und Blockcursor. Weitere Informationen finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md)weiter unten in diesem Abschnitt und [positioniert Update- und Delete-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) und [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
 ![Abrufen des nächsten, vorherigen, ersten und letzten Rowsets](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 Ob ein Cursor als Blockcursor ist ist unabhängig von, ob es bildlauffähig ist. Zum Beispiel die meiste Arbeit in einer Berichtsserver-Anwendung wird aufgewendet, abrufen und Drucken von Zeilen. Aus diesem Grund wird es funktionieren am schnellsten mit einem Vorwärtscursor, Blockcursor. Er verwendet einen Vorwärtscursor, um vermeiden Sie die Kosten für einen bildlauffähigen Cursor und einem Blockcursor, um den Netzwerkdatenverkehr zu reduzieren.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Binden von Spalten für die Verwendung mit Blockcursorn](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [Zeilenstatusarray](../../../odbc/reference/develop-app/row-status-array.md)
