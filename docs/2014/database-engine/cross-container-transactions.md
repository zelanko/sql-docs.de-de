---
title: Container übergreifende Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5d84b51a-ec17-4c5c-b80e-9e994fc8ae80
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 290aff0bfcb01e098ae87b48cf582cdf999314c4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62807424"
---
# <a name="cross-container-transactions"></a>Containerübergreifende Transaktionen
  Containerübergreifende Transaktionen sind entweder implizite oder explizite Benutzertransaktionen, die Aufrufe von systemintern kompilierten gespeicherten Prozeduren oder Vorgängen für speicheroptimierte Tabellen enthalten.  
  
 In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] lösen Aufrufe von gespeicherten Prozeduren keine Transaktion aus. Ausführungen von systemintern kompilierten Prozeduren im Autocommitmodus (nicht im Kontext einer Benutzertransaktion) werden nicht als containerübergreifende Transaktionen angesehen.  
  
 Jede interpretierte Abfrage, die auf speicheroptimierte Tabellen verweist, wird als Teil einer containerübergreifenden Transaktion angesehen. Dies gilt unabhängig davon, ob die Abfrage über eine explizite oder implizite Transaktion oder im Autocommitmodus ausgeführt wurde.  
  
##  <a name="isolation-of-individual-operations"></a><a name="isolation"></a>Isolierung einzelner Vorgänge  
 Jede [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Transaktion hat eine Isolationsstufe. Die Standardisolationsstufe ist Read Committed. Wenn Sie eine andere Isolationsstufe verwenden möchten, können Sie die Isolationsstufe mithilfe von [Set Transaction Isolation Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)festlegen.  
  
 Häufig ist es notwendig, Vorgänge in speicheroptimierten Tabellen auf einer anderen Isolationsstufe als Vorgänge in datenträgerbasierten Tabellen auszuführen. In einer Transaktion ist es möglich, eine andere Isolationsstufe für eine Auflistung von Anweisungen oder für einen einzelnen Lesevorgang festzulegen.  
  
### <a name="specifying-the-isolation-level-of-individual-operations"></a>Angeben der Isolationsstufe bei einzelnen Vorgängen  
 Um eine andere Isolationsstufe für eine Gruppe von Anweisungen in einer Transaktion festzulegen, können Sie `SET TRANSACTION ISOLATION LEVEL` verwenden. Im folgenden Beispiel einer Transaktion wird die Serializable-Isolationsstufe als Standard verwendet. Die Einfüge- und Auswahlvorgänge in t3, t2 und t1 werden in Repeatable Read-Isolation ausgeführt.  
  
```sql  
set transaction isolation level serializable  
go  
  
begin transaction  
 ......  
  set transaction isolation level repeatable read  
  
  insert t3 select * from t1 join t2 on t1.id=t2.id  
  
  set transaction isolation level serializable  
 ......  
commit  
```  
  
 Um eine Isolationsstufe für einzelne Lesevorgänge festzulegen, die vom Transaktionsstandard abweicht, können Sie einen Tabellenhinweis verwenden (z. B. Serializable). Jede Auswahl entspricht einem Lesevorgang, und jedes Update und jede Löschung entsprechen einem Lesevorgang, da die Zeile immer gelesen werden muss, bevor sie aktualisiert oder gelöscht werden kann. Einfügevorgänge haben keine Isolationsstufe, da Schreibvorgänge in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] immer isoliert ausgeführt werden. Im folgenden Beispiel wird die Standardisolationsstufe Read Committed verwendet. Auf Tabelle t1 wird jedoch mit Serializable-Isolation und auf t2 mit Snapshot-Isolation zugegriffen.  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
 ......  
  
  insert t3 select * from t1 (serializable) join t2 (snapshot) on t1.id=t2.id  
  
  ......  
commit  
```  
  
### <a name="isolation-semantics-for-individual-operations"></a>Isolationssemantik für einzelne Vorgänge  
 Eine serialisierbare Transaktion T wird in vollständiger Isolation ausgeführt. Dabei wird angenommen, dass für alle anderen Transaktionen vor dem Start von T ein Commit ausgeführt wurde oder dass alle anderen Transaktionen erst gestartet werden, nachdem für T ein Commit ausgeführt wurde. Noch komplexer wird es, wenn verschiedene Vorgänge in einer Transaktion über unterschiedliche Isolationsstufen verfügen.  
  
 Die allgemeine Semantik der Transaktions Isolations Stufen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]sowie die Auswirkungen auf das Sperren wird unter [Set Transaction Isolation Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)erläutert.  
  
 Bei containerübergreifenden Transaktionen, in denen verschiedene Vorgänge über unterschiedliche Isolationsstufen verfügen können, sollten Sie sich die Semantik für die Isolation einzelner Lesevorgänge verdeutlichen. Schreibvorgänge sind immer isoliert. Schreibvorgänge in verschiedenen Transaktionen haben keine Auswirkungen aufeinander.  
  
 Ein Datenlesevorgang gibt mehrere Zeilen zurück, die eine Filterbedingung erfüllen.  
  
 Lesevorgänge werden als Teil einer Transaktion T ausgeführt. die Isolations Stufen für Lesevorgänge können im Hinblick auf  
  
 Commitstatus  
 Der Commitstatus bezieht sich darauf, ob für den Datenlesevorgang garantiert ein Commit ausgeführt wird.  
  
 (Transaktionale) Konsistenz  
 Transaktionskonsistenz für einen Satz von Lesevorgängen bezieht sich auf die Frage, ob alle gelesenen Zeilenversionen garantiert Updates aus exakt demselben Transaktionssatz enthalten.  
  
 Stabilitätsgarantien, die das System der Transaktion T im Hinblick auf den Lesevorgang gewährt.  
 Stabilität bezieht sich darauf, ob die Lesevorgänge der Transaktion wiederholbar sind. Würden die Lesevorgänge bei einer Wiederholung dieselben Zeilen und Zeilenversionen zurückgeben?  
  
 Bestimmte Garantien beziehen sich auf die logische Beendigungszeit der Transaktion. In der Regel ist die logische Beendigungszeit der Zeitpunkt, zu dem für die Transaktion ein Commit in der Datenbank ausgeführt wird. Wenn die Transaktion auf speicheroptimierte Tabellen zugreift, ist die logische Beendigungszeit technisch gesehen der Anfang der Überprüfungsphase. (Weitere Informationen finden Sie in der Erörterung der Transaktions Lebensdauer unter [Transaktionen in Speicher optimierten Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Für eine Transaktion (t) sind eigene Updates unabhängig von der Isolationsstufe immer sichtbar:  
  
 READ UNCOMMITTED  
 Für die gelesenen Daten, die unter Umständen weder konsistent noch stabil sind, wird möglicherweise kein Commit ausgeführt. Sie enthalten jedoch frühere Schreibvorgänge, die von T vorgenommen wurden.  
  
 READ COMMITTED  
 Für die gelesenen Daten wird ein Commit ausgeführt.  
  
 SNAPSHOT  
 Alle Lesevorgänge, die von T per Snapshot-Isolation ausgeführt wurden, haben die gleiche logische Lesezeit, nämlich den Beginn der Transaktion. Für die gelesenen Daten wird garantiert ein Commit ausgeführt, und sie sind ab der logischen Lesezeit konsistent. Wenn ein Lesevorgang ab der ursprünglichen Lesezeit wiederholt wird, wird garantiert das gleiche Ergebnis zurückgegeben.  
  
 REPEATABLE READ  
 Für die gelesenen Daten wird garantiert ein Commit ausgeführt, und die Stabilität wird zur logischen Beendigungszeit der Transaktion erhöht.  
  
 SERIALIZABLE  
 Alle Garantien von Repeatable Read zuzüglich Phantom Vermeidung und Transaktions Konsistenz in Bezug auf alle serialisierbaren Lesevorgänge, die von t. Phantom Vermeidung durchgeführt werden, bedeutet, dass der Scanvorgang nur zusätzliche Zeilen zurückgeben kann, die von t geschrieben wurden, aber keine Zeilen, die von anderen Transaktionen geschrieben wurden.  
  
 Beachten Sie die folgende Transaktion:  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  -- remove all rows from t3; the related read operation is performed under read committed   
  -- isolation, as this is the default for the transaction  
  delete from t3  
  
  -- copy the contents from t1 to t3; the read on t1 is performed under the serializable   
  -- isolation level  
  insert t3 select * from t1 (serializable)  
  
  -- compare t3 and t1; note: the result set may not be empty, as rows may have been added   
  -- by other transaction before this select, due to the read committed isolation level  
  select * from t3 except t1  
  
  -- compare t1 and t3; note: the result set is empty, as no rows have been added to t1   
  -- since its contents were copied to t1, due to the serializable isolation level  
  select * from t1 except t3  
commit  
```  
  
 Diese Transaktion löscht alle Zeilen aus t3 mit Read Committed-Isolation, kopiert alle Zeilen mit Serializable-Isolation von t1 nach t3 und vergleicht dann t1 und t3. Einige Zeilen [nicht in t1] wurden möglicherweise seit der Leerung der Tabelle t3 hinzugefügt. t1 wurden keine Zeilen hinzugefügt, da die Kopie serialisierbar war.  
  
 Obwohl der Lesevorgang von t1 am Ende der Transaktion syntaktisch gesehen "Read Committed" entspricht, ist er eigentlich "Serializable", da derselbe Lesevorgang schon zu einem früheren Zeitpunkt in der Transaktion mit Serializable-Isolation ausgeführt wurde: Serialisierbarkeit garantiert, dass dieselben Zeilen zurückgegeben werden, wenn der Lesevorgang zu einem späteren Zeitpunkt in der Transaktion ausgeführt wird.  
  
## <a name="cross-container-transactions-and-isolation-levels"></a>Containerübergreifende Transaktionen und Isolationsstufen  
 Eine Container übergreifende Transaktion kann als zwei Seiten betrachtet werden: eine Datenträger basierte Seite (für Vorgänge in Datenträger basierten Tabellen) und eine Speicher optimierte Seite (für Vorgänge in Speicher optimierten Tabellen). Diese beiden Seiten können unterschiedliche Isolationsstufen aufweisen. Tatsächlich können einzelne Lesevorgänge auf jeder Seite unterschiedliche Isolationsstufen haben.  
  
 Die datenträgerbasierte Seite einer gegebenen Transaktion T erreicht eine bestimmte Isolationsstufe X, wenn eine der folgenden Bedingungen erfüllt wird:  
  
-   Sie beginnt in X. Das heißt, der Standard der Sitzung war X, weil Sie entweder `SET TRANSACTION ISOLATION LEVEL`ausgeführt haben oder der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standardwert ist.  
  
-   Während der Transaktion wird die Standardisolationsstufe mit `SET TRANSACTION ISOLATION LEVEL` in X geändert.  
  
-   Ein Lesevorgang in einer datenträgerbasierten Tabelle wird mit der Isolationsstufe X und der Syntax `WITH (X)` ausgeführt.  
  
 Die speicheroptimierte Seite von T erreicht eine Isolationsstufe Y, wenn während der Ausführung von T ein Lesevorgang in einer speicheroptimierten Tabelle oder eine systemintern kompilierte gespeicherte Prozedur mit der Isolationsstufe Y ausgeführt wird.  
  
 Betrachten Sie die folgende Transaktion als Beispiel. Hier sind t1 und t2 datenträgerbasierte Tabellen und t3 und t4 speicheroptimierte Tabellen.  
  
 Die datenträgerbasierte Seite der Transaktion erreicht die Isolationsstufe "Read Committed", da sie auf dieser Ebene beginnt. Die datenträgerbasierte Seite erreicht auch "Repeatable Read", da der erste Lesevorgang mit dieser Isolationsstufe ausgeführt wird. Der Löschvorgang am Ende der Transaktion wird mit der Read Committed-Isolationsstufe ausgeführt und führt daher keine neue Isolationsstufe ein.  
  
 Die speicheroptimierte Seite der Transaktion kann eine von zwei Stufen erreichen: Wenn condition1 wahr ist, wird "Serializable" erreicht, und wenn sie falsch ist, erreicht die speicheroptimierte Seite lediglich die Snapshot-Isolation.  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  select * from t1 (repeatableread)  
  
  if condition1 begin  
    insert t3 select * from t4 (serializable)  
  end  
  else begin  
    insert t3 select * from t4 (snapshot)  
  end  
  
  delete from t1  
commit  
```  
  
### <a name="supported-isolation-levels-for-cross-container-transactions"></a>Unterstützte Isolationsstufen für containerübergreifende Transaktionen  
 Es gibt Einschränkungen hinsichtlich der Isolationsstufen, die bei Vorgängen in speicheroptimierten Tabellen in containerübergreifenden Transaktionen verwendet werden.  
  
 Speicheroptimierte Tabellen unterstützen die Isolationsstufen SNAPSHOT, REPEATABLE READ und SERIALIZABLE. Bei Autocommittransaktionen unterstützen speicheroptimierte Tabellen die Isolationsstufe READ COMMITTED.  
  
 Die folgenden Szenarien werden unterstützt:  
  
-   Containerübergreifende READ UNCOMMITTED-, READ COMMITTED- und READ_COMMITTED_SNAPSHOT-Transaktionen können mit SNAPSHOT-, REPEATABLE READ- und SERIALIZABLE-Isolation auf speicheroptimierte Tabellen zugreifen. Die READ COMMITTED-Garantie bedeutet für die Transaktion, dass für alle Zeilen, die von der Transaktion gelesen wurden, ein Commit in der Datenbank ausgeführt wurde.  
  
-   REPEATABLE READ- und SERIALIZABLE-Transaktionen können mit der SNAPSHOT-Isolation auf speicheroptimierte Tabellen zugreifen.  
  
## <a name="read-only-cross-container-transactions"></a>Schreibgeschützte containerübergreifende Transaktionen  
 Für die meisten schreibgeschützten Transaktionen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wird zur Commitzeit ein Rollback ausgeführt. Da es keine Änderungen gibt, für die ein Commit in der Datenbank ausgeführt wird, gibt das System einfach die Ressourcen frei, die von der Transaktion verwendet wurden. Für schreibgeschützte datenträgerbasierte Transaktionen werden alle von der Transaktion vorgenommenen Sperren zu diesem Zeitpunkt aufgehoben. Für schreibgeschützte speicheroptimierte Transaktionen, die die Ausführung einer einzelnen systemintern kompilierten Prozedur umfassen, wird keine Überprüfung ausgeführt.  
  
 Für containerübergreifende schreibgeschützte Transaktionen im Autocommitmodus wird einfach am Ende der Transaktion ein Rollback ausgeführt. Es wird keine Überprüfung ausgeführt.  
  
 Explizite oder implizite containerübergreifende schreibgeschützte Transaktionen führen die Überprüfung zur Commitzeit aus, wenn die Transaktion mit REPEATABLE READ- oder SERIALIZABLE-Isolation auf speicheroptimierte Tabellen zugreift. Ausführliche Informationen zur Validierung finden Sie im Abschnitt zu Konflikterkennung, Validierung und Commit-Abhängigkeits Prüfungen in [Transaktionen in Speicher optimierten Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu Transaktionen in Speicher optimierten Tabellen](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [Richtlinien für Transaktions Isolations Stufen mit Speicher optimierten Tabellen](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md)   
 [Richtlinien zur Wiederholungslogik für Transaktionen auf speicheroptimierten Tabellen](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  
