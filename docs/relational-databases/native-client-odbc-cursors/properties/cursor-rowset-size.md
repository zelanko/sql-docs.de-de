---
title: Cursor Rowset Größe | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7f799722bfae35a714e740691e2cdc53e3155063
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302869"
---
# <a name="cursor-rowset-size"></a>Cursorrowsetgröße
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC-Cursor sind nicht darauf beschränkt, nur jeweils eine Zeile abzurufen. Sie können mehrere Zeilen in jedem Aufruf von **SQLFetch** oder [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)abrufen. Bei einer Client-/Serverdatenbank, wie Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ist es effizienter, mehrere Zeilen gleichzeitig abzurufen. Die Anzahl der Zeilen, die für einen Abruf zurückgegeben werden, wird als Rowsetgröße bezeichnet und mithilfe der SQL_ATTR_ROW_ARRAY_SIZE von [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)angegeben.  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 Cursor mit einer Rowsetgröße größer als 1 werden als Blockcursor bezeichnet.  
  
 Es gibt zwei Optionen zum Binden von Resultsetspalten für Blockcursor:  
  
-   Spaltenweises Binden  
  
     Jede Spalte wird an ein Array von Variablen gebunden. Jedes Array verfügt über die gleiche Anzahl Elemente wie die Rowsetgröße.  
  
-   Row-wise-Bindung  
  
     Ein Array wird anhand von Strukturen aufgebaut, die die Daten und Indikatoren für alle Spalten in einer Zeile enthalten. Das Array verfügt über die gleiche Anzahl Strukturen wie die Rowsetgröße.  
  
 Wenn entweder spalten- oder zeilenweise Bindung verwendet wird, füllt jeder Aufruf von **SQLFetch** oder **SQLFetchScroll** die gebundenen Arrays mit Daten aus dem abgerufenen Rowset.  
  
 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) kann auch zum Abrufen von Spaltendaten von einem Blockcursor verwendet werden. Da **SQLGetData** jeweils eine Zeile arbeitet, muss **SQLSetPos** aufgerufen werden, um eine bestimmte Zeile im Rowset als aktuelle Zeile festzulegen, bevor **SQLGetData**aufgerufen wird.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bietet eine Optimierung mithilfe von Rowsets, um schnell ein ganzes Resultset abzurufen. Um diese Optimierung zu verwenden, legen Sie die Cursorattribute auf ihre Standardwerte (vorwärts- und schreibgeschützt, Rowsetgröße = 1) zum Zeitpunkt des Aufrufs von **SQLExecDirect** oder **SQLExecute** fest. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber richtet ein Standardergebnissatz ein. Beim Übertragen von Ergebnissen auf den Client ohne Bildlauf ist dies effizienter als Servercursor. Nachdem die Anweisung ausgeführt wurde, erhöhen Sie die Rowsetgröße und verwenden Sie entweder das spaltenweise oder zeilenweise Binden. Dadurch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Sie ein Standardresultat verwenden, um Ergebniszeilen effizient an den Client zu senden, während der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber kontinuierlich Zeilen aus den Netzwerkpuffern auf dem Client abruft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cursoreigenschaften](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
