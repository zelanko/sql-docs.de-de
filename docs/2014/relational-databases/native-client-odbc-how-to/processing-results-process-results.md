---
title: Verarbeiten von Ergebnissen (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fa20ed943be8195eb7719265d3bd2ef0aa26a38c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047822"
---
# <a name="process-results-odbc"></a>Verarbeiten von Ergebnissen (ODBC)
    
### <a name="to-process-results"></a>So verarbeiten Sie Ergebnisse  
  
1.  Rufen Sie Resultsetinformationen ab.  
  
2.  Wenn gebundene Spalten verwendet werden, rufen Sie für jede Spalte, für die eine Bindung erstellt werden soll, [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) auf, um einen Programmpuffer an die Spalte zu binden.  
  
3.  Für jede Zeile im Resultset wird Folgendes ausgeführt:  
  
    -   Rufen Sie [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) auf, um die nächste Zeile abzurufen.  
  
    -   Bei der Verwendung von gebundenen Spalten verwenden Sie die Daten, die nun in den Puffern mit gebundenen Spalten verfügbar sind.  
  
    -   Wenn ungebundene Spalten verwendet werden, rufen Sie [SQLGetData](../native-client-odbc-api/sqlgetdata.md) ein oder mehrere Male auf, um die Daten für ungebundene Spalten nach der letzten gebundenen Spalte abzurufen. Aufrufe von `SQLGetData` in aufsteigender Reihenfolge der Spaltennummer werden sollte.  
  
    -   Rufen Sie `SQLGetData` mehrere Male auf, um Daten aus einer text- oder image-Spalte abzurufen.  
  
4.  Wenn [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) das Ende des Resultsets durch Rückgabe von SQL_NO_DATA signalisiert, rufen Sie [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) auf, um zu bestimmen, ob ein weiteres Resultset verfügbar ist.  
  
    -   Wenn SQL_SUCCESS zurückgegeben wird, ist ein anderes Resultset verfügbar.  
  
    -   Wenn SQL_NO_DATA zurückgegeben wird, sind keine weiteren Resultsets verfügbar.  
  
    -   Wenn SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgegeben wird, rufen Sie [SQLGetDiagRec](http://go.microsoft.com/fwlink/?LinkId=58402) auf, um festzustellen, ob die Ausgabe von einer PRINT- oder RAISERROR-Anweisung verfügbar ist.  
  
         Wenn für Ausgabeparameter oder für den Rückgabewert einer gespeicherten Prozedur gebundene Anweisungsparameter verwendet werden, verwenden Sie die jetzt in den Puffern für gebundene Parameter verfügbaren Daten. Wenn gebundene Parameter verwendet werden, hat jeder Aufruf von [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) oder [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) die SQL-Anweisung *S*-mal ausgeführt, wobei *S* die Anzahl der Elemente im Array von gebundenen Parametern ist. Das bedeutet, dass *S* Ergebnismengen verarbeitet werden müssen, wobei jede Ergebnismenge sämtliche Resultsets, Ausgabeparameter und Rückgabecodes enthält, die in der Regel von einer einzelnen Ausführung der SQL-Anweisung zurückgegeben werden.  
  
    > [!NOTE]  
    >  Wenn ein Resultset COMPUTE-Zeilen (Berechnungszeilen) enthält, wird jede COMPUTE-Zeile als eigenes Resultset verfügbar gemacht. Diese COMPUTE-Resultsets werden in die normalen Zeilen eingefügt und teilen normale Zeilen in mehrere Resultsets.  
  
5.  Sie können optional [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) mit SQL_UNBIND aufrufen, um Puffer mit gebundenen Spalten freizugeben.  
  
6.  Wenn ein weiteres Resultset verfügbar ist, fahren Sie mit Schritt 1 fort.  
  
> [!NOTE]  
>  Um das Verarbeiten eines Resultsets abzubrechen, bevor [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) SQL_NO_DATA zurückgibt, rufen Sie [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md) auf.  
  
## <a name="see-also"></a>Siehe auch  
 [Ergebnisse Vorgehensweisen zum Verarbeiten &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  