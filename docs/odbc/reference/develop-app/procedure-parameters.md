---
title: Prozedurparameter | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 1cab0fea9c39e4946122698f2476668464e556c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751861"
---
# <a name="procedure-parameters"></a>Prozedurparameter
In Prozeduraufrufen können eingegeben werden, Eingabe/Ausgabe- oder Ausgabeparameter enthalten. Dies unterscheidet sich von Parametern in allen anderen SQL-Anweisungen, die immer Eingabeparameter sind.  
  
 Eingabeparameter werden verwendet, um Werte für die Prozedur zu senden. Nehmen wir beispielsweise an, dass die Parts-Tabelle die Spalten PartID, Beschreibung und Preis verfügt. Die Prozedur InsertPart möglicherweise einen Eingabeparameter für jede Spalte in der Tabelle. Zum Beispiel:  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 Ein Treiber sollte nicht ändern Sie den Inhalt von einem Eingabepuffer bis **SQLExecDirect** oder **SQLExecute** SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_NO_DATA zurückgibt. Der Inhalt des Eingabepuffers sollte nicht geändert werden zwar **SQLExecDirect** oder **SQLExecute** gibt SQL_NEED_DATA oder SQL_STILL_EXECUTING zurück.  
  
 Eingabe/Ausgabe-Parameter werden verwendet, um Werte an Prozeduren senden und Abrufen von Werten aus Prozeduren. Mit dem gleichen Parameter wie sowohl Eingabe-als auch ein Output-Parameter ist verwirrend sein und sollte vermieden werden. Nehmen wir beispielsweise an eine Prozedur akzeptiert eine Auftrags-ID und gibt die ID des Kunden zurück. Dies kann mit einem einzelnen Eingabe/Ausgabe-Parameter definiert werden:  
  
```  
{call GetCustID(?)}  
```  
  
 Möglicherweise ist es besser, verwenden Sie zwei Parameter: einen Eingabeparameter für die Bestell-ID und eines Ausgabe- oder Eingabe-/Ausgabeparameter für die Kunden-ID:  
  
```  
{call GetCustID(?, ?)}  
```  
  
 Output-Parameter den Prozedur zurückgegebene Wert abrufen und Abrufen von Werten aus Prozedurargumente verwendet; Prozeduren, die Werte zurückgeben, werden manchmal als bezeichnet *Funktionen*. Nehmen wir beispielsweise an die **GetCustID** erwähnte Verfahren gibt einen Wert, der angibt, ob die Reihenfolge gefunden werden konnte. In den folgenden Aufruf der erste Parameter ist ein Output-Parameter, die zum Abrufen des Prozedur zurückgegebene Wert, der zweite Parameter ist ein Eingabeparameter verwendet, um die Bestell-ID anzugeben, und der dritte Parameter ist ein Output-Parameter verwendet, um die Kunden-ID abzurufen:  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 Treiber Behandeln von Werten für die Eingabe und e/a Parameter in Prozeduren nicht anders als Eingabeparameter in anderen SQL­Anweisungen. Wenn die Anweisung ausgeführt wird, rufen sie die Werte der Variablen für diese Parameter gebunden, und senden sie an der Datenquelle.  
  
 Nachdem die Anweisung ausgeführt wurde, speichern Treiber zurückgegebenen Werte der e/a und Output-Parameter in den Variablen, die an diesen Parameter gebunden. Diese zurückgegebenen Werte nicht garantiert, dass erst festgelegt werden, nachdem alle von der Prozedur zurückgegebene Ergebnisse abgerufen wurden und **SQLMoreResults** SQL_NO_DATA zurückgegeben hat. Wenn die Ausführung der Anweisung zu einem Fehler führt, sind die Inhalte der Eingabe-/Ausgabeparameter Puffer oder in der Ausgabepuffer für die Parameter nicht definiert.  
  
 Ruft die Anwendung **SQLProcedure** bestimmen, ob eine Prozedur einen Rückgabewert verfügt. Ruft **SQLProcedureColumns** zum Bestimmen des Typs (Rückgabewert, Eingabe-, Eingabe/Ausgabe- oder Ausgabeparameter) der einzelnen Prozedurparameter.
