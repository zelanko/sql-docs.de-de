---
title: Richtlinien für Transaktionsisolationsstufen mit speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e365e9ca-c34b-44ae-840c-10e599fa614f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aced288e62fefe46777993fd46130b8dd65e8d1b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510023"
---
# <a name="guidelines-for-transaction-isolation-levels-with-memory-optimized-tables"></a>Richtlinien für Transaktionsisolationsstufen mit speicheroptimierten Tabellen
  In vielen Szenarien müssen Sie die Transaktionsisolationsstufe angeben. Transaktionsisolation für speicheroptimierte Tabellen unterscheidet sich von Transaktionsisolation für datenträgerbasierte Tabellen.  
  
 Anforderungen zum Angeben der Transaktionsisolationsstufe:  
  
-   TRANSAKTIONSISOLATIONSSTUFE ist eine erforderliche Option für den ATOMIC-Block, der den Inhalt einer systemintern kompilierten gespeicherten Prozedur enthält.  
  
-   Aufgrund von Einschränkungen bei der Isolationsstufenverwendung in containerübergreifenden Transaktionen, muss die Verwendung speicheroptimierter Tabellen in interpretiertem [!INCLUDE[tsql](../includes/tsql-md.md)] häufig von einem Tabellenhinweis begleitet werden, der die Isolationsstufe für den Tabellenzugriff angibt. Weitere Informationen zu isolationsstufenhinweisen und containerübergreifenden Transaktionen, finden Sie unter [Isolationsstufen von Transaktionen](../../2014/database-engine/transaction-isolation-levels.md).  
  
-   Die gewünschte Transaktionsisolationsstufe muss explizit deklariert werden. Es ist nicht möglich, Sperrhinweise zu verwenden (etwa XLOCK), um die Isolation bestimmter Zeilen oder Tabellen in der Transaktion sicherzustellen.  
  
-   Die Anwendung, die auf die Datenbank zugreift, sollte Wiederholungslogik implementieren, um Fehler zu behandeln, die aus Konflikten aufgrund fehlgeschlagener Transaktionen, Überprüfungsfehlern und Commitabhängigkeitsfehlern resultieren. Beachten Sie, dass Commitabhängigkeitsfehler auch bei schreibgeschützten Transaktionen auftreten können.  
  
-   Transaktionen mit langer Laufzeit sollten bei speicheroptimierten Tabellen vermieden werden. Derartige Transaktionen erhöhen die Wahrscheinlichkeit, dass Konflikte auftreten und Transaktionen infolgedessen beendet werden. Eine Transaktion mit langer Ausführungszeit verzögert außerdem die Garbage Collection. Je länger eine Transaktion ausgeführt wird, desto länger werden zuletzt gelöschte Zeilenversionen von In-Memory OLTP beibehalten, wodurch die Suchleistung bei neuen Transaktionen beeinträchtigt werden kann.  
  
 Bei datenträgerbasierten Tabellen werden für die Transaktionsisolation normalerweise Sperren und Blockierungen eingesetzt. Speicheroptimierte Tabellen basieren auf Multiversionsverwaltung und Konflikterkennung, um Isolation sicherzustellen. Ausführliche Informationen finden Sie im Abschnitt zur Konflikterkennung, zur Überprüfung und zu Commitabhängigkeitsüberprüfungen unter [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Datenträgerbasierte Tabellen ermöglichen Multiversionsverwaltung mit den Isolationsstufen SNAPSHOT und READ_COMMITTED_SNAPSHOT. Bei speicheroptimierten Tabellen sind alle Isolationsstufen multiversionsbasiert, einschließlich REPEATABLE READ und SERIALIZABLE.  
  
## <a name="types-of-transactions"></a>Transaktionstypen  
 Jede Abfrage in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wird im Kontext einer Transaktion ausgeführt.  
  
 Es gibt drei Typen von Transaktionen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   Autocommittransaktionen. Wenn es keinen aktiven Transaktionskontext gibt und implizite Transaktionen in der Sitzung auf ON festgelegt werden, verfügt jede Abfrage über einen eigenen Transaktionskontext. Die Transaktion startet, wenn die Ausführung der Anweisung beginnt, und endet, wenn die Anweisung abgeschlossen ist.  
  
-   Explizite Transaktionen. Der Benutzer startet die Transaktion durch eine explizite BEGIN TRAN- oder BEGIN ATOMIC-Anweisung. Die Transaktion wird nach der entsprechenden COMMIT- und ROLLBACK- oder END-Anweisung abgeschlossen (im Fall eines ATOMIC-Blocks).  
  
-   Implizite Transaktionen. Wenn die Option IMPLICIT_TRANSACTIONS auf ON festgelegt ist, wird eine Transaktion implizit gestartet, wenn der Benutzer eine Anweisung ausführt und es keinen aktiven Transaktionskontext gibt. Die Transaktion wird durch eine explizite COMMIT- und ROLLBACK-Anweisung abgeschlossen.  
  
## <a name="baseline-read-committed-isolation"></a>READ COMMITTED-Basislinienisolation  
 Die Standardisolationsstufe in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ist READ COMMITTED.  
  
 Die READ COMMITTED-Isolationsstufe gewährleistet, dass Transaktionen nicht auf Daten zugreifen, für die nach einer Änderung außerhalb der aktuellen Transaktion noch kein Commit ausgeführt wurde. Die Transaktion liest also nur Daten, für die ein Commit in der Datenbank ausgeführt wurde oder die von der aktuellen Transaktion geändert wurden.  
  
 Bei allen Isolationsstufen, die für speicheroptimierte Tabellen unterstützt werden, ist Read Committed sichergestellt. Wenn die Transaktion keine stärkeren Garantien erfordert, können Sie daher eine beliebige Isolationsstufe verwenden, die für speicheroptimierte Tabellen unterstützt wird. SNAPSHOT beansprucht im Vergleich zu anderen Isolationsstufen die wenigsten Systemressourcen.  
  
 Die Garantie, welche die SNAPSHOT-Isolationsstufe (die unterste Ebene der Isolation, die für speicheroptimierte Tabellen unterstützt wird) bietet, umfasst die READ COMMITTED-Garantien. Jede Anweisung in der Transaktion liest die gleiche, konsistente Version der Datenbank. Er werden nicht nur alle von der Transaktion gelesenen Zeilen an die Datenbank übergeben, sondern bei allen Lesevorgängen wird auch der Satz von Änderungen angezeigt, die durch den gleichen Transaktionssatz ausgeführt wurden.  
  
 **Richtlinie**: Wenn nur die READ COMMITTED-isolationsgarantie erforderlich ist, interpretiert mit SNAPSHOT-Isolation mit systemintern kompilierten gespeicherten Prozeduren und für den Zugriff auf Speicheroptimierte Tabellen über [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
 Bei speicheroptimierten Tabellen wird für Autocommittransaktionen die Isolationsstufe READ COMMITTED implizit SNAPSHOT zugeordnet. Wenn die Sitzungseinstellung TRANSACTION ISOLATION LEVEL auf READ COMMITTED festgelegt wird, ist es daher nicht notwendig, die Isolationsstufe durch einen Tabellenhinweis anzugeben, wenn Sie auf speicheroptimierte Tabellen zugreifen.  
  
 Das folgende Beispiel für eine Autocommittransaktion zeigt einen Join zwischen einer speicheroptimierten Tabelle [Customers] und einer normalen Tabelle [Order History] als Teil eines Ad-hoc-Batches:  
  
```tsql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;  
GO  
SELECT *   
FROM dbo.Customers AS c   
LEFT JOIN dbo.[Order History] AS oh   
    ON c.customer_id = oh.customer_id;  
```  
  
 Das folgende Beispiel für explizite oder implizite Transaktionen zeigt den gleichen Join, dieses Mal aber in einer expliziten Benutzertransaktion. Auf die speicheroptimierte Tabelle [Customers] wird unter der SNAPSHOT-Isolation zugegriffen, wie durch den Tabellenhinweis WITH (SNAPSHOT) angegeben, und auf die normale Tabelle [Order History] wird unter der READ COMMITTED-Isolation zugegriffen:  
  
```tsql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
GO  
BEGIN TRAN  
SELECT * FROM dbo.Customers c with (SNAPSHOT)   
LEFT JOIN dbo.[Order History] oh   
    ON c.customer_id=oh.customer_id  
...  
COMMIT  
```  
  
### <a name="operational-differences"></a>Betriebliche Unterschiede  
 Neben der READ COMMITTED-Garantie gibt es auch zwei wichtige Implementierungsdetails, auf denen Anwendungen mit datenträgerbasierten Tabellen basieren können. Beachten Sie Folgendes, wenn Sie eine datenträgerbasierte Tabelle, auf die mithilfe von READ COMMITTED-Isolation zugegriffen wird, in eine speicheroptimierte Tabelle konvertieren, auf die mithilfe von SNAPSHOT-Isolation zugegriffen wird:  
  
-   Die Implementierung der READ COMMITTED-Isolationsstufe für datenträgerbasierte Tabellen (vorausgesetzt, READ_COMMITTED_SNAPSHOT ist OFF) verwendet Sperren, um Konflikte zwischen Readern und Writern zu verhindern. Wenn ein Writer mit der Aktualisierung einer Zeile beginnt, wird eine Sperre gesetzt, die erst aufgehoben wird, wenn für die Transaktion ein Commit ausgeführt wurde. Alle Lesevorgänge werden blockiert und warten darauf, dass für die Schreibtransaktion ein Commit ausgeführt wird.  
  
     Einige Anwendungen setzen möglicherweise voraus, dass Reader immer warten, bis Writer einen Commit durchgeführt haben, insbesondere wenn auf der Anwendungsebene eine Synchronisierung zwischen den beiden Transaktionen vorliegt.  
  
     **Richtlinie:** Anwendungen können nicht auf Blockierverhalten basieren. Wenn eine Anwendung die Synchronisierung zwischen gleichzeitigen Transaktionen erfordert, solche Logik kann implementiert werden auf der Anwendungsebene oder in der Datenbankschicht über [Sp_getapplock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql).  
  
-   In Transaktionen, die READ COMMITTED-Isolation verwenden, wird jeder Anweisung die neueste Version der Zeilen in der Datenbank angezeigt. Daher sind Änderungen des Datenbankstatus in nachfolgenden Anweisungen sichtbar.  
  
     Ein Tabellenabruf mithilfe einer WHILE-Schleife, bis eine neue Zeile gefunden wurde, ist ein Beispiel für ein Anwendungsmuster, das diese Annahme verwendet. Bei jeder Iteration der Schleife werden der Abfrage die neuesten Updates in der Datenbank angezeigt.  
  
     **Richtlinie:** Wenn eine Anwendung eine Speicheroptimierte Tabelle zum Abrufen der letzten Zeilen in die Tabelle geschrieben wurden muss, verschieben Sie die Abrufschleife außerhalb des Bereichs der Transaktion aus.  
  
     Es folgt ein Beispiel für ein Anwendungsmuster, das die folgende Annahme verwendet: Abrufen einer Tabelle mithilfe einer WHILE-Schleife, bis eine neue Zeile gefunden wird. In jeder Schleifeniteration greift die Abfrage auf die neuesten Updates in der Datenbank zu.  
  
 Im folgenden Beispielskript wird eine Tabelle t1 abgerufen, bis sie über eine Zeile verfügt. Dann wird aus der Tabelle eine einzelne Zeile für die weitere Verarbeitung entfernt.  
  
 Beachten Sie, dass die Abruflogik außerhalb des Bereichs der Transaktion liegen muss, da sie die Momentaufnahmeisolation verwendet, um auf Tabelle t1 zuzugreifen. Wenn die Abruflogik innerhalb des Bereichs einer Transaktion verwendet wird, würde das zu einer Transaktion mit langer Laufzeit führen, was nicht empfohlen wird.  
  
```tsql  
-- poll table  
WHILE NOT EXISTS (SELECT 1 FROM dbo.t1)  
BEGIN   
  -- if empty, wait and poll again  
  WAITFOR DELAY '00:00:01'  
END  
  
BEGIN TRANSACTION  
  DECLARE @id int  
  SELECT TOP 1 @id=id FROM dbo.t1 WITH (SNAPSHOT)  
  DELETE FROM dbo.t1 WITH (SNAPSHOT) WHERE id=@id  
  
  -- insert processing based on @id  
COMMIT  
```  
  
## <a name="locking-table-hints"></a>Sperrhinweise für Tabellen  
 Sperrhinweise ([Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)) wie HOLDLOCK und XLOCK mit datenträgerbasierten Tabellen verwendet werden können, damit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mehr Sperren als für die angegebene Isolationsstufe erforderlich sind.  
  
 Speicheroptimierte Tabellen verwenden keine Sperren. Höhere Isolationsstufen wie REPEATABLE READ und SERIALIZABLE können verwendet werden, um die gewünschten Garantien zu deklarieren.  
  
 Sperrhinweise werden nicht unterstützt. Deklarieren Sie stattdessen die erforderlichen Garantien über die Transaktionsisolationsstufen. (NOLOCK wird unterstützt, da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keine Sperren für speicheroptimierten Tabellen verwendet. Beachten Sie, dass NOLOCK anders als bei datenträgerbasierten Tabellen kein READ UNCOMMITTED-Verhalten für speicheroptimierte Tabellen impliziert.)  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu Transaktionen in speicheroptimierten Tabellen](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [Richtlinien zur Wiederholungslogik für Transaktionen in speicheroptimierten Tabellen](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)   
 [Transaktionsisolationsstufen](../../2014/database-engine/transaction-isolation-levels.md)  
  
  
