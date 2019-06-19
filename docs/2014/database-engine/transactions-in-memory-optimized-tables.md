---
title: Transaktionen in speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2cd07d26-a1f1-4034-8d6f-f196eed1b763
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bc72eeeb154749b0e889b495fab79bb8bf86db10
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62843100"
---
# <a name="transactions-in-memory-optimized-tables"></a>Transaktionen in speicheroptimierten Tabellen
  Die Zeilenversionsverwaltung für datenträgerbasierte Tabellen (mit SNAPSHOT-Isolation oder READ_COMMITTED_SNAPSHOT) bietet eine Form der optimistischen Nebenläufigkeitssteuerung. Lese- und Schreibvorgänge blockieren sich nicht. Bei speicheroptimierten Tabellen blockieren sich Schreibvorgänge nicht gegenseitig. Bei der Zeilenversionsverwaltung für datenträgerbasierte Tabellen wird die Zeile durch eine Transaktion gesperrt, während gleichzeitige Transaktionen, die die Zeile zu aktualisieren versuchen, blockiert werden. Bei speicheroptimierten Tabellen werden keine Sperren festgelegt. Stattdessen führt der Versuch von zwei Transaktionen, dieselbe Zeile zu aktualisieren, zu einem Schreibkonflikt (Fehler 41302).  
  
 Im Gegensatz zu datenträgerbasierten Tabellen ermöglichen speicheroptimierte Tabellen die optimistische Nebenläufigkeitssteuerung mit den höheren Isolationsstufen REPEATABLE READ und SERIALIZABLE. Isolationsstufen werden nicht mit Sperren erzwungen. Stattdessen werden bei Transaktionsende mit einer Überprüfung die REPEATABLE READ- oder SERIALIZABLE-Annahmen sichergestellt. Wenn ein Verstoß gegen die Annahmen ermittelt wird, wird die Transaktion beendet. Weitere Informationen finden Sie unter [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).  
  
 Die relevanten Transaktionssemantiken für speicheroptimierte Tabellen lauten:  
  
-   Multiversionsverwaltung  
  
-   Transaktionsisolation auf Basis einer Momentaufnahme  
  
-   Optimistisch  
  
-   Konflikterkennung  
  
 Diese Semantiken werden in den folgenden Abschnitten im einzelnen erklärt.  
  
## <a name="multi-versioning-in-memory-optimized-tables"></a>Multiversionsverwaltung in speicheroptimierten Tabellen  
 Zeilen in speicheroptimierten Tabellen können verschiedene Versionen enthalten. Gleichzeitige Transaktionen greifen auf unterschiedliche Versionen derselben Zeile zu.  
  
 Speicheroptimierte Tabellendaten sind versionsbasiert. Für jede Zeile kann es unterschiedliche Versionen geben, die zu unterschiedlichen Zeitpunkten gültig sind. Wenn READ_COMMITTED_SNAPSHOT oder ALLOW_SNAPSHOT_ISOLATION auf ON festgelegt ist, werden in datenträgerbasierten Tabellen unterschiedliche Zeilenversionen verwaltet. Speicheroptimierte Tabellen verwalten selbst dann unterschiedliche Zeilenversionen, wenn READ_COMMITTED_SNAPSHOT und ALLOW_SNAPSHOT_ISOLATION auf OFF festgelegt sind. Die Zeilenversionen aus speicheroptimierten Tabellen werden nicht in tempdb verwaltet. Stattdessen werden die Zeilenversionen inline als Teil der speicheroptimierten Datenstrukturen verwaltet, in denen die Zeilen im Arbeitsspeicher gespeichert werden.  
  
## <a name="snapshot-based-transaction-isolation-for-memory-optimized-tables"></a>Transaktionsisolation auf Basis einer Momentaufnahme für speicheroptimierte Tabellen  
 Alle Vorgänge in einer einzelnen Transaktion verwenden dieselbe im Hinblick auf Transaktionen konsistente Momentaufnahme der speicheroptimierten Tabellen. Jegliche Transaktionsisolation für speicheroptimierte Tabellen beruht auf einer Momentaufnahme. Beispielsweise führt eine Transaktion, die die Serializable-Isolationsstufe für den Zugriff auf speicheroptimierte Tabellen nutzt, alle Vorgänge auf Grundlage ein und derselben, in der Transaktionen konsistenten Momentaufnahme durch.  
  
 Transaktionen, die auf speicheroptimierte Tabellen zugreifen, verwenden die Zeilenversionsverwaltung, um eine transaktionskonsistente Momentaufnahme der Zeilen in den Tabellen zu erhalten. Alle Anweisungen in einer Transaktion lesen eine transaktionskonsistente Version der Daten, wie sie zu Transaktionsbeginn vorlagen. Daher sind Änderungen durch gleichzeitig ausgeführte Transaktionen für Anweisungen in der aktuellen Transaktion nicht sichtbar.  
  
## <a name="optimistic-concurrency-control-for-memory-optimized-tables"></a>Optimistische Nebenläufigkeitssteuerung bei speicheroptimierten Tabellen  
 Konflikte und Fehler sind selten, und bei Transaktionen für speicheroptimierte Tabellen wird davon ausgegangen, dass keine Konflikte bei gleichzeitigen Transaktionen auftreten und die Ausführung erfolgreich ist. Transaktionen verwenden keine Sperren oder Latches für speicheroptimierte Tabellen, um Transaktionsisolation zu gewährleisten. Lesevorgänge werden nicht durch Schreibvorgänge blockiert. Schreibvorgänge blockieren sich nicht gegenseitig. Stattdessen werden die Transaktionen unter der (optimistischen) Annahme ausgeführt, dass keine Konflikte mit anderen Transaktionen bestehen. Da keine Sperren und Latches verwendet werden und nicht darauf gewartet wird, dass andere Transaktionen die Verarbeitung derselben Zeilen abschließen, verbessert sich die Leistung.  
  
 Wenn darüber hinaus von einer Transaktion (TxA) Zeilen gelesen werden, die von einer anderen Transaktion (TxB) eingefügt oder bearbeitet wurden und für die gerade ein Commit ausgeführt wird, wartet die Transaktion nicht auf den Commit, sondern geht optimistisch davon aus, dass die andere Transaktion einen Commit ausführen wird. In diesem Fall übernimmt Transaktion TxA eine Abhängigkeit vom Commit der Transaktion TxB.  
  
## <a name="conflict-detection-validation-and-commit-dependency-checks"></a>Konflikterkennung, Überprüfung und Commitabhängigkeitsüberprüfungen  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] erkennt Konflikte zwischen gleichzeitigen Transaktionen sowie Verletzungen der Isolationsstufe und verwirft eine der in Konflikt stehenden Transaktionen. Diese Transaktion muss erneut ausgeführt werden. (Weitere Informationen finden Sie unter [Richtlinien zur Wiederholungslogik für Transaktionen in speicheroptimierten Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md).)  
  
 Das System nimmt optimistisch an, dass keine Konflikte und keine Verstöße gegen die Transaktionsisolation vorliegen. Falls Konflikte auftreten, die Inkonsistenzen in der Datenbank verursachen oder die Transaktionsisolation verletzen könnten, werden diese Konflikte ermittelt und die Transaktion beendet.  
  
 Wenn ein Konflikt erkannt wird, wird die Transaktion beendet und muss vom Client wiederholt werden.  
  
 In der folgenden Tabelle werden Fehlerbedingungen für Transaktionen zusammengefasst, die auf speicheroptimierte Tabellen zugreifen.  
  
### <a name="error-conditions-for-transactions-accessing-memory-optimized-tables"></a>Fehlerbedingungen für Transaktionen, die auf speicheroptimierte Tabellen zugreifen.  
  
|Fehler|Szenario|  
|-----------|--------------|  
|Schreibkonflikt. Es wurde versucht, einen Datensatz zu aktualisieren, der seit Transaktionsbeginn geändert wurde.|Für eine Zeile, die durch eine gleichzeitige Transaktion aktualisiert oder gelöscht wurde, werden die Befehle UPDATE oder DELETE ausgegeben.|  
|REPEATABLE READ-Überprüfungsfehler.|Eine von der Transaktion gelesene Zeile wurde nach Transaktionsbeginn geändert (aktualisiert oder gelöscht). Die REPEATABLE READ-Überprüfung tritt in der Regel bei Verwendung der Transaktionsisolationsstufen REPEATABLE READ und SERIALIZABLE auf.|  
|SERIALIZABLE-Überprüfungsfehler.|Eine neue (Phantom-)Zeile wurde nach Transaktionsbeginn in einen der Scanbereiche der Transaktion eingefügt. Die Zeile wäre für die Transaktion sichtbar gewesen, wenn für diese vor Transaktionsbeginn in der Datenbank ein Commit ausgeführt worden wäre. Die SERIALIZABLE-Überprüfung tritt in der Regel bei Verwendung der SERIALIZABLE-Isolation und Überprüfung von PRIMARY KEY-Einschränkungen auf.|  
|Commitabhängigkeitsfehler.|Die Transaktion hat eine Abhängigkeit von einer anderen Transaktion übernommen, für die kein Commit ausgeführt werden konnte, entweder wegen eines Fehlers in dieser Tabelle, weil nicht genügend Arbeitsspeicher verfügbar war oder weil der Commit im Transaktionsprotokoll fehlgeschlagen ist. Ein derartiger Fehler kann bei Transaktionen mit Lese-/Schreibzugriff wie auch bei schreibgeschützten Transaktionen auftreten.|  
  
### <a name="transaction-lifetime"></a>Lebensdauer von Transaktionen  
 Die in der vorherigen Tabelle beschriebenen Fehler können zu unterschiedlichen Zeitpunkten während einer Transaktion auftreten. In der folgenden Abbildung werden die Phasen einer Transaktion dargestellt, die auf speicheroptimierte Tabellen zugreift.  
  
 ![Lebensdauer einer Transaktion. ](../../2014/database-engine/media/hekaton-transactions.gif "Lebensdauer einer Transaktion.")  
Lebensdauer einer Transaktion, die auf speicheroptimierte Tabellen zugreift.  
  
#### <a name="regular-processing"></a>Reguläre Verarbeitung  
 Während dieser Phase werden die durch den Benutzer ausgegebenen [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen ausgeführt. Zeilen werden aus den Tabellen gelesen, und neue Zeilenversionen werden in die Datenbank geschrieben. Die Transaktion wird von allen anderen gleichzeitigen Transaktionen isoliert. Die Transaktion verwendet die Momentaufnahme der speicheroptimierten Tabellen, die zu Transaktionsbeginn vorhanden ist.  
  
 Schreibvorgänge, die in dieser Phase der Transaktion in den Tabellen ausgeführt werden, sind für andere Transaktionen noch nicht sichtbar. Eine Ausnahme hiervon bilden Zeilenupdates und -löschungen, die für Update- und Löschvorgänge in anderen Transaktionen sichtbar sind, damit Schreibkonflikte erkannt werden können.  
  
 Wenn bei einem Update- oder Löschvorgang festgestellt wird, dass eine Zeile seit dem logischen Beginn der Transaktion aktualisiert oder gelöscht wurde, schlägt der Vorgang mit Fehler 41302 fehl. Die Fehlermeldung 41302 lautet: "Für die aktuelle Transaktion wurde versucht, einen Datensatz in der Tabelle X zu aktualisieren, der aktualisiert wurde, nachdem diese Transaktion gestartet wurde. Die Anweisung wurde abgebrochen."  
  
 Dieser Fehler führt zu einem Transaktionsabbruch (selbst wenn XACT_ABORT auf OFF festgelegt ist). Dies bedeutet, dass bei Beendigung der Benutzersitzung ein Rollback für die Transaktion ausgeführt wird. Für fehlgeschlagene Transaktionen kann kein Commit ausgeführt werden, und sie unterstützen nur Lesevorgänge, durch die nicht in das Protokoll geschrieben und auf speicheroptimierte Tabellen zugegriffen wird.  
  
#####  <a name="cd"></a> Commit-Abhängigkeiten  
 Während der regulären Verarbeitung kann eine Transaktion Zeilen von anderen Transaktionen lesen, die sich in der Überprüfungs- oder Commitphase befinden, deren Commit jedoch noch nicht abgeschlossen ist. Die Zeilen sind sichtbar, da der logische Endzeitpunkt der Transaktionen beim Start der Überprüfungsphase zugewiesen wurde.  
  
 Wenn Zeilen, für die kein Commit ausgeführt wurde, von einer Transaktion gelesen werden, übernimmt sie eine Commitabhängigkeit von dieser Transaktion. Dies hat zwei wesentliche Auswirkungen:  
  
-   Für eine Transaktion kann erst ein Commit ausgeführt werden, nachdem für die Transaktionen, von denen sie abhängt, ein Commit ausgeführt wurde. Dies bedeutet, das sie die Commitphase erst erreicht, wenn alle Abhängigkeiten aufgelöst sind.  
  
-   Außerdem werden keine Resultsets an den Client zurückgegeben, bis alle Abhängigkeiten aufgelöst sind. Dies stellt sicher, dass der Client keine Daten beachtet, für die noch kein Commit ausgeführt wurde.  
  
 Wenn für eine der abhängigen Transaktionen kein Commit ausgeführt wird, liegt ein Commitabhängigkeitsfehler vor. Dies bedeutet, dass für die Transaktion mit Fehler 41301 kein Commit ausgeführt werden kann. ("Eine vorherige Transaktion, von der die aktuelle Transaktion abhängig ist, wurde abgebrochen, sodass für die aktuelle Transaktion kein Commit mehr ausgeführt werden kann.")  
  
#### <a name="validation-phase"></a>Überprüfungsphase  
 Während der Überprüfungsphase überprüft das System, ob die für die angeforderte Transaktionsisolationsstufe erforderlichen Annahmen zwischen dem logischen Start und dem logischen Ende der Transaktion zutreffend waren.  
  
 Zu Beginn der Überprüfungsphase wird der Transaktion ein logischer Endzeitpunkt zugewiesen. Die in die Datenbank geschriebenen Zeilenversionen werden für andere Transaktionen zum logischen Endzeitpunkt sichtbar. Weitere Informationen finden Sie unter [Commit-Abhängigkeiten](#cd).  
  
##### <a name="repeatable-read-validation"></a>REPEATABLE READ-Überprüfung  
 Wenn die Isolationsstufe der Transaktion REPEATABLE READ- oder SERIALIZABLE ist, oder Tabellen mit REPEATABLE READ- oder SERIALIZABLE-Isolation zugegriffen werden (Weitere Informationen finden Sie im Abschnitt für die Isolierung einzelner Vorgänge in [Transaktion Isolationsstufen](../../2014/database-engine/transaction-isolation-levels.md)), das System überprüft, dass die Lesevorgänge wiederholt werden. Das System überprüft also, ob die von der Transaktion gelesenen Zeilenversionen beim logischen Endzeitpunkt der Transaktion weiterhin gültig sind.  
  
 Wenn eine Zeile aktualisiert oder geändert wurde, schlägt das Transaktionscommit mit Fehler 41305 fehl ("Fehler beim Ausführen eines Commits für die aktuelle Transaktion aufgrund eines REPEATABLE READ-Überprüfungsfehlers").  
  
 Dieser Fehler kann auch auftreten, wenn eine Tabelle nach einem Einfüge-, Update- oder Löschvorgang und vor dem Transaktionscommit gelöscht wird. Dies gilt nur für Einfüge-, Update- oder Löschvorgänge in systemintern kompilierten gespeicherten Prozeduren. Schreibvorgänge, die mit interpretiertem [!INCLUDE[tsql](../includes/tsql-md.md)] durchgeführt werden, verursachen eine Blockierung der DROP TABLE-Anweisung, die dann bis zum Commit der Transaktion warten muss.  
  
##### <a name="serializable-validation"></a>SERIALIZABLE-Überprüfung  
 Die SERIALIZABLE-Überprüfung wird in zwei Fällen ausgeführt:  
  
-   Wenn die Isolationsstufe der Transaktion SERIALIZABLE lautet oder wenn auf Tabellen unter SERIALIZABLE-Isolation zugegriffen wird.  
  
-   Wenn Zeilen in einen eindeutigen Index eingefügt werden, etwa den für eine PRIMARY KEY-Einschränkung erstellten Index. Das System stellt sicher, dass keine Zeilen mit demselben Schlüssel gleichzeitig eingefügt wurden.  
  
 Das System überprüft, dass keine Phantomzeilen in die Datenbank geschrieben wurden. Die durch die Transaktion ausgeführten Lesevorgänge werden ausgewertet, um zu sicherzustellen, dass keine neuen Zeilen in die Scanbereiche dieser Lesevorgänge eingefügt wurden.  
  
 Das Einfügen eines Schlüssels in einen eindeutigen Index umfasst einen impliziten Lesevorgang, mit dem sichergestellt wird, dass der Schlüssel kein Duplikat darstellt. Die SERIALIZABLE-Überprüfung auf eindeutige Indizes stellt sicher, dass diese Indizes keine Duplikate aufweisen können, falls zwei Transaktionen gleichzeitig denselben Schlüssel einfügen.  
  
 Wenn Phantomzeilen erkannt werden, schlägt das Transaktionscommit mit Fehler 41325 fehl ("Fehler beim Ausführen eines Commits für die aktuelle Transaktion aufgrund eines SERIALIZABLE-Überprüfungsfehlers").  
  
#### <a name="commit-processing"></a>Verarbeiten des Commits  
 Wenn die Überprüfung erfolgreich ist und alle Transaktionsabhängigkeiten aufgelöst sind, geht die Transaktion in die Commitverarbeitungsphase über. Während dieser Phase werden die Änderungen an dauerhaften Tabellen in das Protokoll und das Protokoll auf den Datenträger geschrieben, um Dauerhaftigkeit sicherzustellen. Sobald der Protokolldatensatz der Transaktion auf einen Datenträger geschrieben wurde, geht die Steuerung wieder auf den Client über.  
  
 Alle Commitabhängigkeiten für diese Transaktion werden gelöscht, und alle Transaktionen, die auf den Commit dieser Transaktion gewartet haben, können fortgesetzt werden.  
  
## <a name="limitations"></a>Einschränkungen  
  
-   Datenbankübergreifende Transaktionen werden in Verbindung mit speicheroptimierten Tabellen nicht unterstützt. Transaktionen, die auf speicheroptimierte Tabellen zugreifen, können nicht auf mehrere Datenbanken zugreifen. Davon ausgenommen sind der Lese-/Schreibzugriff auf tempdb und der schreibgeschützte Zugriff auf die master-Systemdatenbank.  
  
-   Verteilte Transaktionen werden in Verbindung mit speicheroptimierten Tabellen nicht unterstützt. Mit BEGIN DISTRIBUTED TRANSACTION gestartete verteilte Transaktionen können nicht auf speicheroptimierte Tabellen zugreifen.  
  
-   Speicheroptimierte Tabellen unterstützen keine Sperren. Explizite Sperren nach Sperrhinweisen (wie TABLOCK, XLOCK, ROWLOCK) werden in Verbindung mit speicheroptimierten Tabellen nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu Transaktionen in speicheroptimierten Tabellen](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)  
  
  
