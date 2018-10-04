---
title: Grundlegendes zu Transaktionen auf speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 06075248-705e-4563-9371-b64cd609793c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4aaefdcd2739b2036703cdb7235fe56865ff1fed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064630"
---
# <a name="understanding-transactions-on-memory-optimized-tables"></a>Grundlegendes zu Transaktionen in speicheroptimierten Tabellen
  Transaktionen greifen über eine Form der Multiversionsverwaltung und optimistischen Nebenläufigkeitssteuerung auf speicheroptimierte Tabellen zu. Dies bedeutet, dass es zwei verschiedene Datenversionen gibt. Jede Transaktion verwendet ihre eigene, im Hinblick auf Transaktionen konsistente Datenbankversion, und zwar unabhängig von anderen gleichzeitig ausgeführten Transaktionen. Darüber hinaus werden Transaktionen unter der optimistischen Annahme ausgeführt, dass keine Konflikte mit anderen, gleichzeitig laufenden Transaktionen bestehen. Einerseits entfällt dadurch die Notwendigkeit von Sperren, andererseits muss das System die Konflikte erkennen und eine der konfliktverursachenden Transaktionen beenden. Konflikte können nur bei Write-Write-Transaktionen und Read-Write-Transaktionen auftreten. Wenn ein Write-Write-Konflikt auftritt, wird eine Schreibtransaktion beendet.  
  
 Es gibt Ähnlichkeiten zwischen der Parallelitätssteuerung für speicheroptimierte Tabellen und der Parallelitätssteuerung für datenträgerbasierte Tabellen mit der Transaktionsisolationsstufe READ_COMMITTED_SNAPSHOT oder SNAPSHOT. (Weitere Informationen zu datenträgerbasierten Tabellen, finden Sie unter [auf Zeilenversionsverwaltung basierende Isolation Levels in der Datenbank-Engine](http://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx).)  
  
## <a name="topics-in-this-section"></a>Themen in diesem Abschnitt  
 Dieser Abschnitt über Transaktionen in speicheroptimierten Tabellen enthält folgende Themen:  
  
-   [Richtlinien für Transaktionsisolationsstufen mit speicheroptimierten Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
-   [Richtlinien zur Wiederholungslogik für Transaktionen auf speicheroptimierten Tabellen](guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
-   [Transaktionen in speicheroptimierten Tabellen](transactions-in-memory-optimized-tables.md)  
  
-   [Transaktionsisolationsstufen](transaction-isolation-levels.md)  
  
-   [Containerübergreifende Transaktionen](cross-container-transactions.md)  
  
 Weitere Informationen finden Sie im Thema [Steuern der Transaktionsdauerhaftigkeit](../relational-databases/logs/control-transaction-durability.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Speicheroptimierte Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
