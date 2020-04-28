---
title: Prozedur Aufrufe | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9c52e72512c8b81c6872461207f235ea2731ac5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282230"
---
# <a name="procedure-calls"></a>Prozeduraufrufe
Eine *Prozedur* ist ein ausführbares Objekt, das in der Datenquelle gespeichert ist. In der Regel handelt es sich dabei um eine oder mehrere vorkompilierte SQL-Anweisungen. Die Escapesequenz zum Aufrufen einer Prozedur ist  
  
 **{**[**? =**]**aufrufen** *von Prozedur Name*[**(**[*Parameter*] [**,**[*Parameter*]]... **)**]**}**  
  
 Where *Procedure-Name* gibt den Namen einer Prozedur an, und *Parameter* gibt einen Prozedur Parameter an.  
  
 Weitere Informationen über die Prozedur Rückruf-Escapesequenz finden Sie unter [Prozedur Aufrufe-Escapesequenz](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md) in Anhang C: SQL-Grammatik.  
  
 Eine Prozedur kann 0 (null) oder mehr Parameter haben. Sie kann auch einen Wert zurückgeben, wie vom optionalen Parametermarker **? =** am Anfang der Syntax angegeben. Wenn der *Parameter* ein Eingabe-oder ein Eingabe-/Ausgabeparameter ist, kann er ein Literalwert oder ein Parametermarker sein. Allerdings sollten interoperable Anwendungen immer Parametermarker verwenden, da einige Datenquellen keine literalen Parameterwerte akzeptieren. Wenn der *Parameter* ein Ausgabeparameter ist, muss es sich um eine Parameter Markierung handeln. Parameter Markierungen müssen mit **SQLBindParameter** gebunden werden, bevor die Prozedur aufrufen-Anweisung ausgeführt wird.  
  
 Eingabe- und Eingabe-/Ausgabeparameter müssen in Prozeduraufrufen nicht angegeben werden. Wenn eine Prozedur mit Klammern, aber ohne Parameter aufgerufen wird, z. b. {Aufruf *Prozedur Name*()}, weist der Treiber die Datenquelle an, den Standardwert für den ersten Parameter zu verwenden. Wenn die Prozedur keine Parameter enthält, kann dies dazu führen, dass die Prozedur fehlschlägt. Wenn eine Prozedur ohne Klammern aufgerufen wird, z. b. {Aufruf *Prozedur Name*}, sendet der Treiber keine Parameterwerte.  
  
 Literalwerte können in Prozeduraufrufen für Eingabe- und Eingabe-/Ausgabeparameter angegeben werden. Nehmen wir beispielsweise an, dass die Prozedur **InsertOrder** über fünf Eingabeparameter verfügt. Der folgende Rückruf von **InsertOrder** lässt den ersten Parameter aus, stellt ein Literalzeichen für den zweiten Parameter bereit und verwendet eine Parameter Markierung für den dritten, vierten und fünften Parameter:  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 Beachten Sie Folgendes: Wenn ein Parameter weggelassen wird, muss das Komma, das es aus anderen Parametern abgrenzt, weiterhin angezeigt werden. Wenn ein Eingabe- oder ein Eingabe-/Ausgabeparameter ausgelassen wird, verwendet die Prozedur den Standardwert des Parameters. Eine andere Möglichkeit, den Standardwert eines Eingabe-oder Eingabe-/Ausgabeparameters anzugeben, besteht darin, den Wert des an den-Parameter gebundenen Längen-/Indikatorpuffers auf SQL_DEFAULT_PARAM festzulegen.  
  
 Wenn ein Eingabe-/Ausgabeparameter ausgelassen wird oder wenn ein Literalwert für den Parameter angegeben wird, verwirft der Treiber den Ausgabewert. Entsprechend verwirft der Treiber den Rückgabewert, wenn die Parametermarkierung für den Rückgabewert einer Prozedur ausgelassen wird. Wenn eine Anwendung den Parameter des Rückgabewerts für eine Prozedur angibt, die keinen Wert zurückgibt, legt der Treiber den Wert des an den Parameter gebundenen Längen-/Indikatorpuffers auf SQL_NULL_DATA fest.  
  
 Angenommen, die Prozedur PARTS_IN_ORDERS erstellt ein Resultset, das eine Liste von Bestellungen enthält, die eine bestimmte Teilenummer enthalten. Mit dem folgenden Code wird diese Prozedur für die Teilenummer 544 aufgerufen:  
  
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
  
 Um zu ermitteln, ob eine Datenquelle Prozeduren unterstützt, ruft eine Anwendung **SQLGetInfo** mit der SQL_PROCEDURES-Option auf.  
  
 Weitere Informationen zu Prozeduren finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).
