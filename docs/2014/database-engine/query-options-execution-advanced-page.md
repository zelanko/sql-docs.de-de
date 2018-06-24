---
title: Abfrageergebnis (Seite erweitert) Ausführung | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5cdff5f44079c6c4946f30f9d4cc12ecc1bcac85
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046726"
---
# <a name="query-options-execution-advanced-page"></a>Abfrageausführung (Seite Erweitert)
  Bei Verwendung der **SET** -Anweisung ist eine Vielzahl von Optionen verfügbar. Mithilfe dieser Seite geben Sie eine **set** -Option für die Ausführung von Microsoft SQL Server-Abfragen an. Detaillierte Informationen zu jeder dieser Optionen finden Sie in der SQL Server-Onlinedokumentation.  
  
 **SET NOCOUNT**  
 Es wird nicht die Anzahl der Zeilen als Meldung mit dem Resultset zurückgegeben. Diese Option ist standardmäßig deaktiviert.  
  
 **SET NOEXEC**  
 Die Abfrage wird nicht ausgeführt. Diese Option ist standardmäßig deaktiviert.  
  
 **SET PARSEONLY**  
 Prüft die Syntax der einzelnen Abfragen, führt die Abfragen aber nicht aus. Diese Option ist standardmäßig deaktiviert.  
  
 **SET CONCAT_NULL_YIELDS_NULL**  
 Wenn dieses Kontrollkästchen aktiviert ist, geben Abfragen, von denen ein vorhandener Wert mit einer `NULL` verkettet wird, als Ergebnis immer eine `NULL` zurück. Wenn dieses Kontrollkästchen deaktiviert ist, gibt ein vorhandener, mit einer `NULL` verketteter Wert, den vorhandenen Wert zurück. Diese Option ist standardmäßig aktiviert.  
  
 **SET ARITHABORT**  
 Wenn dieses Kontrollkästchen aktiviert ist und eine `INSERT`-, `DELETE`- oder `UPDATE`-Anweisung bei der Auswertung des Ausdrucks einen arithmetischer Fehler (Überlauf, Division durch null oder Domänenfehler) findet, wird die Abfrage bzw. der Batch beendet. Wenn dieses Kontrollkästchen deaktiviert ist, wird für diesen Wert nach Möglichkeit eine `NULL` bereitgestellt, die Abfrage fortgesetzt und in das Ergebnis eine Meldung eingeschlossen. Eine ausführlichere Beschreibung dieses Verhaltens finden Sie in der Onlinedokumentation. Diese Option ist standardmäßig aktiviert.  
  
 **SET SHOWPLAN_TEXT**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird bei jeder Abfrage der Abfrageplan in Textform zurückgegeben. Diese Option ist standardmäßig deaktiviert.  
  
 **SET STATISTICS TIME**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird bei jeder Abfrage die Zeitstatistik zurückgegeben. Diese Option ist standardmäßig deaktiviert.  
  
 **SET STATISTICS IO**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird bei jeder Abfrage die E/A-bezogene Statistik (Eingabe/Ausgabe) zurückgegeben. Diese Option ist standardmäßig deaktiviert.  
  
 **SET TRANSACTION ISOLATION LEVEL**  
 Die Transaktionsisolationsstufe READ COMMITTED wird standardmäßig festgelegt. Weitere Informationen finden Sie unter [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql). Die MOMENTAUFNAHME-Transaktionsisolationsstufe ist nicht verfügbar. Fügen Sie zum Verwenden der MOMENTAUFNAHME-Isolation die folgende [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisung hinzu:  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 **SET DEADLOCK PRIORITY**  
 Beim Standardwert **Normal** kann jede Abfrage bei Auftreten eines Deadlock dieselbe Priorität haben. Wählen Sie in der Dropdownliste die Priorität Niedrig aus, wenn diese Abfrage bei eventuellen Deadlockkonflikten verlieren und als die zu beendende Abfrage ausgewählt werden soll.  
  
 **SPERREN-TIMEOUT FESTLEGEN**  
 Der Standardwert -1 gibt an, dass Sperren bis zum Abschluss von Transaktionen aktiv bleiben. Der Wert 0 gibt an, dass nicht gewartet und eine Meldung zurückgegeben wird, sobald eine Sperre auftritt. Geben Sie einen Wert von mehr als 0 Millisekunden für die Beendigung einer Transaktion an, wenn die Transaktionssperren länger als diese Zeit aktiv bleiben sollen.  
  
 **SET QUERY_GOVERNOR_COST_LIMIT**  
 Mit der Option **Kostenbeschränkung der Abfragekontrolle** geben Sie ein Höchstlimit für die Zeit an, in der eine Abfrage ausgeführt werden kann. Die Abfragekosten beziehen sich auf eine geschätzte Zeit in Sekunden, die für das Ausführen einer Abfrage bei einer bestimmten Hardwarekonfiguration benötigt wird. Die Standardeinstellung von 0 gibt an, dass die Zeit für die Ausführung einer Abfrage nicht begrenzt ist.  
  
 **Anbieternachrichtenkopf unterdrücken**  
 Wenn dieses Kontrollkästchen aktiviert ist, werden keine Statusmeldungen vom Anbieter (z. B. dem OLE DB-Anbieter) angezeigt. Dieses Kontrollkästchen ist standardmäßig aktiviert. Deaktivieren Sie dieses Kontrollkästchen, wenn bei der Problembehandlung für Abfragen, bei denen auf Anbieterebene ein Fehler auftritt, Anbieternachrichten angezeigt werden sollen.  
  
 **Nach Ausführung die Abfrage trennen**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird die Verbindung mit SQL Server nach Ausführung der Abfrage getrennt. Diese Option ist standardmäßig deaktiviert.  
  
 **Standard wiederherstellen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
  
