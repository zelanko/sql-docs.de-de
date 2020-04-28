---
title: Blockcursor | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa35888ef93da9648fe6422bdc35ebf9da3a0525
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306351"
---
# <a name="block-cursors"></a>Blockcursor
Viele Anwendungen verbringen einen beträchtlichen Zeitaufwand für das Übertragen von Daten über das Netzwerk. Ein Teil dieses Zeitraums ist das eigentliche Einbinden der Daten über das Netzwerk, und ein Teil davon ist für den Netzwerk Aufwand aufgewendet, z. b. durch den Aufruf des Treibers, eine Daten Zeile anzufordern. Die letztgenannte Zeit kann reduziert werden, wenn die Anwendung eine effiziente Verwendung von *Block* -oder *FAT* - *Cursorn* durchführt, die mehrere Zeilen gleichzeitig zurückgeben können.  
  
 Eine Anwendung hat immer die Möglichkeit, einen Block Cursor zu verwenden. Für Datenquellen, aus denen jeweils nur eine Zeile abgerufen werden kann, müssen Blockcursorn im Treiber simuliert werden. Dies können Sie erreichen, indem Sie mehrere einzeilige Abruf Vorgänge ausführen. Obwohl es unwahrscheinlich ist, dass es zu Leistungssteigerungen kommt, öffnet es die Möglichkeiten für Anwendungen. Bei solchen Anwendungen kommt es zu Leistungssteigerungen, da DBMSs Blockcursorn System intern implementiert, und die mit diesen DBMSs verknüpften Treiber machen Sie verfügbar.  
  
 Die Zeilen, die in einem einzelnen Fetch mit einem Block Cursor zurückgegeben werden, werden als *Rowset*bezeichnet. Es ist wichtig, das Rowset nicht mit dem Resultset zu verwechseln. Das Resultset wird in der Datenquelle beibehalten, während das Rowset in Anwendungs Puffern verwaltet wird. Obwohl das Resultset korrigiert ist, ändert sich das Rowset nicht. es ändert die Position und den Inhalt jedes Mal, wenn ein neuer Satz von Zeilen abgerufen wird. Ebenso wie ein Cursor mit einer Zeile, z. b. der herkömmliche SQL-Vorwärts Cursor, auf eine aktuelle Zeile zeigt, zeigt ein Block Cursor auf das Rowset, das als *Aktuelle Zeilen*betrachtet werden kann.  
  
 Zum Ausführen von Vorgängen, die mit einer einzelnen Zeile arbeiten, wenn mehrere Zeilen abgerufen wurden, muss die Anwendung zuerst angeben, welche Zeile die aktuelle Zeile ist. Die aktuelle Zeile ist für Aufrufe von **SQLGetData** und positionierte UPDATE-und DELETE-Anweisungen erforderlich. Wenn ein Block Cursor zuerst ein Rowset zurückgibt, ist die aktuelle Zeile die erste Zeile des Rowsets. Um die aktuelle Zeile zu ändern, ruft die Anwendung **SQLSetPos** oder **SQLBulkOperations** auf (zum Aktualisieren durch Lesezeichen). Die folgende Abbildung zeigt die Beziehung des Resultsets, des Rowsets, der aktuellen Zeile, des Rowsetcursors und des Block Cursors. Weitere Informationen finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md)weiter unten in diesem Abschnitt und [positionierte UPDATE-und DELETE-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) und [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
 ![Abrufen des nächsten, des vorherigen, des ersten und des letzten Rowsets](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 Ob ein Cursor ein Block Cursor ist, ist unabhängig davon, ob er scrollfähig ist. Beispielsweise wird für den größten Teil der Arbeit in einer Berichts Anwendung das Abrufen und Drucken von Zeilen aufgewendet. Aus diesem Grund funktioniert es am schnellsten mit einem vorwärts-, Block Cursor. Es verwendet einen Vorwärts Cursor, um die Kosten eines scrollbaren Cursors zu vermeiden, und einen Block Cursor, um den Netzwerk Datenverkehr zu reduzieren.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Spalten für die Verwendung mit Blockcursorn](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [Zeilenstatusarray](../../../odbc/reference/develop-app/row-status-array.md)
