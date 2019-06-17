---
title: Ausführen von Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], executing
ms.assetid: a75e497a-4661-438a-a10e-f598c65f81be
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff234d1d8e099611c8718eac5ae3b584e926a2bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061968"
---
# <a name="executing-procedures"></a>Ausführen von Prozeduren
ODBC definiert eine standard-Escapesequenz Prozeduren ausgeführt werden. Die Syntax der Sequenz und ein Codebeispiel, das verwendet werden soll, finden Sie unter [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Um eine Prozedur auszuführen, führt eine Anwendung die folgenden Aktionen aus:  
  
1.  Legt die Werte aller Parameter. Weitere Informationen finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
2.  Aufrufe **SQLExecDirect** und übergibt sie eine Zeichenfolge, enthält die SQL-Anweisung, die die Prozedur ausgeführt wird. Diese Anweisung können die Escape-Sequenz, die von ODBC oder DBMS-spezifische Syntax definiert. Anweisungen, die DBMS-spezifische Syntax verwenden, können nicht zusammen.  
  
3.  Wenn **SQLExecDirect** aufgerufen wird, wird den Treiber:  
  
    -   Ruft die aktuellen Parameterwerte aus, und nach Bedarf konvertiert. Weitere Informationen finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Ruft die Prozedur in der Datenquelle, und sendet sie die Werte der konvertierte Parameter. Wie ruft der Treiber das Verfahren ist treiberspezifisch. Z. B. SQL-Anweisung zum Verwenden von SQL-Grammatik für die Datenquelle und senden diese Anweisung für die Ausführung ändern kann, oder es möglicherweise rufen Sie die Prozedur, die direkt mit einem (Remoteprozeduraufruf)-Mechanismus, der im Data Stream-Protokoll des DBMS definiert ist.  
  
    -   Gibt zurück, die Werte von jedem Eingabe-/Ausgabe- oder Output-Parameter oder der Prozedur zurückgegebene Wert, vorausgesetzt, dass die Prozedur erfolgreich ausgeführt wird. Diese Werte möglicherweise erst verfügbar, wenn nicht, nachdem alle anderen Ergebnisse (Zeilenanzahl und Resultsets) generiert, die von der Prozedur verarbeitet wurden. Wenn die Prozedur ein Fehler auftritt, gibt der Treiber alle Fehler zurück.
