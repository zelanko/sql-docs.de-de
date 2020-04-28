---
title: Prozeduren ausführen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a796c615d7dfdec11a9acb90ab4b5129cf69717
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305711"
---
# <a name="executing-procedures"></a>Ausführen von Prozeduren
ODBC definiert eine Standard-Escapesequenz zum Ausführen von Prozeduren Die Syntax dieser Sequenz und ein Codebeispiel, in dem Sie verwendet wird, finden Sie unter [Prozedur Aufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Zum Ausführen einer Prozedur führt eine Anwendung die folgenden Aktionen aus:  
  
1.  Legt die Werte von Parametern fest. Weitere Informationen finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
2.  Ruft **SQLExecDirect** auf und übergibt ihm eine Zeichenfolge, die die SQL-Anweisung enthält, die die Prozedur ausführt. Diese Anweisung kann die von der ODBC-oder DBMS-spezifische Syntax definierte Escapesequenz verwenden. -Anweisungen, die DBMS-spezifische Syntax verwenden, sind nicht interoperabel.  
  
3.  Wenn **SQLExecDirect** aufgerufen wird, führt der Treiber Folgendes aus:  
  
    -   Ruft die aktuellen Parameterwerte ab und konvertiert sie nach Bedarf. Weitere Informationen finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Ruft die Prozedur in der Datenquelle auf und sendet Sie die konvertierten Parameterwerte. Die Art und Weise, wie der Treiber die Prozedur aufruft, ist Treiber spezifisch. Beispielsweise kann die SQL-Anweisung geändert werden, um die SQL-Grammatik der Datenquelle zu verwenden und diese Anweisung zur Ausführung zu übermitteln, oder Sie kann die Prozedur direkt mithilfe eines RPC-Mechanismus (Remote Procedure Aufruf) abrufen, der im Datenstrom Protokoll des DBMS definiert ist.  
  
    -   Gibt die Werte aller Eingabe-/Ausgabe-oder Ausgabeparameter oder den Rückgabewert der Prozedur zurück, sofern die Prozedur erfolgreich ausgeführt wurde. Diese Werte sind möglicherweise erst verfügbar, wenn alle anderen Ergebnisse (Zeilen Anzahl und Resultsets), die von der Prozedur generiert wurden, verarbeitet wurden. Wenn die Prozedur fehlschlägt, gibt der Treiber alle Fehler zurück.
