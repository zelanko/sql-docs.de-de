---
title: Prozeduraufrufe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure calls
- procedure calls [ODBC]
ms.assetid: 145130cc-40e7-4722-8417-dff131084752
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 926ee91fae207d50248df4c82d1b82bb6424e239
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023253"
---
# <a name="procedure-calls"></a>Prozeduraufrufe
Ein *Prozedur* ein ausführbares Objekt in der Datenquelle gespeichert ist. In der Regel handelt es sich dabei um eine oder mehrere vorkompilierte SQL-Anweisungen. Die-Escapesequenz zum Aufrufen einer Prozedur ist.  
  
 **{** [ **? =** ]**Aufrufen** *Prozedurname*[ **(** [*Parameter*] [ **,** [*Parameter*]]... **)** ] **}**  
  
 in denen *Prozedurname* gibt den Namen einer Prozedur und *Parameter* gibt die Parameter einer Prozedur an.  
  
 Weitere Informationen zu die Prozedur Call-Escape-Sequenz, finden Sie unter [Prozedur Call-Escapesequenz](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md) in Anhang C: SQL-Grammatik.  
  
 Eine Prozedur kann 0 (null) oder mehr Parameter haben. Sie können auch einen Wert zurückgeben, wie durch die optionale parametermarkierung **? =** am Anfang der Syntax. Wenn *Parameter* ist eine Eingabe oder ein Eingabe-/Ausgabeparameter, es kann ein Literal oder eine parametermarkierung sein. Interoperable Anwendungen ausführen können sollten jedoch immer parametermarkierungen verwenden, da einige Datenquellen keine Werte für Zeichenfolgenliteral-Parameter akzeptieren. Wenn *Parameter* ist ein Output-Parameter muss eine parametermarkierung sein. Parametermarkierungen müssen gebunden werden **SQLBindParameter** vor dem Aufruf der Prozedur die Anweisung ausgeführt wird.  
  
 Eingabe- und Eingabe-/Ausgabeparameter müssen in Prozeduraufrufen nicht angegeben werden. Wenn eine Prozedur mit Klammern aber ohne Parameter, wie z. B. aufgerufen wird, {Aufrufen *Prozedurname*()}, der Treiber angewiesen, die Datenquelle auf den Standardwert für den ersten Parameter verwenden. Wenn die Prozedur keine Parameter, kann dies dazu führen, dass die Prozedur fehlschlägt. Wenn eine Prozedur ohne Klammern, wie z. B. aufgerufen wird {aufrufen *Prozedurname*}, sendet der Treiber keine Parameterwerte.  
  
 Literalwerte können in Prozeduraufrufen für Eingabe- und Eingabe-/Ausgabeparameter angegeben werden. Nehmen wir beispielsweise an die Prozedur **InsertOrder** fünf Eingabeparameter aufweisen. Der folgende Aufruf von **InsertOrder** der erste Parameter und stellt ein Literal für den zweiten Parameter wird eine parametermarkierung verwendet wird, für den dritten, vierten und fünften Parameter:  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 Beachten Sie, dass wenn ein Parameter weggelassen wird, muss das Komma als Trennzeichen es von anderen Parametern weiterhin angezeigt. Wenn ein Eingabe- oder ein Eingabe-/Ausgabeparameter ausgelassen wird, verwendet die Prozedur den Standardwert des Parameters. Eine weitere Möglichkeit, um anzugeben, dass der Standardwert eines Eingabe- oder Eingabe/Ausgabe-Parameters ist, zum Festlegen des Werts, der den Längen-/Indikatorpuffer, die an den Parameter auf SQL_DEFAULT_PARAM gebunden werden.  
  
 Wenn ein Eingabe-/Ausgabeparameter ausgelassen wird oder ein Literal für den Parameter angegeben wird, verwirft der Treiber den Ausgabewert. Entsprechend verwirft der Treiber den Rückgabewert, wenn die Parametermarkierung für den Rückgabewert einer Prozedur ausgelassen wird. Wenn eine Anwendung den Parameter des Rückgabewerts für eine Prozedur angibt, die keinen Wert zurückgibt, legt der Treiber den Wert des an den Parameter gebundenen Längen-/Indikatorpuffers auf SQL_NULL_DATA fest.  
  
 Nehmen wir an, dass die Prozedur PARTS_IN_ORDERS ein Resultset erstellt, die eine Liste der Aufträge enthält, die eine bestimmte Teilenummer enthalten. Der folgende Code ruft diese Prozedur für die Teilenummer 544:  
  
```  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_SLONG, SQL_INTEGER, 0, 0,  
                  &PartID, 0, PartIDInd);  
  
// Place the department number in PartID.  
PartID = 544;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "{call PARTS_IN_ORDERS(?)}", SQL_NTS);  
```  
  
 Um zu bestimmen, ob eine Datenquelle Prozeduren unterstützt, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_PROCEDURES.  
  
 Weitere Informationen zu Prozeduren finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).
