---
title: Blockieren von Cursorn | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306351"
---
# <a name="block-cursors"></a>Blockcursor
Viele Anwendungen verbringen viel Zeit mit dem Datenüberführen über das Netzwerk. Ein Teil dieser Zeit wird tatsächlich für das Zusammenführen der Daten über das Netzwerk aufgewendet, und ein Teil davon wird für den Netzwerkaufwand aufgewendet, z. B. für den Anruf des Treibers, um eine Datenzeile anzufordern. Die letztgenannte Zeit kann reduziert *werden,* wenn die Anwendung block- oder *fette* Cursor effizient *nutzt,* die mehr als eine Zeile gleichzeitig zurückgeben können.  
  
 Eine Anwendung hat immer die Möglichkeit, einen Blockcursor zu verwenden. Bei Datenquellen, aus denen jeweils nur eine Zeile abgerufen werden kann, müssen Blockcursor im Treiber simuliert werden. Dies kann durch mehrere einzeilige Abrufe erfolgen. Obwohl dies wahrscheinlich keine Leistungssteigerungen mit sich bringt, eröffnet es Möglichkeiten für Anwendungen. Solche Anwendungen werden dann Leistungssteigerungen erfahren, da DBMS Blockcursor nativ implementieren und die treiber, die mit diesen DBMS verknüpft sind, sie verfügbar machen.  
  
 Die Zeilen, die in einem einzelnen Abruf mit einem Blockcursor zurückgegeben werden, werden *rowset*genannt. Es ist wichtig, das Rowset nicht mit dem Resultset zu verwechseln. Das Resultset wird an der Datenquelle beibehalten, während das Rowset in Anwendungspuffern verwaltet wird. Während das Resultset fixiert ist, ist das Rowset nicht - es ändert Position und Inhalt jedes Mal, wenn ein neuer Satz von Zeilen abgerufen wird. Genauso wie ein cursorer cursor, wie der herkömmliche SQL-Forward-Cursor, auf eine aktuelle Zeile zeigt, zeigt ein Blockcursor auf das Rowset, das als *aktuelle Zeilen*betrachtet werden kann.  
  
 Um Vorgänge auszuführen, die für eine einzelne Zeile ausgeführt werden, wenn mehrere Zeilen abgerufen wurden, muss die Anwendung zuerst angeben, welche Zeile die aktuelle Zeile ist. Die aktuelle Zeile wird durch Aufrufe von **SQLGetData** und positionierte Aktualisierungs- und Löschanweisungen benötigt. Wenn ein Blockcursor zuerst ein Rowset zurückgibt, ist die aktuelle Zeile die erste Zeile des Rowsets. Um die aktuelle Zeile zu ändern, ruft die Anwendung **SQLSetPos** oder **SQLBulkOperations** auf (um sie nach Lesezeichen zu aktualisieren). Die folgende Abbildung zeigt die Beziehung zwischen Resultset, Rowset, aktueller Zeile, Rowset-Cursor und Blockcursor. Weitere Informationen finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md)weiter unten in diesem Abschnitt sowie [In Position Update and Delete Statements](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) and Updating Data with [SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
 ![Abrufen des nächsten, des vorherigen, des ersten und des letzten Rowsets](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 Ob ein Cursor ein Blockcursor ist, hängt davon ab, ob er scrollbar ist. Beispielsweise wird der größte Teil der Arbeit in einer Berichtsanwendung für das Abrufen und Drucken von Zeilen aufgewendet. Aus diesem Grund funktioniert es am schnellsten mit einem vorwärts-nur, Blockcursor. Es verwendet einen Vorwärts-Cursor, um die Kosten eines scrollbaren Cursors zu vermeiden, und einen Blockcursor, um den Netzwerkverkehr zu reduzieren.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Spalten für die Verwendung mit Blockcursorn](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [Zeilenstatusarray](../../../odbc/reference/develop-app/row-status-array.md)
