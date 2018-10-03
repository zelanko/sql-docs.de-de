---
title: Long-Daten, SQLSetPos und SQLBulkOperations | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- SQLSetPos function [ODBC], long data and SQLBulkOperations
- data updates [ODBC], long data
- updating data [ODBC], long data
- SQLBulkOperations function [ODBC], long data
ms.assetid: e2fdf842-5e4c-46ca-bb21-4625c3324f28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b1d1a55d3b417ff7a0a673bda8d289a72d7c1cb1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658428"
---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>Long-Daten, SQLSetPos und SQLBulkOperations
Wie bei den Parametern in SQL-Anweisungen der Fall ist, long-Daten gesendet werden können, wenn aktualisieren, die mit Zeilen **SQLBulkOperations** oder **SQLSetPos** oder beim Einfügen von Zeilen mit **SQLBulkOperations**. Die Daten werden gesendet, in Teilen durch mehrere Aufrufe **SQLPutData**. Spalten, die für die Daten zum Zeitpunkt der Ausführung gesendet werden, werden als bezeichnet *Data-at-Execution-Spalten*.  
  
> [!NOTE]  
>  Eine Anwendung tatsächlich kann zu senden alle Arten von Daten zum Zeitpunkt der Ausführung mit **SQLPutData**, obwohl nur Zeichen- und Binärdaten in Teilen gesendet werden können. Wenn die Daten klein genug, um in einen einzelnen Puffer zu passen, gibt es ist jedoch im Allgemeinen kein Grund für die Verwendung **SQLPutData**. Es ist einfacher, den Puffer zu binden, und lassen den Treiber, die Abrufen der Daten aus dem Puffer.  
  
 Weil Sie long-Daten-Spalten in der Regel nicht gebunden sind, muss die Anwendung die Spalte vor dem Aufruf binden **SQLBulkOperations** oder **SQLSetPos** und heben Sie die Bindung nach dem Aufruf **SQLBulkOperations**  oder **SQLSetPos**. Die Spalte gebunden werden muss, da **SQLBulkOperations** oder **SQLSetPos** kann nur bei gebundenen Spalten und muss nicht aufgehoben werden, damit **SQLGetData** kann zum Abrufen von Daten verwendet werden in der Spalte.  
  
 Zum Senden von Daten zum Zeitpunkt der Ausführung führt die Anwendung Folgendes aus:  
  
1.  Einen 32-Bit-Wert platziert im Rowset Puffer statt eines Datenwerts. Dieser Wert wird an die Anwendung später zurückgegeben werden, damit die Anwendung, die keinen sinnvollen Wert ein, z. B. die Anzahl der Spalte oder das Handle für eine Datei mit Daten festgelegt werden soll.  
  
2.  Legt den Wert in den Längen-/Indikatorpuffers auf das Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*) Makro. Dieser Wert gibt an, an den Treiber, die die Daten für den Parameter mit gesendet werden **SQLPutData**. Die *Länge* Wert wird verwendet, beim Senden von long-Daten an eine Datenquelle, die muss wissen, wie viele Bytes an Daten vom Typ long gesendet werden, damit es die Speicherplatz vorab zuweisen kann. Um festzustellen, ob die Datenquelle diesen Wert, ruft die Anwendung muss **SQLGetInfo** mit der Option SQL_NEED_LONG_DATA_LEN. Alle Treiber müssen dieses Makro unterstützen. Wenn die Bytelänge in die Datenquelle nicht erforderlich ist, können Sie durch der Treiber ignorieren.  
  
3.  Aufrufe **SQLBulkOperations** oder **SQLSetPos**. Der Treiber ermittelt, dass ein Längen-/Indikatorpuffers auf das Ergebnis der SQL_LEN_DATA_AT_EXEC enthält (*Länge*)-Makro aus und gibt SQL_NEED_DATA zurück, als der Rückgabewert der Funktion zurück.  
  
4.  Aufrufe **SQLParamData** Rückgabewert als Reaktion auf die SQL_NEED_DATA zurück. Wenn Sie long-Daten gesendet werden, müssen **SQLParamData** wird SQL_NEED_DATA zurückgegeben. In den Puffer, der auf die *ValuePtrPtr* -Argument, gibt der Treiber den eindeutigen Wert, der die Anwendung im Puffer Rowset eingefügt. Wenn mehr als ein Data-at-Execution-Spalte vorhanden ist, verwendet die Anwendung diesen Wert, um zu bestimmen, welche Spalte zum Senden von Daten für; der Treiber ist nicht erforderlich, Anfordern von Daten für Data-at-Execution-Spalten in einer bestimmten Reihenfolge.  
  
5.  Aufrufe **SQLPutData** zum Senden der Spaltendaten an den Treiber. Wenn die Spaltendaten wie häufig der Fall mit langen Daten ist in einem einzelnen Puffer nicht passt, wird die Anwendung ruft **SQLPutData** wiederholt, um die Daten in Teile senden es obliegt dem Treiber und der Datenquelle, die Daten wieder zusammenzusetzen. Wenn die Anwendung Daten mit Null endende Zeichenfolge erfolgreich ist, muss die Treiber oder die Datenquelle die Null-Terminierungszeichen als Teil des Prozesses für die Reassemblierung entfernen.  
  
6.  Aufrufe **SQLParamData** erneut aus, um anzugeben, dass sie alle Daten für die Spalte gesendet hat. Wenn alle Data-at-Execution-Spalten, die für die Daten nicht gesendet wurden vorhanden sind, gibt der Treiber SQL_NEED_DATA sowie den eindeutigen Wert für die nächste Data-at-Execution-Spalte; Gibt zurück, die Anwendung mit Schritt 5 fort. Wenn die Daten für alle Data-at-Execution-Spalten gesendet wurde, werden die Daten für die Zeile an die Datenquelle gesendet. **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO und kann SQLSTATE zurückgeben **SQLBulkOperations** oder **SQLSetPos** zurückgeben können.  
  
 Nach dem **SQLBulkOperations** oder **SQLSetPos** wird SQL_NEED_DATA zurückgegeben. und bevor die Daten vollständig für die letzte Data-at-Execution-Spalte gesendet wurden, wird die Anweisung in einem Zustand der Daten erforderlich ist. In diesem Fall kann die Anwendung nur aufrufen **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**, oder **SQLGetDiagRec**; alle anderen Funktionen zurückgeben SQLSTATE HY010 (Sequenzfehler funktionieren). Aufrufen von **SQLCancel** bricht die Ausführung der Anweisung ab und gibt sie an den ursprünglichen Zustand zurück. Weitere Informationen finden Sie unter [Anhang B: ODBC-Übergang-Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
