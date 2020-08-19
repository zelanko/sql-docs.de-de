---
description: Dynamische ODBC-Cursor
title: Dynamische ODBC-Cursor | Microsoft-Dokumentation
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
ms.openlocfilehash: 19ae15a211329e07fdab13a5b6ff40e210e97cb5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429192"
---
# <a name="odbc-dynamic-cursors"></a>Dynamische ODBC-Cursor
Ein dynamischer Cursor ist genau das: Dynamic. Sie kann alle Änderungen erkennen, die an der Mitgliedschaft, der Reihenfolge und den Werten des Resultsets vorgenommen wurden, nachdem der Cursor geöffnet wurde. Angenommen ein dynamischer Cursor ruft zwei Zeilen ab, und eine andere Anwendung aktualisiert daraufhin eine dieser Zeilen und löscht die andere. Wenn der dynamische Cursor dann versucht, diese Zeilen erneut abzurufen, wird die gelöschte Zeile nicht gefunden, die neuen Werte für die aktualisierte Zeile werden jedoch zurückgegeben.  
  
 Dynamische Cursor erkennen alle Updates, Löschungen und Einfügungen, sowohl eigene als auch andere, die von anderen Benutzern vorgenommen wurden. (Dies unterliegt der Isolationsstufe der Transaktion, die vom SQL_ATTR_TXN_ISOLATION Verbindungs Attribut festgelegt wird.) Das vom Attribut der SQL_ATTR_ROW_STATUS_PTR Anweisung angegebene Zeilen Status Array reflektiert diese Änderungen und kann SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO, SQL_ROW_ERROR, SQL_ROW_UPDATED und SQL_ROW_ADDED enthalten. SQL_ROW_DELETED kann nicht zurückgegeben werden, da ein dynamischer Cursor keine gelöschten Zeilen außerhalb des Rowsets zurückgibt und daher nicht mehr erkennt, dass die gelöschte Zeile im Resultset oder das entsprechende Element im Zeilen Status Array vorhanden ist. SQL_ROW_ADDED wird nur zurückgegeben, wenn eine Zeile durch einen-Befehl von **SQLSetPos**aktualisiert wird, nicht wenn Sie von einem anderen Cursor aktualisiert wird.  
  
 Eine Möglichkeit, dynamische Cursor in der Datenbank zu implementieren, besteht darin, einen selektiven Index zu erstellen, der die Mitgliedschaft und die Reihenfolge des Resultsets definiert. Da der Index aktualisiert wird, wenn andere Benutzer Änderungen vornehmen, ist ein Cursor, der auf einem solchen Index basiert, für alle Änderungen sensibel. Eine zusätzliche Auswahl innerhalb des durch diesen Index definierten Resultsets ist möglich, indem der Index verarbeitet wird.  
  
 Dynamische Cursor können simuliert werden, indem das Resultset nach einem eindeutigen Schlüssel geordnet werden muss. Diese Einschränkung wird durch Ausführen einer **Select** -Anweisung bei jedem Abrufen von Zeilen durch den Cursor durchgeführt. Nehmen wir beispielsweise an, dass das Resultset durch diese Anweisung definiert wird:  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 Um das nächste Rowset in diesem Resultset abzurufen, legt der simulierte Cursor die Parameter in der folgenden **Select** -Anweisung auf die Werte in der letzten Zeile des aktuellen Rowsets fest und führt Sie dann aus:  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 Diese Anweisung erstellt ein zweites Resultset, das erste Rowset, dessen das nächste Rowset im ursprünglichen Resultset ist, in diesem Fall der Satz von Zeilen in der Customers-Tabelle. Der Cursor gibt dieses Rowset an die Anwendung zurück.  
  
 Es ist interessant zu beachten, dass ein dynamischer Cursor, der auf diese Weise implementiert wird, tatsächlich viele Resultsets erstellt, sodass er Änderungen am ursprünglichen Resultset erkennen kann. Die Anwendung erfährt nie, dass diese hilfsresultsets vorhanden sind. Sie wird einfach so angezeigt, als ob der Cursor Änderungen am ursprünglichen Resultset erkennen kann.
