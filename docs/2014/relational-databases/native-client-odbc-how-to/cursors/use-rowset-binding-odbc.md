---
title: Verwenden der Rowsetbindung (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 71a00f38d1424a05d5549e3b3a4c4fa816f26844
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412329"
---
# <a name="use-rowset-binding-odbc"></a>Verwenden der Rowsetbindung (ODBC)
    
### <a name="to-use-column-wise-binding"></a>So verwenden Sie spaltenbezogene Bindungen  
  
1.  Gehen Sie für jede gebundene Spalte wie folgt vor:  
  
    -   Weisen Sie ein Array von R (oder mehr) Spaltenpuffern zum Speichern von Datenwerten zu, wobei R die Anzahl der Zeilen im Rowset ist.  
  
    -   Weisen Sie optional ein Array von R (oder mehr) Spaltenpuffern zum Speichern von Datenlängen zu.  
  
    -   Rufen Sie [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) die Datenwert und die datenlängenarrays an die Spalte des Rowsets zu binden.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , die folgenden Attribute festzulegen:  
  
    -   Stellen Sie SQL_ATTR_ROW_ARRAY_SIZE auf die Anzahl der Zeilen im Rowset ein (R).  
  
    -   Stellen Sie SQL_ATTR_ROW_BIND_TYPE auf SQL_BIND_BY_COLUMN ein.  
  
    -   Legen Sie fest, dass das SQL_ATTR_ROWS FETCHED_PTR-Attribut auf eine SQLUINTEGER-Variable verweist, die die Anzahl der abgerufenen Zeilen enthält.  
  
    -   Lassen Sie SQL_ATTR_ROW_STATUS_PTR auf ein Array[R] von SQLUSSMALLINT-Variablen verweisen, die die Zeilenstatusindikatoren enthalten.  
  
3.  Ausführen der Anweisung.  
  
4.  Jeder Aufruf von [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) oder [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) ruft R-Zeilen ab und überträgt die Daten in die gebundenen Spalten.  
  
### <a name="to-use-row-wise-binding"></a>So verwenden Sie zeilenbezogene Bindungen  
  
1.  Weisen Sie ein Array [R] mit Strukturen zu, wobei R der Anzahl der Zeilen im Rowset entspricht. Die Struktur verfügt über ein Element für jede Spalte, und jedes Element besteht aus zwei Teilen:  
  
    -   Der erste Teil ist eine Variable des entsprechenden Datentyps zum Speichern der Spaltendaten.  
  
    -   Der zweite Teil ist eine SQLINTEGER-Variable zum Speichern des Spaltenstatusindikators.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , die folgenden Attribute festzulegen:  
  
    -   Stellen Sie SQL_ATTR_ROW_ARRAY_SIZE auf die Anzahl der Zeilen im Rowset ein (R).  
  
    -   Legen Sie SQL_ATTR_ROW_BIND_TYPE auf die Größe der in Schritt 1 zugeordneten Struktur fest.  
  
    -   Legen Sie fest, dass das SQL_ATTR_ROWS_FETCHED_PTR-Attribut auf eine SQLUINTEGER-Variable verweist, die die Anzahl der abgerufenen Zeilen enthält.  
  
    -   Lassen Sie SQL_ATTR_PARAMS_STATUS_PTR auf ein Array[R] von SQLUSSMALLINT-Variablen verweisen, die die Zeilenstatusindikatoren enthalten.  
  
3.  Rufen Sie für jede Spalte im Resultset [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) , zeigen Sie den Datenwert- und den datenlängenzeigern der Spalte auf die Variablen im ersten Element des Arrays mit Strukturen, die in Schritt 1 zugewiesen wurden.  
  
4.  Ausführen der Anweisung.  
  
5.  Jeder Aufruf von [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) oder [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) ruft R-Zeilen ab und überträgt die Daten in die gebundenen Spalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Cursorn Gewusst-wie-Themen &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)   
 [Implementieren von Cursorn](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [Verwenden von Cursorn &#40;ODBC&#41;](use-cursors-odbc.md)  
  
  
