---
title: ODBC Dynamische Cursor | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], dynamic
- dynamic cursors [ODBC]
ms.assetid: de709fd3-9eb2-44e1-a2f0-786e2b9602a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f94b83ef1458cd9f8368d1bea3a39682bd80b1a2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302322"
---
# <a name="odbc-dynamic-cursors"></a>Dynamische ODBC-Cursor
Ein dynamischer Cursor ist genau das: dynamisch. Es kann alle Änderungen erkennen, die an der Mitgliedschaft, der Reihenfolge und den Werten des Resultsets vorgenommen wurden, nachdem der Cursor geöffnet wurde. Angenommen ein dynamischer Cursor ruft zwei Zeilen ab, und eine andere Anwendung aktualisiert daraufhin eine dieser Zeilen und löscht die andere. Wenn der dynamische Cursor dann versucht, diese Zeilen erneut abzurufen, wird die gelöschte Zeile nicht gefunden, sondern die neuen Werte für die aktualisierte Zeile zurückgegeben.  
  
 Dynamische Cursor erkennen alle Aktualisierungen, Löschungen und Einfügungen, sowohl ihre eigenen als auch die von anderen. (Dies unterliegt der Isolationsstufe der Transaktion, die durch das SQL_ATTR_TXN_ISOLATION Verbindungsattribut festgelegt wird.) Das vom Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung angegebene Zeilenstatusarray spiegelt diese Änderungen wider und kann SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO, SQL_ROW_ERROR, SQL_ROW_UPDATED und SQL_ROW_ADDED enthalten. Sie kann SQL_ROW_DELETED nicht zurückgeben, da ein dynamischer Cursor keine gelöschten Zeilen außerhalb des Rowsets zurückgibt und daher das Vorhandensein der gelöschten Zeile im Resultset oder des entsprechenden Elements im Zeilenstatusarray nicht mehr erkennt. SQL_ROW_ADDED wird nur zurückgegeben, wenn eine Zeile durch einen Aufruf von **SQLSetPos**aktualisiert wird, nicht wenn sie von einem anderen Cursor aktualisiert wird.  
  
 Eine Möglichkeit zum Implementieren dynamischer Cursor in der Datenbank besteht darin, einen selektiven Index zu erstellen, der die Mitgliedschaft und Reihenfolge des Resultsets definiert. Da der Index aktualisiert wird, wenn andere Änderungen vornehmen, ist ein Cursor, der auf einem solchen Index basiert, für alle Änderungen empfindlich. Eine zusätzliche Auswahl innerhalb des durch diesen Index definierten Resultsets ist durch Verarbeitung entlang des Indexes möglich.  
  
 Dynamische Cursor können simuliert werden, indem das Resultset durch einen eindeutigen Schlüssel sortiert werden muss. Bei einer solchen Einschränkung werden Abrufe durch Ausführen einer **SELECT-Anweisung** jedes Mal durchgeführt, wenn der Cursor Zeilen abruft. Angenommen, das Resultset wird durch diese Anweisung definiert:  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 Um das nächste Rowset in diesem Resultset abzurufen, legt der simulierte Cursor die Parameter in der folgenden **SELECT-Anweisung** auf die Werte in der letzten Zeile des aktuellen Rowsets fest und führt sie dann aus:  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 Diese Anweisung erstellt ein zweites Resultset, dessen erstes Rowset das nächste Rowset im ursprünglichen Resultset ist - in diesem Fall der Satz von Zeilen in der Tabelle Customers. Der Cursor gibt dieses Rowset an die Anwendung zurück.  
  
 Es ist interessant festzustellen, dass ein dynamischer Cursor, der auf diese Weise implementiert wird, tatsächlich viele Resultsets erstellt, wodurch er Änderungen am ursprünglichen Resultset erkennen kann. Die Anwendung erfährt nie von der Existenz dieser Hilfsergebnissätze; Es scheint einfach so zu sein, als ob der Cursor in der Lage ist, Änderungen am ursprünglichen Resultset zu erkennen.
