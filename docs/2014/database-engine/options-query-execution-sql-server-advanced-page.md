---
title: 'Optionen (Abfrageausführung: SQL Server Abfragen: Seite "Erweitert") | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAdvanced
ms.assetid: 3ec788c7-22c3-4216-9ad0-81a168d17074
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 5323054b77ed26a3ada816f44c1bf6764ded931d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66089373"
---
# <a name="options-query-executionsql-serveradvanced-page"></a>Optionen (Abfrageausführung > SQL Server > Seite „Erweitert“)
  Bei Verwendung des SET-Befehls stehen mehrere Optionen zur Verfügung. Geben Sie mithilfe dieser Seite eine **set** -Option zur Ausführung von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Abfragen im Abfrage-Editor von SQL Server an. Auswirkungen auf andere Code-Editoren bestehen nicht. Die an diesen Optionen vorgenommenen Änderungen werden nur auf neue [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Abfragen angewendet. Um die Optionen für die aktuellen Abfragen zu ändern, klicken Sie im Menü **Abfrage** oder im Kontextmenü des Abfragefensters von **auf** Abfrageoptionen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Klicken Sie unter **Ausführung**auf **Erweitert**. Weitere Informationen hierzu finden Sie in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="options"></a>Optionen  
 **SET NOCOUNT**  
 Es wird nicht die Anzahl der Zeilen als Meldung mit dem Resultset zurückgegeben. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SET NOEXEC**  
 Die Abfrage wird nicht ausgeführt. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SET PARSEONLY**  
 Prüft die Syntax der einzelnen Abfragen, führt die Abfragen aber nicht aus. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SET CONCAT_NULL_YIELDS_NULL**  
 Wenn dieses Kontrollkästchen aktiviert ist, geben Abfragen, von denen ein vorhandener Wert mit einer NULL verkettet wird, als Ergebnis immer eine NULL zurück. Wenn dieses Kontrollkästchen deaktiviert ist, gibt ein vorhandener, mit einer NULL verketteter Wert, den vorhandenen Wert zurück. Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
 **SET ARITHABORT**  
 Wenn dieses Kontrollkästchen aktiviert ist und eine INSERT-, DELETE- oder UPDATE-Anweisung bei der Auswertung des Ausdrucks einen arithmetischer Fehler (Überlauf, Division durch null oder Domänenfehler) findet, wird die Abfrage bzw. der Batch beendet. Wenn dieses Kontrollkästchen deaktiviert ist, wird für diesen Wert nach Möglichkeit eine NULL bereitgestellt, die Abfrage fortgesetzt und in das Ergebnis eine Meldung eingeschlossen. Weitere Informationen finden Sie unter [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql). Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
 **SET SHOWPLAN_TEXT**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird bei jeder Abfrage der Abfrageplan im Textformat zurückgegeben. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SET STATISTICS TIME**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird bei jeder Abfrage die Zeitstatistik zurückgegeben. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SET STATISTICS IO**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird bei jeder Abfrage die Statistik zur Eingabe und Ausgabe zurückgegeben. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SET TRANSACTION ISOLATION LEVEL**  
 Die Transaktionsisolationsstufe READ COMMITTED wird standardmäßig festgelegt. Weitere Informationen finden Sie unter [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql). Die MOMENTAUFNAHME-Transaktionsisolationsstufe ist nicht verfügbar. Fügen Sie zum Verwenden der MOMENTAUFNAHME-Isolation die folgende [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisung hinzu:  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 **SET DEADLOCK PRIORITY**  
 Beim Standardwert Normal kann jede Abfrage bei Auftreten eines Deadlock dieselbe Priorität haben. Wählen Sie die Priorität Niedrig aus, wenn diese Abfrage bei eventuellen Deadlockkonflikten verlieren und als die zu beendende Abfrage ausgewählt werden soll.  
  
 **SPERREN-TIMEOUT FESTLEGEN**  
 Der Standardwert -1 gibt an, dass Sperren bis zum Abschluss von Transaktionen aktiv bleiben. Der Wert 0 gibt an, dass nicht gewartet und eine Meldung zurückgegeben wird, sobald eine Sperre auftritt. Geben Sie einen Wert von mehr als 0 Millisekunden für die Beendigung einer Transaktion an, wenn die Transaktionssperren länger als diese Zeit aktiv bleiben sollen.  
  
 **SET QUERY_GOVERNOR_COST_LIMIT**  
 Mithilfe der Option **QUERY_GOVERNOR_COST_LIMIT** können Sie eine obere Grenze für den Zeitraum angeben, in dem eine Abfrage ausgeführt werden kann. Die Abfragekosten beziehen sich auf eine geschätzte Zeit in Sekunden, die für das Ausführen einer Abfrage bei einer bestimmten Hardwarekonfiguration benötigt wird. Die Standardeinstellung von 0 gibt an, dass die Zeit für die Ausführung einer Abfrage nicht begrenzt ist.  
  
 **Anbieternachrichtenkopf unterdrücken**  
 Wenn dieses Kontrollkästchen aktiviert ist, werden keine Statusmeldungen vom Anbieter (z. B. dem SQLClient-Anbieter) angezeigt. Dieses Kontrollkästchen ist standardmäßig aktiviert. Deaktivieren Sie dieses Kontrollkästchen, wenn bei der Problembehandlung für Abfragen, bei denen auf Anbieterebene ein Fehler auftritt, Anbieternachrichten angezeigt werden sollen.  
  
 **Trennen Sie nach Ausführung der Abfrage**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird die Verbindung zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nach Ausführung der Abfrage getrennt. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **Standard wiederherstellen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
  
