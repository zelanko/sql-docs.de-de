---
title: Prozedur Parameter | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f85512a1686df26cad739dc906e49cc5499f62e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912301"
---
# <a name="procedure-parameters"></a>Prozedurparameter
Parameter in Prozedur aufrufen können Eingabe-, Eingabe-/Ausgabe-oder Ausgabeparameter sein. Dies unterscheidet sich von den Parametern aller anderen SQL-Anweisungen, bei denen es sich immer um Eingabeparameter handelt.  
  
 Eingabeparameter werden verwendet, um Werte an die Prozedur zu senden. Angenommen, die parts-Tabelle enthält die Spalten partid, Description und Price. Die insertpart-Prozedur kann über einen Eingabeparameter für jede Spalte in der Tabelle verfügen. Beispiel:  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 Ein Treiber sollte den Inhalt eines Eingabe Puffers erst ändern, wenn **SQLExecDirect** oder **SQLExecute** SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_NO_DATA zurückgibt. Der Inhalt des Eingabe Puffers sollte nicht geändert werden, während **SQLExecDirect** oder **SQLExecute** SQL_NEED_DATA oder SQL_STILL_EXECUTING zurückgibt.  
  
 Eingabe-/Ausgabeparameter werden verwendet, um Werte an Prozeduren zu senden und Werte aus Verfahren abzurufen. Die Verwendung desselben Parameters, der sowohl ein Eingabe-als auch ein Output-Parameter ist, ist tendenziell verwirrend und sollte vermieden werden. Nehmen wir beispielsweise an, eine Prozedur akzeptiert eine Bestell-ID und gibt die ID des Kunden zurück. Dies kann mit einem einzelnen Eingabe-/Ausgabeparameter definiert werden:  
  
```  
{call GetCustID(?)}  
```  
  
 Es ist möglicherweise besser, zwei Parameter zu verwenden: einen Eingabeparameter für die Auftrags-ID und einen Output-oder Input/Output-Parameter für die Kunden-ID:  
  
```  
{call GetCustID(?, ?)}  
```  
  
 Ausgabeparameter werden zum Abrufen des Prozedur Rückgabewerts und zum Abrufen von Werten aus Prozedur Argumenten verwendet. Prozeduren, die Werte zurückgeben, werden mitunter als *Funktionen*bezeichnet. Angenommen, die **getcustid-** Prozedur, die soeben erwähnt wurde, gibt z. b. einen Wert zurück, der angibt, ob Sie die Bestellung finden konnte. Im folgenden-Befehl ist der erste Parameter ein Ausgabeparameter, der zum Abrufen des Prozedur Rückgabewerts verwendet wird. der zweite Parameter ist ein Eingabeparameter, der zum Angeben der Auftrags-ID verwendet wird, und der dritte Parameter ist ein Output-Parameter, der zum Abrufen der Kunden-ID verwendet wird:  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 Treiber behandeln Werte für Eingabe-und Eingabe-/Ausgabeparameter in Prozeduren, die nicht anders als Eingabeparameter in anderen SQL-Anweisungen Wenn die-Anweisung ausgeführt wird, rufen Sie die Werte der Variablen ab, die an diese Parameter gebunden sind, und senden Sie an die Datenquelle.  
  
 Nachdem die Anweisung ausgeführt wurde, speichern die Treiber die zurückgegebenen Werte der Eingabe-/Ausgabeparameter und Ausgabeparameter in den Variablen, die an diese Parameter gebunden sind. Diese zurückgegebenen Werte werden nicht garantiert festgelegt, bis alle von der Prozedur zurückgegebenen Ergebnisse abgerufen wurden und **SQLMoreResults** SQL_NO_DATA zurückgegeben hat. Wenn das Ausführen der Anweisung zu einem Fehler führt, ist der Inhalt des Eingabe-/ausgabeparameterpuffers oder des Ausgabeparameter Puffers nicht definiert.  
  
 Eine Anwendung ruft **SqlProcedure** auf, um zu bestimmen, ob eine Prozedur über einen Rückgabewert verfügt. Er ruft **sqlprocedurecolrens** auf, um den Typ (Rückgabewert, Eingabe, Eingabe/Ausgabe oder Ausgabe) der einzelnen Prozedur Parameter zu bestimmen.
