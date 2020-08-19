---
description: Long-Daten, SQLSetPos und SQLBulkOperations
title: Long Data und SQLSetPos und SQLBulkOperations | Microsoft-Dokumentation
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
ms.openlocfilehash: 12bc0299df58bf85272445773a8f33a872c39ef2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429272"
---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>Long-Daten, SQLSetPos und SQLBulkOperations
Wie bei Parametern in SQL-Anweisungen können lange Daten beim Aktualisieren von Zeilen mit **SQLBulkOperations** oder **SQLSetPos** oder beim Einfügen von Zeilen mit **SQLBulkOperations**gesendet werden. Die Daten werden in Teilen mit mehreren Aufrufen von **SQLPutData**gesendet. Spalten, für die Daten zur Ausführungszeit gesendet werden, werden als *Data-at-Execution-Spalten*bezeichnet.  
  
> [!NOTE]  
>  Eine Anwendung kann alle Datentypen zur Ausführungszeit mit **SQLPutData**senden, obwohl nur Zeichen-und Binärdaten in Teilen gesendet werden können. Wenn die Daten jedoch klein genug sind, um in einen einzelnen Puffer zu passen, gibt es in der Regel keinen Grund, **SQLPutData**zu verwenden. Es ist viel einfacher, den Puffer zu binden, sodass der Treiber die Daten aus dem Puffer abrufen kann.  
  
 Da lange Datenspalten in der Regel nicht gebunden werden, muss die Anwendung die Spalte vor dem Aufrufen von **SQLBulkOperations** oder **SQLSetPos** binden und die Bindung nach dem Aufrufen von **SQLBulkOperations** oder **SQLSetPos**aufheben. Die Spalte muss gebunden werden, da **SQLBulkOperations** oder **SQLSetPos** nur für gebundene Spalten funktioniert und die Bindung aufgehoben werden muss, damit **SQLGetData** zum Abrufen von Daten aus der Spalte verwendet werden kann.  
  
 Zum Senden von Daten zur Ausführungszeit führt die Anwendung die folgenden Schritte aus:  
  
1.  Platziert einen 32-Bit-Wert im rowsetpuffer anstelle eines Datenwerts. Dieser Wert wird später an die Anwendung zurückgegeben, sodass die Anwendung Sie auf einen sinnvollen Wert festlegen muss, z. b. die Nummer der Spalte oder das Handle einer Datei, die Daten enthält.  
  
2.  Legt den Wert im Längen-/Indikatorpuffer auf das Ergebnis des SQL_LEN_DATA_AT_EXEC (*length*)-Makros fest. Dieser Wert gibt dem Treiber an, dass die Daten für den Parameter mit **SQLPutData**gesendet werden. Der *Längen* Wert wird verwendet, wenn lange Daten an eine Datenquelle gesendet werden, die wissen müssen, wie viele Bytes von langen Daten gesendet werden, damit der Speicherplatz vorab zugeordnet werden kann. Um zu ermitteln, ob eine Datenquelle diesen Wert erfordert, ruft die Anwendung **SQLGetInfo** mit der SQL_NEED_LONG_DATA_LEN-Option auf. Dieses Makro muss von allen Treibern unterstützt werden. Wenn die Datenquelle die Byte Länge nicht benötigt, kann Sie vom Treiber ignoriert werden.  
  
3.  Ruft **SQLBulkOperations** oder **SQLSetPos**auf. Der Treiber ermittelt, dass ein Längen-/Indikatorpuffer das Ergebnis des SQL_LEN_DATA_AT_EXEC (*length*)-Makros enthält und SQL_NEED_DATA als Rückgabewert der Funktion zurückgibt.  
  
4.  Ruft **SQLParamData** als Reaktion auf den SQL_NEED_DATA Rückgabewert auf. Wenn Long-Daten gesendet werden müssen, gibt **SQLParamData** SQL_NEED_DATA zurück. Im Puffer, auf den das *ValuePtrPtr* -Argument zeigt, gibt der Treiber den eindeutigen Wert zurück, den die Anwendung in den rowsetpuffer eingefügt hat. Wenn mehr als eine Data-at-Execution-Spalte vorhanden ist, verwendet die Anwendung diesen Wert, um zu ermitteln, für welche Spalte Daten gesendet werden sollen. der Treiber muss keine Daten für Data-at-Execution-Spalten in einer bestimmten Reihenfolge anfordern.  
  
5.  Ruft **SQLPutData** auf, um die Spaltendaten an den Treiber zu senden. Wenn die Spaltendaten nicht in einen einzelnen Puffer passen, wie es häufig bei langen Daten der Fall ist, ruft die Anwendung **SQLPutData** wiederholt auf, um die Daten in Teilen zu senden. der Treiber und die Datenquelle müssen die Daten neu zuweisen. Wenn die Anwendung auf NULL endenden Zeichen folgen Daten übergibt, muss der Treiber oder die Datenquelle das NULL-Beendigungs Zeichen als Teil des neuzuordnungs Prozesses entfernen.  
  
6.  Ruft **SQLParamData** erneut auf, um anzugeben, dass alle Daten für die Spalte gesendet wurden. Wenn Data-at-Execution-Spalten vorhanden sind, für die keine Daten gesendet wurden, gibt der Treiber SQL_NEED_DATA und den eindeutigen Wert für die nächste Data-at-Execution-Spalte zurück. die Anwendung kehrt zu Schritt 5 zurück. Wenn Daten für alle Data-at-Execution-Spalten gesendet wurden, werden die Daten für die Zeile an die Datenquelle gesendet. **SQLParamData** gibt dann SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück und kann beliebige SQLSTATE-Objekte zurückgeben, die von **SQLBulkOperations** oder **SQLSetPos** zurückgegeben werden können.  
  
 Nachdem **SQLBulkOperations** oder **SQLSetPos** SQL_NEED_DATA zurückgegeben und die Daten vollständig für die letzte Data-at-Execution-Spalte gesendet wurden, befindet sich die-Anweisung in einem Daten Zustands Bedarf. In diesem Zustand kann die Anwendung nur **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**oder **SQLGetDiagRec**aufrufen. alle anderen Funktionen geben SQLSTATE HY010 (Funktions Sequenz Fehler) zurück. Durch den Aufruf von **SQLCancel** wird die Ausführung der-Anweisung abgebrochen und in den vorherigen Zustand zurückversetzt. Weitere Informationen finden Sie unter [Anhang B: ODBC-Status Übergangs Tabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
