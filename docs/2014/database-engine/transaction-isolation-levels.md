---
title: Transaktionsisolationsstufen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8a6a82bf-273c-40ab-a101-46bd3615db8a
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abdac8463a5f6ce54c0ed8bf2de71b477865fb50
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392313"
---
# <a name="transaction-isolation-levels"></a>Transaktionsisolationsstufen
  Die folgenden Isolationsstufen werden für Transaktionen unterstützt, die auf Speicheroptimierte Tabellen zugreifen.  
  
-   SNAPSHOT  
  
-   REPEATABLE READ  
  
-   SERIALIZABLE  
  
-   READ COMMITTED  
  
 Die Transaktionsisolationsstufe kann als Teil des Atomic-Blocks einer systemintern kompilierten gespeicherten Prozedur angegeben werden. Weitere Informationen finden Sie unter [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql). Beim Zugriff auf speicheroptimierte Tabellen von interpretiertem [!INCLUDE[tsql](../includes/tsql-md.md)] aus kann die Isolationsstufe mithilfe von Hinweisen auf Tabellenebene angegeben werden.  
  
 Sie müssen die Transaktionsisolationsstufe angeben, wenn Sie eine systemintern kompilierte gespeicherte Prozedur definieren. Die Angabe der Isolationsstufe in Tabellenhinweisen ist beim Zugriff auf speicheroptimierte Tabellen über Benutzertransaktionen in interpretiertem [!INCLUDE[tsql](../includes/tsql-md.md)] erforderlich. Weitere Informationen finden Sie unter [Richtlinien für Transaktionsisolationsstufen mit speicheroptimierten Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Die Isolationsstufe READ COMMITTED wird für speicheroptimierte Tabellen mit Autocommittransaktionen unterstützt. READ COMMITTED ist in Benutzertransaktionen oder in einem atomaren Block nicht zulässig. READ COMMITTED wird mit expliziten oder impliziten Benutzertransaktionen nicht unterstützt. Die READ_COMMITTED_SNAPSHOT-Isolationsstufe wird für speicheroptimierte Tabellen mit Autocommittransaktionen und nur dann unterstützt, wenn die Abfrage nicht auf datenträgerbasierte Tabellen zugreift. Zudem können Transaktionen, die mit interpretiertem [!INCLUDE[tsql](../includes/tsql-md.md)] mit SNAPSHOT-Isolation gestartet werden, nicht auf speicheroptimierte Tabellen zugreifen. Transaktionen, die interpretiertes [!INCLUDE[tsql](../includes/tsql-md.md)] mit REPEATABLE READ- oder SERIALIZABLE-Isolation verwenden, müssen mit SNAPSHOT-Isolation auf speicheroptimierte Tabellen zugreifen. Weitere Informationen zu diesem Szenario finden Sie unter [containerübergreifende Transaktionen](cross-container-transactions.md).  
  
 READ COMMITTED ist die Standardisolationsstufe in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Wenn die Isolationsstufe der Sitzung READ COMMITED (oder niedriger) ist, können Sie eine der folgenden Maßnahmen ergreifen:  
  
-   Verwenden Sie zum Zugreifen auf die speicheroptimierte Tabelle explizit einen Hinweis für eine höhere Isolationsstufe (z. B. WITH (SNAPSHOT)).  
  
-   Geben Sie die SET-Option `MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT` an. Damit wird die Isolationsstufe für speicheroptimierte Tabellen auf SNAPSHOT festgelegt (wie bei der Einbindung von WITH(SNAPSHOT)-Hinweisen für alle speicheroptimierten Tabellen). Weitere Informationen zu `MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT`, finden Sie unter [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
 Falls die Isolationsstufe der Sitzung READ COMMITTED ist, können Sie alternativ Autocommittransaktionen verwenden.  
  
 SNAPSHOT-Transaktionen, die in interpretiertem [!INCLUDE[tsql](../includes/tsql-md.md)] gestartet werden, können nicht auf speicheroptimierte Tabellen zugreifen.  
  
 Die Transaktionsisolationsstufen, die für speicheroptimierte Tabellen unterstützt werden, bieten dieselben logischen Garantien wie datenträgerbasierte Tabellen. Zum Bereitstellen von Isolationsstufengarantien wird ein anderer Mechanismus verwendet.  
  
 Für datenträgerbasierte Tabellen werden die meisten Isolationsstufengarantien durch Sperren implementiert, wodurch Blockierungskonflikte verhindert werden. Bei speicheroptimierten Tabellen werden die Garantien mithilfe eines Konflikterkennungsmechanismus erzwungen, der die Anwendung von Sperren verhindert. Die Ausnahme besteht in der SNAPSHOT-Isolation bei datenträgerbasierten Tabellen. Die entsprechende Implementierung ähnelt der SNAPSHOT-Isolation bei speicheroptimierten Tabellen mit einem Konflikterkennungsmechanismus.  
  
 SNAPSHOT  
 Diese Isolationsstufe gibt an, dass die von einer beliebigen Anweisung in einer Transaktion gelesenen Daten der im Hinblick auf Transaktionen konsistenten Version der Daten entsprechen, die zu Beginn der Transaktion vorhanden waren. Die Transaktion kann nur Datenänderungen erkennen, für die vor dem Beginn der Transaktion ein Commit ausgeführt wurde. Datenänderungen, die nach Beginn der aktuellen Transaktion von anderen Transaktionen vorgenommen wurden, sind für in der aktuellen Transaktion ausgeführte Anweisungen nicht sichtbar. Die Anweisungen in einer Transaktion erhalten eine Momentaufnahme der Daten, für die ein Commit ausgeführt wurde, wie sie zu Beginn der Transaktion vorhanden waren.  
  
 Schreibvorgänge (Updates, Einfügungen und Löschungen) sind immer vollständig von anderen Transaktionen isoliert. Daher können die Schreibvorgänge einer SNAPSHOT-Transaktion mit den Schreibvorgängen anderer Transaktionen in Konflikt geraten. Wenn die aktuelle Transaktion versucht, eine Zeile zu aktualisieren oder zu löschen, die durch eine andere Transaktion aktualisiert oder gelöscht wurde, für die ein Commit ausgeführt wurde, nachdem die aktuelle Transaktion gestartet wurde, wird die Transaktion mit der folgenden Fehlermeldung beendet.  
  
 Fehler 41302. Für die aktuelle Transaktion wurde versucht, einen Datensatz in der Tabelle X zu aktualisieren, der aktualisiert wurde, nachdem diese Transaktion gestartet wurde. Die Transaktion wurde abgebrochen.  
  
 Wenn die aktuelle Transaktion versucht, eine Zeile mit dem gleichen Primärschlüsselwert wie eine Zeile einzufügen, die durch eine andere Transaktion eingefügt wurde, für die vor der aktuellen Transaktion ein Commit ausgeführt wurde, kommt es zu einem Commitfehler mit der folgenden Fehlermeldung.  
  
 Fehler 41325 fehl. Für die aktuelle Transaktion wurde aufgrund eines serialisierbaren Überprüfungsfehlers kein Commit ausgeführt.  
  
 Wenn eine Transaktion in eine Tabelle schreibt, die gelöscht wird, bevor für die Transaktion ein Commit ausgeführt wird, wird die Transaktion mit folgender Fehlermeldung beendet:  
  
 Fehler 41305 fehl. Fehler beim Ausführen eines Commits für die aktuelle Transaktion aufgrund eines REPEATABLE READ-Überprüfungsfehlers.  
  
 REPEATABLE READ  
 Diese Isolationsstufe enthält die Garantien, die von der SNAPSHOT-Isolationsstufe gegeben wurden. Darüber hinaus garantiert REPEATABLE READ, dass Zeilen, die von der Transaktion zum Zeitpunkt der Ausführung des Commits durch die Transaktion gelesen werden, nicht von einer anderen Transaktion geändert wurden. Jeder Lesevorgang der Transaktion kann bis zum Ende der Transaktion wiederholt werden.  
  
 Wenn die aktuelle Transaktion eine Zeile gelesen hat, die durch eine andere Transaktion aktualisiert wurde, für die vor der aktuellen Transaktion ein Commit ausgeführt wurde, schlägt der Commit mit der folgenden Fehlermeldung fehl.  
  
 Fehler 41305 fehl. Fehler beim Ausführen eines Commits für die aktuelle Transaktion aufgrund eines REPEATABLE READ-Überprüfungsfehlers.  
  
 SERIALIZABLE  
 Diese Isolationsstufe umfasst die durch REPEATABLE READ gewährten Garantien. Zwischen der Momentaufnahme und dem Ende der Transaktion sind keine Phantomzeilen aufgetreten. Phantomzeilen entsprechen der Filterbedingung einer Auswahl, eines Updates oder einer Löschung.  
  
 Die Transaktion wurde ausgeführt, als seien keine gleichzeitigen Transaktionen vorhanden. Alle Aktionen erfolgen praktisch an einem einzelnen serialisierungspunkt (Commitzeit).  
  
 Wenn eine dieser Garantien verletzt wird, kann für die Transaktion kein Commit ausgeführt werden, und es wird die folgende Fehlermeldung angezeigt:  
  
 Fehler 41325 fehl. Für die aktuelle Transaktion wurde aufgrund eines serialisierbaren Überprüfungsfehlers kein Commit ausgeführt.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu Transaktionen in speicheroptimierten Tabellen](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [Richtlinien für Transaktionsisolationsstufen mit speicheroptimierten Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md)   
 [Richtlinien zur Wiederholungslogik für Transaktionen auf speicheroptimierten Tabellen](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  
