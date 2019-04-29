---
title: Verwalten von Transaktionen (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c85b1f9db4667c64bed7cf87189e48b507e5f75
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63055075"
---
# <a name="managing-transactions-xmla"></a>Verwalten von Transaktionen (XMLA)
  Jeder Befehl XML for Analysis (XMLA) an eine Instanz des gesendeten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] innerhalb des Kontexts einer Transaktion auf der aktuellen impliziten oder expliziten Sitzung ausgeführt wird. Um alle diese Transaktionen zu verwalten, verwenden Sie die [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla), und [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) Befehle. Durch die Verwendung dieser Befehle können Sie implizite oder explizite Transaktionen erstellen, den Verweiszähler der Transaktion ändern, Transaktionen starten sowie einen Commit oder ein Rollback für diese Transaktionen ausführen.  
  
## <a name="implicit-and-explicit-transactions"></a>Implizite und explizite Transaktionen  
 Eine Transaktion ist entweder implizit oder explizit:  
  
 **Implizite Transaktion**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt eine *implizite* Transaktion für einen XMLA-Befehl, wenn die **BeginTransaction** -Befehl nicht den Beginn einer Transaktion angibt. Wenn der Befehl erfolgreich ist, führt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] immer einen Commit für die implizite Transaktionen aus, und wenn der Befehl einen Fehler generiert, wird ein Rollback für die implizite Transaktion ausgeführt.  
  
 **Explizite Transaktion**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt eine *explizite* Transaktion Wenn die **BeginTransaction** Befehl startet eine Transaktion. Allerdings [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nur eine explizite Transaktion ein Commit wird, wenn eine **CommitTransaction** Befehl gesendet wird und ein Rollback für eine explizite Transaktion aus, wenn eine **RollbackTransaction** -Befehl gesendet wird.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] führt zudem ein Rollback sowohl für implizite als auch für explizite Transaktionen aus, wenn die aktuelle Sitzung beendet wird, bevor die aktive Transaktion fertiggestellt wird.  
  
## <a name="transactions-and-reference-counts"></a>Transaktionen und Verweiszähler  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwaltet einen Transaktionsverweiszähler für jede Sitzung. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt jedoch keine geschachtelten Transaktionen, da nur eine aktive Transaktion pro Sitzung verwaltet wird. Wenn die aktuelle Sitzung keine aktive Transaktion besitzt, wird der Transaktionsverweiszähler auf null festgelegt.  
  
 Das heißt, jede **BeginTransaction** Befehl inkrementiert den Verweiszähler um eins, während jeder **CommitTransaction** Befehl dekrementiert den Verweiszähler um eins. Wenn eine **CommitTransaction** Befehl wird die Transaktionsanzahl auf 0 (null), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] führt einen Commit der Transaktion.  
  
 Allerdings die **RollbackTransaction** Befehl setzt die aktive Transaktion unabhängig vom aktuellen Wert der Verweiszähler der Transaktion zurück. Das heißt, eine einzelne **RollbackTransaction** Befehl Rollback für die aktive Transaktion, unabhängig davon, wie viele **BeginTransaction** Befehle oder **CommitTransaction** Befehle gesendet wurden, und legt den transaktionsverweiszähler auf NULL.  
  
## <a name="beginning-a-transaction"></a>Beginnen einer Transaktion  
 Die **BeginTransaction** Befehl startet eine explizite Transaktion für die aktuelle Sitzung und erhöht den transaktionsverweiszähler für die aktuelle Sitzung um eins. Alle nachfolgenden Befehle gelten als innerhalb der aktiven Transaktion, bis entweder genug **CommitTransaction** Befehle werden an die aktive Transaktion oder ein einzelnes commit gesendet **RollbackTransaction**Befehl an die aktive Transaktion ein Rollback gesendet.  
  
## <a name="committing-a-transaction"></a>Commitausführung für eine Transaktion  
 Die **CommitTransaction** Befehl führt einen Commit für die Ergebnisse von Befehlen, die ausgeführt werden, nachdem die **BeginTransaction** -Befehl in der aktuellen Sitzung ausgeführt wurde. Jede **CommitTransaction** -Befehl verringert den Verweiszähler für aktive Transaktionen auf eine Sitzung. Wenn eine **CommitTransaction** Befehl wird den Verweiszähler auf 0 (null), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] führt einen Commit für die aktive Transaktion. Wenn keine aktive Transaktion vorhanden ist (das heißt, der transaktionsverweiszähler für die aktuelle Sitzung ist bereits festgelegt auf 0 (null)), eine **CommitTransaction** Befehl führt zu einem Fehler.  
  
## <a name="rolling-back-a-transaction"></a>Ausführen von Rollbacks für eine Transaktion  
 Die **RollbackTransaction** Befehl Rollback für die Ergebnisse von Befehlen, die ausgeführt werden, nachdem die **BeginTransaction** -Befehl in der aktuellen Sitzung ausgeführt wurde. Die **RollbackTransaction** Befehl führt einen Rollback für die aktive Transaktion, unabhängig von der aktuellen transaktionsverweiszähler, und legt den transaktionsverweiszähler auf NULL fest. Wenn keine aktive Transaktion vorhanden ist (das heißt, der transaktionsverweiszähler für die aktuelle Sitzung ist bereits festgelegt auf 0 (null)), eine **RollbackTransaction** Befehl führt zu einem Fehler.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
