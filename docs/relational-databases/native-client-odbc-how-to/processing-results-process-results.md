---
description: 'Verarbeiten von Ergebnissen: Prozessergebnisse'
title: Verarbeitungsergebnisse (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 12c2e1a04ce4ed79d90d7f8e10852e68e0e86352
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440022"
---
# <a name="processing-results---process-results"></a>Verarbeiten von Ergebnissen: Prozessergebnisse
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Bei der Verarbeitung von Ergebnissen in einer ODBC-Anwendung werden zunächst die Merkmale des Resultsets ermittelt und anschließend die Daten mithilfe von [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) oder [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)in Programmvariablen abgerufen.  
  
### <a name="to-process-results"></a>So verarbeiten Sie Ergebnisse  
  
1.  Rufen Sie Resultsetinformationen ab.  
  
2.  Wenn gebundene Spalten verwendet werden, rufen Sie für jede Spalte, für die eine Bindung erstellt werden soll, [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) auf, um einen Programmpuffer an die Spalte zu binden.  
  
3.  Für jede Zeile im Resultset wird Folgendes ausgeführt:  
  
    -   Rufen Sie [SQLFetch](../../odbc/reference/syntax/sqlfetch-function.md) auf, um die nächste Zeile abzurufen.  
  
    -   Bei der Verwendung von gebundenen Spalten verwenden Sie die Daten, die nun in den Puffern mit gebundenen Spalten verfügbar sind.  
  
    -   Wenn ungebundene Spalten verwendet werden, rufen Sie [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) ein oder mehrere Male auf, um die Daten für ungebundene Spalten nach der letzten gebundenen Spalte abzurufen. Aufrufe von **SQLGetData** müssen in aufsteigender Reihenfolge der Spaltennummer erfolgen.  
  
    -   Rufen Sie **SQLGetData** mehrere Male auf, um Daten aus einer text- oder image-Spalte abzurufen.  
  
4.  Wenn [SQLFetch](../../odbc/reference/syntax/sqlfetch-function.md) das Ende des Resultsets durch Rückgabe von SQL_NO_DATA signalisiert, rufen Sie [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) auf, um zu bestimmen, ob ein weiteres Resultset verfügbar ist.  
  
    -   Wenn SQL_SUCCESS zurückgegeben wird, ist ein anderes Resultset verfügbar.  
  
    -   Wenn SQL_NO_DATA zurückgegeben wird, sind keine weiteren Resultsets verfügbar.  
  
    -   Wenn SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgegeben wird, rufen Sie [SQLGetDiagRec](../../odbc/reference/syntax/sqlgetdiagrec-function.md) auf, um festzustellen, ob die Ausgabe von einer PRINT- oder RAISERROR-Anweisung verfügbar ist.  
  
         Wenn für Ausgabeparameter oder für den Rückgabewert einer gespeicherten Prozedur gebundene Anweisungsparameter verwendet werden, verwenden Sie die jetzt in den Puffern für gebundene Parameter verfügbaren Daten. Wenn gebundene Parameter verwendet werden, hat jeder Aufruf von [SQLExecute](../../odbc/reference/syntax/sqlexecute-function.md) oder [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) die SQL-Anweisung *S*-mal ausgeführt, wobei *S* die Anzahl der Elemente im Array von gebundenen Parametern ist. Dies bedeutet, dass *S* Sätze von Ergebnissen verarbeitet werden müssen, wobei jeder Resultset alle Resultsets, Ausgabeparameter und Rückgabecodes enthält, die normalerweise von einer einzelnen Ausführung der SQL-Anweisung zurückgegeben werden.  
  
    > [!NOTE]  
    >  Wenn ein Resultset COMPUTE-Zeilen (Berechnungszeilen) enthält, wird jede COMPUTE-Zeile als eigenes Resultset verfügbar gemacht. Diese COMPUTE-Resultsets werden in die normalen Zeilen eingefügt und teilen normale Zeilen in mehrere Resultsets.  
  
5.  Sie können optional [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) mit SQL_UNBIND aufrufen, um Puffer mit gebundenen Spalten freizugeben.  
  
6.  Wenn ein weiteres Resultset verfügbar ist, fahren Sie mit Schritt 1 fort.  

> [!NOTE]  
>  Um das Verarbeiten eines Resultsets abzubrechen, bevor [SQLFetch](../../odbc/reference/syntax/sqlfetch-function.md) SQL_NO_DATA zurückgibt, rufen Sie [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md) auf.  
  
## <a name="see-also"></a>Weitere Informationen  
[Abrufen von Resultsetinformationen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-retrieve-result-set-information.md)   
  
