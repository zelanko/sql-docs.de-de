---
title: Verarbeitungsergebnisse (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21474aed83aac1fe86e2242b1238affa11ae64a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63200316"
---
# <a name="process-results-odbc"></a>Verarbeiten von Ergebnissen (ODBC)
    
### <a name="to-process-results"></a>So verarbeiten Sie Ergebnisse  
  
1.  Rufen Sie Resultsetinformationen ab.  
  
2.  Wenn gebundene Spalten verwendet werden, rufen Sie für jede Spalte, für die eine Bindung erstellt werden soll, [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) auf, um einen Programmpuffer an die Spalte zu binden.  
  
3.  Für jede Zeile im Resultset wird Folgendes ausgeführt:  
  
    -   Rufen Sie [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) auf, um die nächste Zeile abzurufen.  
  
    -   Bei der Verwendung von gebundenen Spalten verwenden Sie die Daten, die nun in den Puffern mit gebundenen Spalten verfügbar sind.  
  
    -   Wenn ungebundene Spalten verwendet werden, rufen Sie [SQLGetData](../native-client-odbc-api/sqlgetdata.md) ein oder mehrere Male auf, um die Daten für ungebundene Spalten nach der letzten gebundenen Spalte abzurufen. Aufrufe von `SQLGetData` sollten in aufsteigender Reihenfolge der Spaltennummer erfolgen.  
  
    -   Rufen Sie `SQLGetData` mehrere Male auf, um Daten aus einer text- oder image-Spalte abzurufen.  
  
4.  Wenn [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) das Ende des Resultsets durch Rückgabe von SQL_NO_DATA signalisiert, rufen Sie [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) auf, um zu bestimmen, ob ein weiteres Resultset verfügbar ist.  
  
    -   Wenn SQL_SUCCESS zurückgegeben wird, ist ein anderes Resultset verfügbar.  
  
    -   Wenn SQL_NO_DATA zurückgegeben wird, sind keine weiteren Resultsets verfügbar.  
  
    -   Wenn SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgegeben wird, rufen Sie [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) auf, um festzustellen, ob die Ausgabe von einer PRINT- oder RAISERROR-Anweisung verfügbar ist.  
  
         Wenn für Ausgabeparameter oder für den Rückgabewert einer gespeicherten Prozedur gebundene Anweisungsparameter verwendet werden, verwenden Sie die jetzt in den Puffern für gebundene Parameter verfügbaren Daten. Wenn gebundene Parameter verwendet werden, hat jeder Aufruf von [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) oder [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) die SQL-Anweisung *S*-mal ausgeführt, wobei *S* die Anzahl der Elemente im Array von gebundenen Parametern ist. Dies bedeutet, dass *S* Sätze von Ergebnissen verarbeitet werden müssen, wobei jeder Resultset alle Resultsets, Ausgabeparameter und Rückgabecodes enthält, die normalerweise von einer einzelnen Ausführung der SQL-Anweisung zurückgegeben werden.  
  
    > [!NOTE]  
    >  Wenn ein Resultset COMPUTE-Zeilen (Berechnungszeilen) enthält, wird jede COMPUTE-Zeile als eigenes Resultset verfügbar gemacht. Diese COMPUTE-Resultsets werden in die normalen Zeilen eingefügt und teilen normale Zeilen in mehrere Resultsets.  
  
5.  Sie können optional [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) mit SQL_UNBIND aufrufen, um Puffer mit gebundenen Spalten freizugeben.  
  
6.  Wenn ein weiteres Resultset verfügbar ist, fahren Sie mit Schritt 1 fort.  
  
> [!NOTE]  
>  Um das Verarbeiten eines Resultsets abzubrechen, bevor [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) SQL_NO_DATA zurückgibt, rufen Sie [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md) auf.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Themen zur Vorgehensweise bei der Verarbeitung von Ergebnissen &#40;ODBC-&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
