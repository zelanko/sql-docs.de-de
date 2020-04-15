---
title: Lange Daten und SQLSetPos und SQLBulkOperations | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4bc6c5d2da2f796a7c312971635fc36bc2fae8af
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287864"
---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>Long-Daten, SQLSetPos und SQLBulkOperations
Wie bei Parametern in SQL-Anweisungen können lange Daten gesendet werden, wenn Zeilen mit **SQLBulkOperations** oder **SQLSetPos** aktualisiert werden oder Zeilen mit **SQLBulkOperations**eingefügt werden. Die Daten werden in Teilen mit mehreren Aufrufen von **SQLPutData**gesendet. Spalten, für die Daten zur Ausführungszeit gesendet werden, werden als *Data-at-Execution-Spalten*bezeichnet.  
  
> [!NOTE]  
>  Eine Anwendung kann tatsächlich jede Art von Daten zur Ausführungszeit mit **SQLPutData**senden, obwohl nur Zeichen- und Binärdaten in Teilen gesendet werden können. Wenn die Daten jedoch klein genug sind, um in einen einzelnen Puffer zu passen, gibt es im Allgemeinen keinen Grund, **SQLPutData**zu verwenden. Es ist viel einfacher, den Puffer zu binden und den Treiber die Daten aus dem Puffer abrufen zu lassen.  
  
 Da lange Datenspalten in der Regel nicht gebunden sind, muss die Anwendung die Spalte binden, bevor sie **SQLBulkOperations** oder **SQLSetPos** aufruft, und die Bindung nach dem Aufruf von **SQLBulkOperations** oder **SQLSetPos**aufkleben. Die Spalte muss gebunden werden, da **SQLBulkOperations** oder **SQLSetPos** nur für gebundene Spalten arbeitet und ungebunden sein muss, damit **SQLGetData** zum Abrufen von Daten aus der Spalte verwendet werden kann.  
  
 Um Daten zur Ausführungszeit zu senden, führt die Anwendung die folgenden Schritte aus:  
  
1.  Platziert einen 32-Bit-Wert im Rowset-Puffer anstelle eines Datenwerts. Dieser Wert wird später an die Anwendung zurückgegeben, daher sollte die Anwendung ihn auf einen aussagekräftigen Wert festlegen, z. B. die Nummer der Spalte oder das Handle einer Datei, die Daten enthält.  
  
2.  Legt den Wert im Längen-/Indikatorpuffer auf das Ergebnis des Makros*SQL_LEN_DATA_AT_EXEC(Länge*) fest. Dieser Wert gibt dem Treiber an, dass die Daten für den Parameter mit **SQLPutData**gesendet werden. Der *Längenwert* wird beim Senden langer Daten an eine Datenquelle verwendet, die wissen muss, wie viele Bytes langer Daten gesendet werden, damit Speicherplatz vorab zugewiesen werden kann. Um zu bestimmen, ob eine Datenquelle diesen Wert erfordert, ruft die Anwendung **SQLGetInfo** mit der Option SQL_NEED_LONG_DATA_LEN auf. Alle Treiber müssen dieses Makro unterstützen. Wenn die Datenquelle die Bytelänge nicht benötigt, kann der Treiber sie ignorieren.  
  
3.  Ruft **SQLBulkOperations** oder **SQLSetPos**auf. Der Treiber stellt fest, dass ein Längen-/Indikatorpuffer das Ergebnis des*SQL_LEN_DATA_AT_EXEC-Makros*enthält und gibt SQL_NEED_DATA als Rückgabewert der Funktion zurück.  
  
4.  Ruft **SQLParamData** als Antwort auf den SQL_NEED_DATA Rückgabewert auf. Wenn lange Daten gesendet werden müssen, gibt **SQLParamData** SQL_NEED_DATA zurück. Im Puffer, auf den das *ValuePtrPtr-Argument* zeigt, gibt der Treiber den eindeutigen Wert zurück, den die Anwendung im Rowset-Puffer platziert hat. Wenn mehr als eine Data-at-Execution-Spalte vorhanden ist, verwendet die Anwendung diesen Wert, um zu bestimmen, für welche Spalte Daten gesendet werden sollen. Der Treiber ist nicht verpflichtet, Daten für Data-at-Execution-Spalten in einer bestimmten Reihenfolge anzufordern.  
  
5.  Ruft **SQLPutData** auf, um die Spaltendaten an den Treiber zu senden. Wenn die Spaltendaten nicht in einen einzelnen Puffer passen, wie dies bei langen Daten häufig der Fall ist, ruft die Anwendung **SQLPutData** wiederholt auf, um die Daten in Teilen zu senden. Es liegt an dem Treiber und der Datenquelle, die Daten wieder zusammenzusetzen. Wenn die Anwendung null-beendete Zeichenfolgendaten übergibt, muss der Treiber oder die Datenquelle das NULL-Beendigungszeichen als Teil des Reassembly-Prozesses entfernen.  
  
6.  Ruft **SQLParamData** erneut auf, um anzugeben, dass alle Daten für die Spalte gesendet wurden. Wenn Daten bei der Ausführung vorhanden sind, für die keine Daten gesendet wurden, gibt der Treiber SQL_NEED_DATA und den eindeutigen Wert für die nächste Spalte "Data-at-Execution" zurück. die Anwendung kehrt zu Schritt 5 zurück. Wenn Daten für alle Data-at-Execution-Spalten gesendet wurden, werden die Daten für die Zeile an die Datenquelle gesendet. **SQLParamData** gibt dann SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück und kann alle SQLSTATE zurückgeben, die **SQLBulkOperations** oder **SQLSetPos** zurückgeben können.  
  
 Nachdem **SQLBulkOperations** oder **SQLSetPos** SQL_NEED_DATA zurückgegeben und bevor Daten vollständig für die letzte Data-at-Execution-Spalte gesendet wurden, befindet sich die Anweisung im Status "Need Data". In diesem Zustand kann die Anwendung nur **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**oder **SQLGetDiagRec**aufrufen . Alle anderen Funktionen geben SQLSTATE HY010 (Funktionssequenzfehler) zurück. Durch Aufrufen von **SQLCancel** wird die Ausführung der Anweisung abgebrochen und in den vorherigen Zustand zurückgesendet. Weitere Informationen finden Sie in [Anhang B: ODBC-Zustandsübergangstabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
