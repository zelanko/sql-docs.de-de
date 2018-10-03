---
title: Abrufen und Aktualisieren von Rowsets (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc6a5254afc715a950f2d3c63d02bfca7a1890ea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076580"
---
# <a name="fetch-and-update-rowsets-odbc"></a>Abfragen und Aktualisieren von Rowsets (ODBC)
    
### <a name="to-fetch-and-update-rowsets"></a>So können Sie Rowsets abfragen und aktualisieren  
  
1.  Rufen Sie optional [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) mit SQL_ROW_ARRAY_SIZE so ändern Sie die Anzahl der Zeilen (R) im Rowset.  
  
2.  Rufen Sie [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) oder [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) um ein Rowset abzurufen.  
  
3.  Bei der Verwendung von gebundenen Spalten verwenden Sie die Datenwerte und Datenlängen, die nun in den Puffern mit gebundenen Spalten für das Rowset verfügbar sind.  
  
     Bei der Verwendung von ungebundenen Spalten rufen Sie für jede Zeile [SQLSetPos](http://go.microsoft.com/fwlink/?LinkId=58407) mit SQL_POSITION auf, um die Cursorposition festzulegen. Gehen Sie anschließend bei jeder ungebundenen Spalte wie folgt vor:  
  
    -   Rufen Sie [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) einmal oder mehrmals zum Abrufen der Daten für ungebundene Spalten nach der letzten Spalte des Rowsets gebundenen. Aufrufe von [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) sollte in der Reihenfolge zunehmender spaltenzahlfolge sein.  
  
    -   Rufen Sie [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) mehrere Male auf, um Daten aus einer text- oder image-Spalte abzurufen.  
  
4.  Richten Sie alle Data-at-Execution-text- oder Data-at-Execution-image-Spalten ein.  
  
5.  Rufen Sie [SQLSetPos](http://go.microsoft.com/fwlink/?LinkId=58407) oder [SQLBulkOperations](http://go.microsoft.com/fwlink/?LinkId=58398) auf, um die Cursorposition festzulegen und Zeilen im Rowset zu aktualisieren, zu löschen oder hinzuzufügen.  
  
     Data-at-Execution-text- oder Data-at-Execution-image-Spalten, die zum Aktualisieren oder Hinzufügen verwendet werden, müssen verarbeitet werden.  
  
6.  Führen Sie wahlweise eine positionierte Update- oder DELETE-Anweisung, dabei den Cursornamen angeben (verfügbar über [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)) und ein anderes Anweisungshandle für dieselbe Verbindung verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Cursorn Gewusst-wie-Themen &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)  
  
  
