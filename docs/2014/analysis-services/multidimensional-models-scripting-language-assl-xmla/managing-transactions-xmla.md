---
title: Verwalten von Transaktionen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, transactions
- XMLA, transactions
- explicit transactions [XMLA]
- implicit transactions
- transactions [XML for Analysis]
- rolling back transactions, XMLA
- reference counts [XML for Analysis]
- committing transactions
- starting transactions
ms.assetid: f5112e01-82f8-4870-bfb7-caa00182c999
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad8a77d1d8552dc811c1232afb53c142452658db
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154757"
---
# <a name="managing-transactions-xmla"></a>Verwalten von Transaktionen (XMLA)
  Jeder Befehl XML for Analysis (XMLA) an eine Instanz des gesendeten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] innerhalb des Kontexts einer Transaktion auf der aktuellen impliziten oder expliziten Sitzung ausgeführt wird. Um alle diese Transaktionen zu verwalten, verwenden Sie die [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla), und [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) Befehle. Durch die Verwendung dieser Befehle können Sie implizite oder explizite Transaktionen erstellen, den Verweiszähler der Transaktion ändern, Transaktionen starten sowie einen Commit oder ein Rollback für diese Transaktionen ausführen.  
  
## <a name="implicit-and-explicit-transactions"></a>Implizite und explizite Transaktionen  
 Eine Transaktion ist entweder implizit oder explizit:  
  
 **Implizite Transaktion**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt eine *implizite* Transaktion für einen XMLA-Befehl, wenn die `BeginTransaction` -Befehl nicht den Beginn einer Transaktion angibt. Wenn der Befehl erfolgreich ist, führt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] immer einen Commit für die implizite Transaktionen aus, und wenn der Befehl einen Fehler generiert, wird ein Rollback für die implizite Transaktion ausgeführt.  
  
 **Explizite Transaktion**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt eine *explizite* Transaktion Wenn die `BeginTransaction` Befehl startet eine Transaktion. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] führt jedoch einen Commit für eine explizite Transaktion nur aus, wenn ein `CommitTransaction`-Befehl gesendet wird und führt ein Rollback für eine explizite Transaktion aus, wenn ein `RollbackTransaction`-Befehl gesendet wird.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] führt zudem ein Rollback sowohl für implizite als auch für explizite Transaktionen aus, wenn die aktuelle Sitzung beendet wird, bevor die aktive Transaktion fertiggestellt wird.  
  
## <a name="transactions-and-reference-counts"></a>Transaktionen und Verweiszähler  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwaltet einen Transaktionsverweiszähler für jede Sitzung. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt jedoch keine geschachtelten Transaktionen, da nur eine aktive Transaktion pro Sitzung verwaltet wird. Wenn die aktuelle Sitzung keine aktive Transaktion besitzt, wird der Transaktionsverweiszähler auf null festgelegt.  
  
 Dies bedeutet, dass jeder `BeginTransaction`-Befehl den Verweiszähler um eins erhöht, während jeder `CommitTransaction`-Befehl den Verweiszähler um eins verringert. Wenn ein `CommitTransaction`-Befehl den Transaktionszähler auf null festlegt, führt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] einen Commit für die Transaktion aus.  
  
 Der `RollbackTransaction`-Befehl führt jedoch unabhängig vom aktuellen Wert des Transaktionsverweiszählers ein Rollback für die aktive Transaktion aus. Das heißt, ein einzelner `RollbackTransaction`-Befehl führt ein Rollback für die aktive Transaktion aus, unabhängig davon, wie viele `BeginTransaction`- oder `CommitTransaction`-Befehle gesendet wurden, und legt den Transaktionsverweiszähler auf null fest.  
  
## <a name="beginning-a-transaction"></a>Beginnen einer Transaktion  
 Der `BeginTransaction`-Befehl beginnt eine explizite Transaktion für die aktuelle Sitzung und erhöht den Transaktionsverweiszähler für die aktuelle Sitzung um eins. Alle nachfolgenden Befehle werden als innerhalb der aktiven Transaktion befindlich betrachtet, bis entweder genug `CommitTransaction`-Befehle gesendet wurden, um einen Commit für die aktive Transaktion auszuführen, oder ein einzelner `RollbackTransaction`-Befehl gesendet wird, um ein Rollback für die aktive Transaktion auszuführen.  
  
## <a name="committing-a-transaction"></a>Commitausführung für eine Transaktion  
 Der `CommitTransaction` -Befehl führt einen Commit für die Ergebnisse von Befehlen aus, die ausgeführt werden, nachdem der `BeginTransaction`-Befehl für die aktuelle Sitzung ausgeführt wurde. Jeder `CommitTransaction`-Befehl verringert den Verweiszähler für aktive Transaktionen für eine Sitzung. Wenn ein `CommitTransaction`-Befehl den Verweiszähler auf null festlegt, führt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] einen Commit für die aktive Transaktion aus. Wenn keine aktive Transaktion vorhanden ist (das heißt, wenn der Transaktionsverweiszähler für die aktuelle Sitzung bereits auf null festgelegt ist), führt ein `CommitTransaction`-Befehl zu einem Fehler.  
  
## <a name="rolling-back-a-transaction"></a>Ausführen von Rollbacks für eine Transaktion  
 Der `RollbackTransaction` -Befehl führt ein Rollback für die Ergebnisse von Befehlen aus, die ausgeführt werden, nachdem der `BeginTransaction`-Befehl für die aktuelle Sitzung ausgeführt wurde. Der `RollbackTransaction`-Befehl führt unabhängig von dem aktuellen Transaktionsverweiszähler ein Rollback für die aktive Transaktion aus und legt den Transaktionsverweiszähler auf null fest. Wenn keine aktive Transaktion vorhanden ist (das heißt, wenn der Transaktionsverweiszähler für die aktuelle Sitzung bereits auf null festgelegt ist), führt ein `RollbackTransaction`-Befehl zu einem Fehler.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
