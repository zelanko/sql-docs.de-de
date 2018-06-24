---
title: Cursorrowsetgröße | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bec0b6eb7f85c5dc11c1e590d809ba0a32079fe2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047585"
---
# <a name="cursor-rowset-size"></a>Cursorrowsetgröße
  ODBC-Cursor sind nicht darauf beschränkt, nur jeweils eine Zeile abzurufen. Sie können mehrere Zeilen in jedem Aufruf abrufen **SQLFetch** oder [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md). Bei einer Client-/Serverdatenbank, wie Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ist es effizienter, mehrere Zeilen gleichzeitig abzurufen. Die Anzahl der Zeilen, die bei einem Abrufvorgang zurückgegebenen Rowsetgröße bezeichnet wird und mit SQL_ATTR_ROW_ARRAY_SIZE von angegeben [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 Cursor mit einer Rowsetgröße größer als 1 werden als Blockcursor bezeichnet.  
  
 Es gibt zwei Optionen zum Binden von Resultsetspalten für Blockcursor:  
  
-   Spaltenweises Binden  
  
     Jede Spalte wird an ein Array von Variablen gebunden. Jedes Array verfügt über die gleiche Anzahl Elemente wie die Rowsetgröße.  
  
-   Zeilenbezogene Bindungen  
  
     Ein Array wird anhand von Strukturen aufgebaut, die die Daten und Indikatoren für alle Spalten in einer Zeile enthalten. Das Array verfügt über die gleiche Anzahl Strukturen wie die Rowsetgröße.  
  
 Wenn entweder das spaltenweise oder zeilenweise Bindung verwendet wird, bei jedem Aufruf **SQLFetch** oder **SQLFetchScroll** füllt die gebundene Arrays mit Daten aus dem Rowset abgerufen.  
  
 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) kann auch verwendet werden, um Spaltendaten von einem Blockcursor abzurufen. Da **SQLGetData** funktioniert eine Zeile zu einem Zeitpunkt **SQLSetPos** aufgerufen werden, um eine bestimmte Zeile im Rowset als aktuelle Zeile vor dem Aufruf festgelegt **SQLGetData**.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bietet eine Optimierung Rowsets verwenden, um ein gesamtes Resultset schnell abzurufen. Um diese Optimierung verwenden zu können, legen Sie die Cursorattribute auf ihre Standardwerte (vorwärts, schreibgeschützt, Rowsetgröße = 1) zu dem Zeitpunkt **SQLExecDirect** oder **SQLExecute** aufgerufen wird. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber richtet ein Standardresultset. Beim Übertragen von Ergebnissen auf den Client ohne Bildlauf ist dies effizienter als Servercursor. Nachdem die Anweisung ausgeführt wurde, erhöhen Sie die Rowsetgröße und verwenden Sie entweder das spaltenweise oder zeilenweise Binden. Auf diese Weise können [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwenden, die ein Standardresultset Ergebniszeilen effizient an den Client senden während der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber ruft kontinuierlich Zeilen aus den Netzwerkpuffern des Clients.  
  
## <a name="see-also"></a>Siehe auch  
 [Cursoreigenschaften](cursor-properties.md)  
  
  