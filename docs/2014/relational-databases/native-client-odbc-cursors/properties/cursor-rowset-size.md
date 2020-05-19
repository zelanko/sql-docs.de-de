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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9facf44afde40c69523c67997f294c4a5fa620c8
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705575"
---
# <a name="cursor-rowset-size"></a>Cursorrowsetgröße
  ODBC-Cursor sind nicht darauf beschränkt, nur jeweils eine Zeile abzurufen. Sie können mehrere Zeilen in jedem-Befehl von **SQLFetch** oder [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)abrufen. Bei einer Client-/Serverdatenbank, wie Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ist es effizienter, mehrere Zeilen gleichzeitig abzurufen. Die Anzahl der bei einem Abruf Vorgang zurückgegebenen Zeilen wird als Rowsetgröße bezeichnet und mithilfe der SQL_ATTR_ROW_ARRAY_SIZE von [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)angegeben.  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 Cursor mit einer Rowsetgröße größer als 1 werden als Blockcursor bezeichnet.  
  
 Es gibt zwei Optionen zum Binden von Resultsetspalten für Blockcursor:  
  
-   Spaltenweises Binden  
  
     Jede Spalte wird an ein Array von Variablen gebunden. Jedes Array verfügt über die gleiche Anzahl Elemente wie die Rowsetgröße.  
  
-   Zeilen weises binden  
  
     Ein Array wird anhand von Strukturen aufgebaut, die die Daten und Indikatoren für alle Spalten in einer Zeile enthalten. Das Array verfügt über die gleiche Anzahl Strukturen wie die Rowsetgröße.  
  
 Wenn entweder eine spaltenweise oder zeilenweise Bindung verwendet wird, füllt jeder-Befehl von **SQLFetch** oder **SQLFetchScroll** die gebundenen Arrays mit Daten aus dem abgerufenen Rowset.  
  
 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) kann auch zum Abrufen von Spaltendaten aus einem Block Cursor verwendet werden. Da **SQLGetData** jeweils eine Zeile verwendet, müssen **SQLSetPos** aufgerufen werden, um eine bestimmte Zeile im Rowset als aktuelle Zeile festzulegen, bevor **SQLGetData**aufgerufen wird.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber bietet eine Optimierung, bei der mithilfe von Rowsets ein gesamtes Resultset schnell abgerufen wird. Um diese Optimierung zu verwenden, legen Sie die Cursor Attribute auf ihre Standardwerte fest (vorwärts, schreibgeschützt, Rowsetgröße = 1), wenn **SQLExecDirect** oder **SQLExecute** aufgerufen wird. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber richtet ein Standardresultset ein. Beim Übertragen von Ergebnissen auf den Client ohne Bildlauf ist dies effizienter als Servercursor. Nachdem die Anweisung ausgeführt wurde, erhöhen Sie die Rowsetgröße und verwenden Sie entweder das spaltenweise oder zeilenweise Binden. Dadurch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann ein Standardresultset verwendet werden, um Ergebniszeilen effizient an den Client zu senden, während der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber kontinuierlich Zeilen aus den Netzwerkpuffern auf dem Client abruft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cursoreigenschaften](cursor-properties.md)  
  
  
