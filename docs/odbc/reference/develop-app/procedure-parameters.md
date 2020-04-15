---
title: Prozedurparameter | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- procedure parameters [ODBC]
ms.assetid: 54fd857e-d2cb-467d-bb72-121e67a8e88d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 35d43ca7cf6e603d7dabca9eacf1e026daa753b7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306956"
---
# <a name="procedure-parameters"></a>Prozedurparameter
Parameter in Prozeduraufrufen können Eingabe-, Ein-/Ausgabe- oder Ausgabeparameter sein. Dies unterscheidet sich von Parametern in allen anderen SQL-Anweisungen, die immer Eingabeparameter sind.  
  
 Eingabeparameter werden verwendet, um Werte an die Prozedur zu senden. Angenommen, die Tabelle Parts enthält die Spalten PartID, Beschreibung und Preis. Die InsertPart-Prozedur verfügt möglicherweise über einen Eingabeparameter für jede Spalte in der Tabelle. Beispiel:  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 Ein Treiber sollte den Inhalt eines Eingabepuffers erst ändern, **wenn SQLExecDirect** oder **SQLExecute** SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_NO_DATA zurückgibt. Der Inhalt des Eingabepuffers sollte nicht geändert werden, während **SQLExecDirect** oder **SQLExecute** SQL_NEED_DATA oder SQL_STILL_EXECUTING zurückgibt.  
  
 Eingabe-/Ausgabeparameter werden sowohl zum Senden von Werten an Prozeduren als auch zum Abrufen von Werten aus Prozeduren verwendet. Die Verwendung desselben Parameters wie ein Eingabe- und ein Ausgabeparameter ist in der Regel verwirrend und sollte vermieden werden. Angenommen, eine Prozedur akzeptiert eine Auftrags-ID und gibt die ID des Debitors zurück. Dies kann mit einem einzigen Eingabe-/Ausgabeparameter definiert werden:  
  
```  
{call GetCustID(?)}  
```  
  
 Es könnte besser sein, zwei Parameter zu verwenden: einen Eingabeparameter für die Auftrags-ID und einen Ausgabe- oder Eingabe-/Ausgabeparameter für die Kunden-ID:  
  
```  
{call GetCustID(?, ?)}  
```  
  
 Ausgabeparameter werden verwendet, um den Prozedurrückgabewert abzurufen und Werte aus Prozedurargumenten abzurufen. Prozeduren, die Werte zurückgeben, werden manchmal als *Funktionen*bezeichnet. Angenommen, die soeben erwähnte **GetCustID-Prozedur** gibt einen Wert zurück, der angibt, ob die Bestellung gefunden werden konnte. Im folgenden Aufruf ist der erste Parameter ein Ausgabeparameter, der zum Abrufen des Prozedurrückgabewerts verwendet wird, der zweite Parameter ist ein Eingabeparameter, der zum Angeben der Auftrags-ID verwendet wird, und der dritte Parameter ist ein Ausgabeparameter, der zum Abrufen der Kunden-ID verwendet wird:  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 Treiber behandeln Werte für Eingabe- und Eingabe-/Ausgabeparameter in Prozeduren, die sich nicht von Eingabeparametern in anderen SQL-Anweisungen ändern. Wenn die Anweisung ausgeführt wird, rufen sie die Werte der an diese Parameter gebundenen Variablen ab und senden sie an die Datenquelle.  
  
 Nachdem die Anweisung ausgeführt wurde, speichern Treiber die zurückgegebenen Werte der Eingabe-/Ausgabe- und Ausgabeparameter in den an diese Parameter gebundenen Variablen. Diese zurückgegebenen Werte werden erst dann festgelegt, nachdem alle von der Prozedur zurückgegebenen Ergebnisse abgerufen wurden und **SQLMoreResults** SQL_NO_DATA zurückgegeben wurde. Wenn die Ausführung der Anweisung zu einem Fehler führt, ist der Inhalt des Eingabe-/Ausgabeparameterpuffers oder ausgabeparameterpuffers nicht definiert.  
  
 Eine Anwendung ruft **SQLProcedure** auf, um zu bestimmen, ob eine Prozedur einen Rückgabewert hat. Es ruft **SQLProcedureColumns** auf, um den Typ (Rückgabewert, Eingabe, Eingabe/Ausgabe oder Ausgabe) jedes Prozedurparameters zu bestimmen.
