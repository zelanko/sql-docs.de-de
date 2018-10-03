---
title: Cursorrowsetgröße | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bff145e7e3c6e429ca0877c81c5188b02e428809
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48143040"
---
# <a name="cursor-rowset-size"></a>Cursorrowsetgröße
  ODBC-Cursor sind nicht darauf beschränkt, nur jeweils eine Zeile abzurufen. Sie können mehrere Zeilen in jedem Aufruf von abrufen **SQLFetch** oder [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md). Bei einer Client-/Serverdatenbank, wie Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ist es effizienter, mehrere Zeilen gleichzeitig abzurufen. Die Anzahl der Zeilen, die bei einem Abrufvorgang zurückgegebenen ist Rowsetgröße bezeichnet und wird angegeben, indem Sie mit SQL_ATTR_ROW_ARRAY_SIZE von [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 Cursor mit einer Rowsetgröße größer als 1 werden als Blockcursor bezeichnet.  
  
 Es gibt zwei Optionen zum Binden von Resultsetspalten für Blockcursor:  
  
-   Spaltenweises Binden  
  
     Jede Spalte wird an ein Array von Variablen gebunden. Jedes Array verfügt über die gleiche Anzahl Elemente wie die Rowsetgröße.  
  
-   Zeilenweises binden  
  
     Ein Array wird anhand von Strukturen aufgebaut, die die Daten und Indikatoren für alle Spalten in einer Zeile enthalten. Das Array verfügt über die gleiche Anzahl Strukturen wie die Rowsetgröße.  
  
 Wenn entweder das spaltenweise oder zeilenweise Binden verwendet wird, hat jeder Aufruf zu **SQLFetch** oder **SQLFetchScroll** füllt die gebundene Arrays mit Daten aus dem Rowset abgerufen.  
  
 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) kann auch verwendet werden, um Spaltendaten von einem Blockcursor abzurufen. Da **SQLGetData** funktioniert eine Zeile zu einem Zeitpunkt **SQLSetPos** aufgerufen werden, um eine bestimmte Zeile im Rowset als aktuelle Zeile vor dem Aufruf festgelegt **SQLGetData**.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bietet eine Optimierung anhand von Rowsets ein gesamtes Resultset schnell abrufen. Um diese Optimierung zu verwenden, legen Sie die Cursorattribute auf ihre Standardwerte (Vorwärtscursor, schreibgeschützt, Rowsetgröße = 1) zum Zeitpunkt **SQLExecDirect** oder **SQLExecute** aufgerufen wird. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber richtet ein Standardresultset. Beim Übertragen von Ergebnissen auf den Client ohne Bildlauf ist dies effizienter als Servercursor. Nachdem die Anweisung ausgeführt wurde, erhöhen Sie die Rowsetgröße und verwenden Sie entweder das spaltenweise oder zeilenweise Binden. Auf diese Weise können [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwenden um Ergebniszeilen effizient an den Client senden ein Standardresultset während der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber wird kontinuierlich Zeilen aus den Netzwerkpuffern des Clients abruft.  
  
## <a name="see-also"></a>Siehe auch  
 [Cursoreigenschaften](cursor-properties.md)  
  
  
