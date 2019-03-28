---
title: Steuern der Transaktionsdauerhaftigkeit | Microsoft-Dokumentation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- delayed durability
- Lazy Commit
ms.assetid: 3ac93b28-cac7-483e-a8ab-ac44e1cc1c76
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a90d40b158acf786ccb5bcdf962c2d6077c59dd
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535182"
---
# <a name="control-transaction-durability"></a>Steuern der Transaktionsdauerhaftigkeit
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Transaktionscommits können entweder vollständig dauerhaft sein, was in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Standardeinstellung entspricht, oder sie können verzögert dauerhaft sein (auch bekannt als verzögerter Commit).  
  
 Vollständig dauerhafte Transaktionscommits sind synchron, melden, dass ein COMMIT erfolgreich ausgeführt wurde, und geben die Steuerung erst an den Client zurück, nachdem die Protokolldatensätze für die Transaktion auf den Datenträger geschrieben wurden. Verzögert dauerhafte Transaktionscommits sind asynchron und melden, dass ein COMMIT erfolgreich ausgeführt wurde, bevor die Protokolldatensätze für die Transaktion auf den Datenträger geschrieben wurden. Damit eine Transaktion dauerhaft ist, müssen die Transaktionsprotokolleinträge auf dem Datenträger festgeschrieben werden. Verzögert dauerhafte Transaktionen werden dauerhaft, nachdem die Transaktionsprotokolleinträge auf den Datenträger geleert wurden.  
  
 In diesem Thema werden verzögert dauerhafte Transaktionen ausführlich beschrieben.  
  
## <a name="full-vs-delayed-transaction-durability"></a>Vollständige oder  verzögerte Transaktionsdauerhaftigkeit  
 Sowohl die vollständige als auch die verzögerte Transaktionsdauerhaftigkeit bietet Vor- und Nachteile. Eine Anwendung kann eine Mischung aus vollständig dauerhaften und verzögert dauerhaften Transaktionen aufweisen. Sie sollten sorgfältig abwägen, welche der beiden Transaktionsarten besser für Ihre Geschäftsanforderungen geeignet ist.  
  
### <a name="full-transaction-durability"></a>Vollständige Transaktionsdauerhaftigkeit  
 Bei vollständig dauerhaften Transaktionen wird das Transaktionsprotokoll auf dem Datenträger festgeschrieben, bevor die Steuerung an den Client zurückgegeben wird. Vollständig dauerhafte Transaktionen sollten in folgenden Fällen verwendet werden:  
  
-   Das System toleriert keine Datenverluste.   
    Informationen zu möglichen Datenverlusten finden Sie im Abschnitt [Wann können Daten verloren gehen?](#when-can-i-lose-data) .  
  
-   Der Engpass ist nicht auf Latenzen beim Schreiben des Transaktionsprotokolls zurückzuführen.  
  
 Bei verzögerter Transaktionsdauerhaftigkeit verringert sich die Latenz aufgrund der E/A-Protokollvorgänge, weil die Transaktionsprotokoll-Datensätze im Arbeitsspeicher vorgehalten und batchweise in das Transaktionsprotokoll geschrieben werden und infolgedessen weniger E/A-Vorgänge erfordern. Verzögerte Transaktionsdauerhaftigkeit kann Konflikte bei Protokoll-E/A-Vorgängen verringern und so Wartezeiten im System reduzieren.  
  
 **Zusicherungen bei vollständiger Transaktionsdauerhaftigkeit**  
  
-   Sobald ein Transaktionscommit erfolgreich war, sind die durch die Transaktion ausgeführten Änderungen für die anderen Transaktionen im System sichtbar. Finden Sie im Thema [Isolationsstufen von Transaktionen](../../database-engine/transaction-isolation-levels.md) für Weitere Informationen.  
  
-   Die Dauerhaftigkeit ist beim Commit gewährleistet. Die entsprechenden Protokolldatensätze werden dauerhaft auf dem Datenträger gespeichert, bevor das Transaktionscommit erfolgreich ausgeführt und die Steuerung an den Client zurückgegeben wird.  
  
### <a name="delayed-transaction-durability"></a>Verzögerte Transaktionsdauerhaftigkeit  
 Die verzögerte Transaktionsdauerhaftigkeit wird durch das asynchrone Schreiben von Protokolleinträgen auf den Datenträger erreicht. Transaktionsprotokoll-Datensätze werden in einem Puffer vorgehalten und auf dem Datenträger festgeschrieben, sobald sich der Puffer füllt oder das Leeren des Puffers durch ein Ereignis ausgelöst wird. Die verzögerte Transaktionsdauerhaftigkeit reduziert sowohl Latenzen als auch Konflikte innerhalb des Systems aus folgenden Gründen:  
  
-   Die Transaktionscommitverarbeitung wartet nicht, bis E/A-Protokollvorgänge abgeschlossen sind und die Steuerung an den Client zurückgegeben wurde.  
  
-   Bei gleichzeitigen Transaktionen sinkt die Konfliktwahrscheinlichkeit bei E/A-Protokollvorgängen. Stattdessen kann der Protokollpuffer in größeren Blöcken auf den Datenträger geleert werden, wodurch Konflikte verringert und der Durchsatz erhöht werden.  
  
    > [!NOTE]  
    >  Bei einem hohen Grad an Parallelität können weiterhin Konflikte bei E/A-Protokollvorgängen auftreten, insbesondere, wenn der Protokollpuffer schneller gefüllt als geleert wird.  
  
 **Verwenden Sie die verzögerte transaktionsdauerhaftigkeit**  
  
 In folgenden Situationen ist die verzögerte Transaktionsdauerhaftigkeit u. U. von Vorteil:  
  
 **Sie können es sich um gewisser Datenverlust tolerieren.**  
 Sofern Datenverluste vertretbar sind, also einzelne Datensätze z. B. nicht ins Gewicht fallen, solange der Großteil der Daten erhalten bleibt, könnten verzögert dauerhafte Transaktionen für Sie in Betracht kommen. Falls kein Datenverlust hinnehmbar ist, sollten Sie auf die verzögerte Transaktionsdauerhaftigkeit verzichten.  
  
 **Sie treten Engpässe auf Schreibzugriffen auf Transaktionsprotokolle.**  
 Wenn die Leistungsprobleme auf Latenzen beim Schreiben in das Transaktionsprotokoll zurückzuführen sind, wird Ihre Anwendung u. U. von der Verwendung verzögerter Transaktionsdauerhaftigkeit profitieren.  
  
 **Arbeitsauslastungen weisen eine hohe Konfliktrate auf.**  
 Wenn Ihr System Arbeitsauslastungen mit einer hohen Konfliktrate aufweist, wird viel Zeit mit dem Warten auf die Freigabe von Sperren vergeudet. Da die Commitzeit durch die verzögerte Transaktionsdauerhaftigkeit verkürzt wird, können Sperren schneller freigegeben und der Durchsatz erhöht werden.  
  
 **Zusicherungen bei verzögerter Transaktionsdauerhaftigkeit**  
  
-   Sobald ein Transaktionscommit erfolgreich war, sind die durch die Transaktion ausgeführten Änderungen für die anderen Transaktionen im System sichtbar.  
  
-   Die Transaktionsdauerhaftigkeit ist erst gewährleistet, nachdem das In-Memory-Transaktionsprotokoll auf den Datenträger geleert wurde. Das In-Memory-Transaktionsprotokoll wird in folgenden Fällen auf den Datenträger geleert:  
  
    -   Durch eine vollständig dauerhafte Transaktion in derselben Datenbank werden eine Änderung in der Datenbank vorgenommen und erfolgreich ein Commit ausgeführt.  
  
    -   Der Benutzer führt erfolgreich die gespeicherte Systemprozedur `sp_flush_log` aus.  
  
    -   Der In-Memory-Transaktionsprotokollpuffer wird aufgefüllt und automatisch auf den Datenträger geleert.  
  
     Nachdem für eine vollständig dauerhafte Transaktion oder sp_flush_log erfolgreich ein Commit ausgeführt wurde, werden alle verzögert dauerhaften Transaktionen, für die zuvor ein Commit ausgeführt wurde, zu dauerhaften Transaktionen.  
  
 Das Protokoll kann regelmäßig auf den Datenträger geleert werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt jedoch keine Garantie der Dauerhaftigkeit außer bei dauerhaften Transaktionen und sp_flush_log.  
  
## <a name="how-to-control-transaction-durability"></a>Steuern der Transaktionsdauerhaftigkeit  
  
### <a name="database-level-control"></a>Steuerung auf Datenbankebene  
 Der Datenbankadministrator kann mithilfe der folgenden Anweisung steuern, ob Benutzer die verzögerte Transaktionsdauerhaftigkeit in einer Datenbank nutzen können. Sie müssen die Einstellung für verzögerte Dauerhaftigkeit mit ALTER DATABASE festlegen.  
  
```sql  
ALTER DATABASE ... SET DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
```  
  
 `DISABLED`  
 [Standard] Mit dieser Einstellung sind alle Transaktionen, für die in der Datenbank ein Commit ausgeführt wurde, unabhängig von der Einstellung der Commitebene (DELAYED_DURABILITY=[ON | OFF]) vollständig dauerhaft. Gespeicherte Prozeduren müssen weder geändert noch neu kompiliert werden. Auf diese Weise können Sie verhindern, dass Daten aufgrund verzögerter Dauerhaftigkeit gefährdet werden.  
  
 `ALLOWED`  
 Mit dieser Einstellung wird die Dauerhaftigkeit jeder Transaktion auf der Transaktionsebene bestimmt: DELAYED_DURABILITY = { *OFF* | ON }. Finden Sie unter [Ebene Steuerung von Atomic-Blockebene – systemintern kompilierte gespeicherte Prozeduren](#atomic-block-level-control---natively-compiled-stored-procedures) und [COMMIT-Steuerung auf Datenbankebene - Transact-SQL](#commit-level-control---t-sql) für Weitere Informationen.  
  
 `FORCED`  
 Mit dieser Einstellung wird jede Transaktion, für die in der Datenbank ein Commit ausgeführt wird, zu einer verzögert dauerhaften Transaktion. Unabhängig davon, ob für die Transaktion vollständige Dauerhaftigkeit (DELAYED_DURABILITY = OFF) oder keine Einstellung angegeben wird, wird sie zu einer verzögert dauerhaften Transaktion. Diese Einstellung ist hilfreich, wenn die verzögerte Transaktionsdauerhaftigkeit für eine Datenbank von Nutzen ist und Sie keinen Anwendungscode ändern möchten.  
  
### <a name="atomic-block-level-control---natively-compiled-stored-procedures"></a>Ebene Steuerung von Atomic-Blockebene – systemintern kompilierte gespeicherte Prozeduren  
 Folgender Code wird in den Atomic-Block eingefügt.  
  
```sql  
DELAYED_DURABILITY = { OFF | ON }  
```  
  
 `OFF`  
 [Standard] Die Transaktion ist vollständig dauerhaft, es sei denn, die Datenbankoption DELAYED_DURABLITY = FORCED ist aktiviert, wodurch das COMMIT asynchron und daher verzögert dauerhaft ist. Weitere Informationen finden Sie unter [Database level control](#database-level-control) .  
  
 `ON`  
 Die Transaktion ist verzögert dauerhaft, es sei denn, die Datenbankoption DELAYED_DURABLITY = DISABLED ist aktiviert, wodurch das COMMIT synchron und daher vollständig dauerhaft ist.  Weitere Informationen finden Sie unter [Database level control](#database-level-control) .  
  
 **Beispielcode:**  
  
```sql  
CREATE PROCEDURE <procedureName> ...  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    DELAYED_DURABILITY = ON,  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'English'  
    ...  
)  
END  
```  
  
### <a name="table-1-durability-in-atomic-blocks"></a>Tabelle 1: Dauerhaftigkeit in Atomic-Blöcken  
  
|Dauerhaftigkeitsoption für Atomic-Block|Keine Transaktion vorhanden|Transaktion wird ausgeführt (vollständig oder verzögert dauerhaft)|  
|------------------------------------|-----------------------------|---------------------------------------------------------|  
|`DELAYED_DURABILITY = OFF`|Atomic-Block startet eine neue vollständig dauerhafte Transaktion.|Atomic-Block erstellt einen Sicherungspunkt in der vorhandenen Transaktion und startet dann die neue Transaktion.|  
|`DELAYED_DURABILITY = ON`|Atomic-Block startet eine neue verzögert dauerhafte Transaktion.|Atomic-Block erstellt einen Sicherungspunkt in der vorhandenen Transaktion und startet dann die neue Transaktion.|  
  
### <a name="commit-level-control---t-sql"></a>Übernehmen der Steuerung auf Datenbankebene - (T-SQL)
 Da die COMMIT-Syntax erweitert ist, kann die verzögerte Transaktionsdauerhaftigkeit erzwungen werden. Wenn für DELAYED_DURABILITY auf Datenbankebene DISABLED oder FORCED festgelegt wird (siehe oben), wird diese COMMIT-Option ignoriert.  
  
```sql  
COMMIT [ { TRAN | TRANSACTION } ] [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]  
  
```  
  
 `OFF`  
 [Standard] Das COMMIT der Transaktion ist vollständig dauerhaft, es sei denn, die Datenbankoption DELAYED_DURABLITY = FORCED ist aktiviert, wodurch das COMMIT asynchron und daher verzögert dauerhaft ist. Weitere Informationen finden Sie unter [Database level control](#database-level-control) .  
  
 `ON`  
 Das COMMIT der Transaktion ist verzögert dauerhaft, es sei denn, die Datenbankoption DELAYED_DURABLITY = DISABLED ist aktiviert, wodurch das COMMIT synchron und daher vollständig dauerhaft ist. Weitere Informationen finden Sie unter [Database level control](#database-level-control) .  
  
### <a name="summary-of-options-and-their-interactions"></a>Zusammenfassung der Optionen und jeweiligen Interaktionen  
 In der folgenden Tabelle wird erläutert, auf welche Weise Einstellungen für verzögerte Dauerhaftigkeit auf Datenbankebene und Commitebene interagieren. Einstellungen auf Datenbankebene haben immer Vorrang vor Einstellungen auf Commitebene.  
  
|COMMIT-Einstellung/Datenbankeinstellung|DELAYED_DURABILITY = DISABLED|DELAYED_DURABILITY = ALLOWED|DELAYED_DURABILITY = FORCED|  
|--------------------------------------|-------------------------------------|------------------------------------|-----------------------------------|  
|`DELAYED_DURABILITY = OFF` Transaktionen auf Datenbankebene.|Transaktion ist vollständig dauerhaft.|Transaktion ist vollständig dauerhaft.|Transaktion ist verzögert dauerhaft.|  
|`DELAYED_DURABILITY = ON` Transaktionen auf Datenbankebene.|Transaktion ist vollständig dauerhaft.|Transaktion ist verzögert dauerhaft.|Transaktion ist verzögert dauerhaft.|  
|`DELAYED_DURABILITY = OFF` Datenbankübergreifende oder verteilte Transaktion.|Transaktion ist vollständig dauerhaft.|Transaktion ist vollständig dauerhaft.|Transaktion ist vollständig dauerhaft.|  
|`DELAYED_DURABILITY = ON` Datenbankübergreifende oder verteilte Transaktion.|Transaktion ist vollständig dauerhaft.|Transaktion ist vollständig dauerhaft.|Transaktion ist vollständig dauerhaft.|  
  
## <a name="how-to-force-a-transaction-log-flush"></a>Erzwungenes Leeren des Transaktionsprotokolls  
 Sie können auf zwei Weisen erzwingen, dass das Transaktionsprotokoll auf den Datenträger geleert wird.  
  
-   Durch Ausführen einer beliebigen vollständig dauerhaften Transaktion, die dieselbe Datenbank ändert. Dadurch wird erzwungen, dass die Protokolldatensätze aller vorherigen verzögert dauerhaften Transaktionen, für die ein Commit ausgeführt wurde, auf den Datenträger geleert werden.  
  
-   Durch Ausführen der gespeicherten Systemprozedur `sp_flush_log`. Durch diese Prozedur wird erzwungen, dass die Protokolldatensätze aller vorherigen verzögert dauerhaften Transaktionen, für die ein Commit ausgeführt wurde, auf den Datenträger geleert werden. Weitere Informationen finden Sie unter [sys.sp_flush_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql).  
  
##  <a name="delayed-durability-and-other-sql-server-features"></a>Verzögerte Dauerhaftigkeit und andere SQL Server-Funktionen  
 **Änderungsnachverfolgung und Change Data Capture**  
 Alle Transaktionen mit Änderungsnachverfolgung sind vollständig dauerhaft. Eine Transaktion verfügt über die Eigenschaft für das Nachverfolgen von Änderungen, wenn sie Schreibvorgänge in Tabellen ausführt, für die die Änderungsnachverfolgung aktiviert ist. Die Verwendung der verzögerten Dauerhaftigkeit wird für Datenbanken, die Change Data Capture (CDC) verwenden, nicht unterstützt.   
  
 **Wiederherstellung nach einem Systemabsturz**  
 Zwar ist Konsistenz gewährleistet, allerdings können einige Änderungen durch verzögert dauerhafte Transaktionen, für die ein Commit ausgeführt wurde, verloren gehen.  
  
 **Datenbankübergreifende Transaktionen und DTC**  
 Ist eine Transaktion datenbankübergreifend oder verteilt, ist sie unabhängig von einer Datenbank- oder Transaktionscommiteinstellung vollständig dauerhaft.  
  
 **Always On-Verfügbarkeitsgruppen und Spiegelung**  
 Verzögert dauerhafte Transaktionen gewährleisten weder auf dem primären noch auf den sekundären Replikaten Dauerhaftigkeit. Darüber hinaus sind keine zuverlässigen Informationen zur Transaktion auf dem sekundären Replikat verfügbar. Nach dem COMMIT wird die Steuerung an den Client zurückgegeben, bevor eine Bestätigung von einem synchronen sekundären Replikat empfangen wird.  
  
 **Failover-Clusterunterstützung**  
 Einige Schreibvorgänge verzögert dauerhafter Transaktionen können verloren gehen.  
  
 **Transaktionsreplikation**  
 Verzögerte dauerhafte Transaktionen werden bei der Transaktionsreplikation nicht unterstützt.  
  
 **Protokollversand**  
 In das gesendete Protokoll werden nur Transaktionen aufgenommen, die in dauerhafte Transaktionen konvertiert wurden.  
  
 **Protokollsicherung**  
 In die Sicherung werden nur Transaktionen aufgenommen, die in dauerhafte Transaktionen konvertiert wurden.  
  
## <a name="when-can-i-lose-data"></a>Wann können Daten verloren gehen?  
 Wenn Sie verzögerte Dauerhaftigkeit in einer der Tabellen implementieren, sollten Sie beachten, dass es unter bestimmten Umständen zu Datenverlust kommen kann. Falls kein Datenverlust hinnehmbar ist, sollten Sie auf die verzögerte Dauerhaftigkeit in Tabellen verzichten.  
  
### <a name="catastrophic-events"></a>Notfälle  
 Bei Notfällen wie beispielsweise einem Serverabsturz gehen die Daten für alle Transaktionen, für die ein Commit ausgeführt wurde, aber die noch nicht auf dem Datenträger gespeichert wurden, verloren. Verzögert dauerhafte Transaktionen werden auf dem Datenträger gespeichert, sobald eine vollständig dauerhafte Transaktion für eine Tabelle in der Datenbank ausgeführt wird (dauerhaft speicheroptimiert oder datenträgerbasiert), oder wenn `sp_flush_log` aufgerufen wird. Bei Verwendung von verzögert dauerhaften Transaktionen sollten Sie eine kleine Tabelle in der Datenbank erstellen, die Sie regelmäßig aktualisieren, oder Sie rufen regelmäßig `sp_flush_log` auf, um alle ausstehenden Transaktionen, für die ein Commit ausgeführt wurde, zu speichern. Das Transaktionsprotokoll wird ebenfalls geleert, sobald es voll ist, aber dies ist schwer vorherzusagen und kaum zu steuern.  
  
### <a name="sql-server-shutdown-and-restart"></a>SQL Server herunterfahren und Neustart  
 Für die verzögerte Dauerhaftigkeit macht es keinen Unterschied, ob das Herunterfahren unerwartet erfolgt oder das Herunterfahren/Neustarten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geplant ist. Wie bei Notfällen sollten Sie mit Datenverlusten rechnen. Beim geplanten Herunterfahren/Neustarten werden möglicherweise einige Transaktionen, die noch nicht auf dem Datenträger festgeschrieben wurden, zuerst auf dem Datenträger gespeichert, aber dies lässt sich nicht planen. Planen Sie so, als ob beim Herunterfahren/Neustarten (ob geplant oder ungeplant) die Daten genauso wie bei unvorhersehbaren Notfällen verloren gehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Isolationsstufen von Transaktionen](../../database-engine/transaction-isolation-levels.md)   
 [Richtlinien für Transaktionsisolationsstufen mit speicheroptimierten Tabellen](../in-memory-oltp/memory-optimized-tables.md)  
  
  
