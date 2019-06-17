---
title: Dynamische Cursor von ODBC | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64215cff750e39dc78ad1a695bbe553d900f4120
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312873"
---
# <a name="odbc-dynamic-cursors"></a>Dynamische ODBC-Cursor
Ein dynamischer Cursor handelt es sich um: dynamische. Sie können erkennen, dass alle Änderungen an der Mitgliedschaft, Reihenfolge und Werte des Resultsets nach der der Cursor geöffnet wird. Angenommen ein dynamischer Cursor ruft zwei Zeilen ab, und eine andere Anwendung aktualisiert daraufhin eine dieser Zeilen und löscht die andere. Wenn der dynamische Cursor anschließend versucht, diese Zeilen erneut abzurufen, die gelöschte Zeile nicht gefunden, aber neue Werte für die aktualisierte Zeile zurück.  
  
 Dynamische Cursor erkennen alle Updates, Lösch- und Einfügevorgänge, sowohl ihre eigenen und die von anderen Benutzern. (Dies unterliegt die Isolation von der Transaktion, wie durch das Verbindungsattribut SQL_ATTR_TXN_ISOLATION festgelegt.) Zeilenstatusarray, die vom Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung angegebenen diese Änderungen und SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO, SQL_ROW_ERROR, SQL_ROW_UPDATED und SQL_ROW_ADDED enthalten kann. Es kann nicht SQL_ROW_DELETED zurückgegeben, da ein dynamic-Cursor keinen gelöschten Zeilen, die außerhalb des Rowsets zurückgibt und daher nicht mehr das Vorhandensein von die gelöschte Zeile im Resultset oder das entsprechende Element in der zeilenstatusarray erkennt. SQL_ROW_ADDED wird nur zurückgegeben, wenn eine Zeile, durch einen Aufruf von aktualisiert wird **SQLSetPos**, nicht verwendet werden, wenn sie von einem anderen Cursor aktualisiert wird.  
  
 Eine Möglichkeit zum Implementieren von dynamischer Cursors in der Datenbank wird durch Erstellen eines selektive Index, das definiert, die Mitgliedschaft und Sortierung des Resultsets festgelegt. Da der Index aktualisiert wird, wenn andere Änderungen vornehmen, ist ein Cursor, die basierend auf solchen Index alle Änderungen. Zusätzliche Auswahl innerhalb des Resultsets, die von diesem Index definiert ist durch die Verarbeitung auf den Index möglich.  
  
 Dynamische Cursor können durch das Anfordern von des Resultsets auf die durch einen eindeutigen Schlüssel sortiert werden simuliert werden. Durch eine solche Einschränkung Abrufvorgänge erfolgen Ausführen einer **wählen** Anweisung jedes Mal, die der Cursor ruft Zeilen ab. Nehmen wir beispielsweise an das Resultset von dieser Anweisung definiert ist:  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 Zum Abrufen des nächsten Rowsets in diesem Resultset des Cursors simulierten legt für die Parameter in der folgenden **wählen** Anweisung, um die Werte in der letzten Zeile des aktuellen Rowsets, und anschließend ausgeführt:  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 Diese Anweisung erstellt eine zweite Resultset, das erste Rowset, von denen des nächsten Rowsets im ursprünglichen Resultset – in diesem Fall ist, den Satz von Zeilen in der Customers-Tabelle. Der Cursor an die Anwendung das folgende Rowset zurückgibt.  
  
 Es ist interessant, beachten Sie, dass ein dynamischer Cursor, die auf diese Weise implementiert tatsächlich viele Resultsets erstellt, wodurch Änderungen an der ursprünglichen Resultset zu erkennen. Die Anwendung nie erfährt von der Existenz von dieser zusätzlichen Resultsets; Sie wird lediglich angezeigt, als wenn der Cursor kann Änderungen an der ursprünglichen Resultset zu erkennen ist.
