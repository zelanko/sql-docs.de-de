---
title: Ausführen von Prozeduren | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305711"
---
# <a name="executing-procedures"></a>Ausführen von Prozeduren
ODBC definiert eine Standard-Escapesequenz für die Ausführung von Prozeduren. Die Syntax dieser Sequenz und ein Codebeispiel, das sie verwendet, finden Sie unter [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Um eine Prozedur auszuführen, führt eine Anwendung die folgenden Aktionen aus:  
  
1.  Legt die Werte aller Parameter fest. Weitere Informationen finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
2.  Ruft **SQLExecDirect** auf und übergibt ihm eine Zeichenfolge, die die SQL-Anweisung enthält, die die Prozedur ausführt. Diese Anweisung kann die Escapesequenz verwenden, die durch ODBC- oder DBMS-spezifische Syntax definiert wird. Anweisungen, die DBMS-spezifische Syntax verwenden, sind nicht interoperabel.  
  
3.  Wenn **SQLExecDirect** aufgerufen wird, lautet der Treiber:  
  
    -   Ruft die aktuellen Parameterwerte ab und konvertiert sie bei Bedarf. Weitere Informationen finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Ruft die Prozedur in der Datenquelle auf und sendet ihr die konvertierten Parameterwerte. Wie der Treiber die Prozedur aufruft, ist treiberspezifisch. Sie kann z. B. die SQL-Anweisung ändern, um die SQL-Grammatik der Datenquelle zu verwenden und diese Anweisung zur Ausführung zu übermitteln, oder sie ruft die Prozedur direkt mithilfe eines RPC-Mechanismus (Remote Procedure Call) auf, der im Datenstromprotokoll des DBMS definiert ist.  
  
    -   Gibt die Werte aller Eingabe-/Ausgabe- oder Ausgabeparameter oder des Prozedurrückgabewerts zurück, vorausgesetzt, die Prozedur ist erfolgreich. Diese Werte sind möglicherweise erst verfügbar, nachdem alle anderen ergebnisse (Zeilenanzahl und Resultsets), die von der Prozedur generiert wurden, verarbeitet wurden. Wenn die Prozedur fehlschlägt, gibt der Treiber alle Fehler zurück.
