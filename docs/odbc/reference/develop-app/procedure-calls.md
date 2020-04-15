---
title: Verfahrensaufrufe | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282230"
---
# <a name="procedure-calls"></a>Prozeduraufrufe
Eine *Prozedur* ist ein ausführbares Objekt, das in der Datenquelle gespeichert ist. In der Regel handelt es sich dabei um eine oder mehrere vorkompilierte SQL-Anweisungen. Die Escape-Sequenz für das Aufrufen einer Prozedur ist  
  
 **•**[**?=**]**Prozedurname** *procedure-name*aufrufen [**(**[*Parameter*][**,**[*Parameter*]]... **)**]**}**  
  
 wobei *procedure-name* den Namen einer Prozedur angibt und *der Parameter* einen Prozedurparameter angibt.  
  
 Weitere Informationen zur Prozeduraufruf-Escapesequenz finden Sie unter [Prozeduraufruf-Escapesequenz](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md) in Anhang C: SQL-Grammatik.  
  
 Eine Prozedur kann 0 (null) oder mehr Parameter haben. Es kann auch einen Wert zurückgeben, wie durch die optionale Parametermarkierung **?=** am Anfang der Syntax angegeben. Wenn *der Parameter* ein Eingabe- oder ein Eingabe-/Ausgabeparameter ist, kann es sich um ein Literal oder eine Parametermarkierung handeln. Interoperable Anwendungen sollten jedoch immer Parametermarkierungen verwenden, da einige Datenquellen keine Literalparameterwerte akzeptieren. Wenn *parameter* ein Ausgabeparameter ist, muss er eine Parametermarkierung sein. Parametermarkierungen müssen mit **SQLBindParameter** gebunden werden, bevor die Prozeduraufrufanweisung ausgeführt wird.  
  
 Eingabe- und Eingabe-/Ausgabeparameter müssen in Prozeduraufrufen nicht angegeben werden. Wenn eine Prozedur mit Klammern, aber ohne Parameter aufgerufen wird, z. B. "Call *Procedure-Name*()", weist der Treiber die Datenquelle an, den Standardwert für den ersten Parameter zu verwenden. Wenn die Prozedur keine Parameter enthält, kann dies dazu führen, dass die Prozedur fehlschlägt. Wenn eine Prozedur ohne Klammern aufgerufen wird, z. B. "Call *Procedure-Name",* sendet der Treiber keine Parameterwerte.  
  
 Literalwerte können in Prozeduraufrufen für Eingabe- und Eingabe-/Ausgabeparameter angegeben werden. Angenommen, die Prozedur **InsertOrder** verfügt über fünf Eingabeparameter. Der folgende Aufruf von **InsertOrder** lässt den ersten Parameter aus, stellt ein Literal für den zweiten Parameter bereit und verwendet eine Parametermarkierung für den dritten, vierten und fünften Parameter:  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 Beachten Sie, dass, wenn ein Parameter weggelassen wird, das Komma, das ihn von anderen Parametern abgrenzt, weiterhin angezeigt werden muss. Wenn ein Eingabe- oder ein Eingabe-/Ausgabeparameter ausgelassen wird, verwendet die Prozedur den Standardwert des Parameters. Eine andere Möglichkeit, den Standardwert eines Eingabe- oder Eingabe-/Ausgabeparameters anzugeben, besteht darin, den Wert des an den Parameter gebundenen Längen-/Indikatorpuffers auf SQL_DEFAULT_PARAM festzulegen.  
  
 Wenn ein Eingabe-/Ausgabeparameter weggelassen wird oder ein Literal für den Parameter angegeben wird, verwirft der Treiber den Ausgabewert. Entsprechend verwirft der Treiber den Rückgabewert, wenn die Parametermarkierung für den Rückgabewert einer Prozedur ausgelassen wird. Wenn eine Anwendung den Parameter des Rückgabewerts für eine Prozedur angibt, die keinen Wert zurückgibt, legt der Treiber den Wert des an den Parameter gebundenen Längen-/Indikatorpuffers auf SQL_NULL_DATA fest.  
  
 Angenommen, die Prozedur PARTS_IN_ORDERS erstellt ein Resultset, das eine Liste von Aufträgen enthält, die eine bestimmte Teilenummer enthalten. Der folgende Code ruft dieses Verfahren für die Teilenummer 544 auf:  
  
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
  
 Um zu bestimmen, ob eine Datenquelle Prozeduren unterstützt, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_PROCEDURES auf.  
  
 Weitere Informationen zu Prozeduren finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).
