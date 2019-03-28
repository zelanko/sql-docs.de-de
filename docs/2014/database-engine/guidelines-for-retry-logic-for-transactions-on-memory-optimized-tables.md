---
title: Richtlinien zur Wiederholungslogik für Transaktionen in speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2a35c37-4449-49ee-8bba-928028f1de66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 01f719470419940b130967b7c1360c4ae0c281eb
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530132"
---
# <a name="guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables"></a>Richtlinien zur Wiederholungslogik für Transaktionen auf speicheroptimierten Tabellen
  Es gibt Fehlerbedingungen, die bei Transaktionen auftreten, die auf speicheroptimierte Tabellen zugreifen.  
  
-   41302. Die aktuelle Transaktion hat versucht, einen Datensatz zu aktualisieren, der seit dem Start dieser Transaktion aktualisiert wurde.  
  
-   41305. Fehler beim Ausführen eines Commits für die aktuelle Transaktion aufgrund eines REPEATABLE READ-Überprüfungsfehlers.  
  
-   41325. Für die aktuelle Transaktion wurde aufgrund eines serialisierbaren Überprüfungsfehlers kein Commit ausgeführt.  
  
-   41301. Eine vorherige Transaktion, zu der die aktuelle Transaktion eine Abhängigkeit eingegangen war, wurde abgebrochen. Die aktuelle Transaktion kann keinen Commit mehr ausführen.  
  
 Eine häufige Ursache für diesen Fehler ist die gegenseitige Beeinflussung von gleichzeitig ausgeführten Transaktion. Die gängige Korrekturmaßnahme besteht darin, die Transaktion zu wiederholen.  
  
 Weitere Informationen zu diesen fehlerbedingungen finden Sie im Abschnitt für die Konflikterkennung, Überprüfung und Commitabhängigkeitsüberprüfungen unter [Transaktionen in speicheroptimierten Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Deadlocks (Fehlercode 1205) können bei speicheroptimierten Tabellen nicht auftreten. Sperren werden bei speicheroptimierten Tabellen nicht verwendet. Wenn die Anwendung allerdings bereits Wiederholungslogik für Deadlocks enthält, könnte die vorhandene Logik erweitert werden, um die neuen Fehlercodes einzuschließen.  
  
## <a name="considerations-for-retrying"></a>Überlegungen zu Wiederholungen  
 Bei Anwendungen treten in der Regel Konflikte zwischen Transaktionen auf, und zur Behebung dieser Konflikte muss Wiederholungslogik implementiert werden. Die Anzahl der aufgetretenen Konflikte hängt von mehreren Faktoren ab:  
  
-   Konflikt bei einzelnen Zeilen. Das Konfliktpotenzial steigt mit der Anzahl der Transaktionen, die versuchen, dieselbe Zeile zu aktualisieren.  
  
-   Anzahl der von REPEATABLE READ-Transaktionen gelesenen Zeilen. Je mehr Zeilen gelesen werden, desto größer ist die Wahrscheinlichkeit, dass einige dieser Zeilen durch gleichzeitige Transaktionen aktualisiert werden. Dies führt zu REPEATABLE READ-Überprüfungsfehlern.  
  
-   Größe der Scanbereiche, die von SERIALIZABLE-Transaktionen verwendet werden. Je größer die Scanbereiche, je höher die Wahrscheinlichkeit, dass durch gleichzeitige Transaktionen Phantomzeilen entstehen, die SERIALIZABLE-Überprüfungsfehler verursachen.  
  
     Es ist schwierig für eine Anwendung, diese Konflikte zu vermeiden, was Wiederholungslogik erforderlich macht.  
  
> [!IMPORTANT]  
>  Lese-/Schreibtransaktionen, die auf speicheroptimierte Tabellen zugreifen, erfordern Wiederholungslogik.  
  
### <a name="considerations-for-read-only-transactions-and-natively-compiled-stored-procedures"></a>Überlegungen zu schreibgeschützten Transaktionen und systemintern kompilierten gespeicherten Prozeduren  
 Schreibgeschützte Transaktionen, die eine einzelne Ausführung einer systemintern kompilierten gespeicherten Prozedur enthalten, benötigen keine Überprüfung auf REPEATABLE READ- und SERIALIZABLE-Transaktionen. Schreibkonflikte können auftreten, weil eine Transaktion schreibgeschützt ist.  
  
 Abhängigkeitsfehler können jedoch weiterhin auftreten. Abhängigkeitsfehler sind seltener als Fehler, die aus Konflikten entstehen. Daher ist bei schreibgeschützten Transaktionen, die einzelne Ausführungen systemintern kompilierter gespeicherter Prozeduren enthalten, in vielen Fällen keine spezifische Wiederholungslogik erforderlich.  
  
### <a name="considerations-for-read-only-transactions-and-cross-container-transactions"></a>Überlegungen zu schreibgeschützten Transaktionen und containerübergreifenden Transaktionen  
 Schreibgeschützte containerübergreifende Transaktionen, die Transaktionen sind, die außerhalb des Kontexts einer systemintern kompilierten gespeicherten Prozedur gestartet werden, führen keine Überprüfung aus, wenn auf alle speicheroptimierten Tabellen unter der SNAPSHOT-Isolation zugegriffen wird. Wenn auf speicheroptimierte Tabellen unter REPEATABLE READ- oder SERIALIZABLE-Isolation zugegriffen wird, wird allerdings zum Commitzeitpunkt eine Überprüfung ausgeführt. In diesem Fall kann Wiederholungslogik erforderlich sein.  
  
 Weitere Informationen finden Sie im Abschnitt zu Containerübergreifenden Transaktionen in [Isolationsstufen von Transaktionen](../../2014/database-engine/transaction-isolation-levels.md).  
  
## <a name="implementing-retry-logic"></a>Implementieren von Wiederholungslogik  
 Wie bei allen Transaktionen, die auf speicheroptimierte Tabellen zugreifen, müssen Sie Wiederholungslogik vorsehen, um mögliche Fehler wie Schreibkonflikte (Fehlercode 41302) oder Abhängigkeitsfehler (Fehlercode 41301) zu behandeln. Obwohl die Fehlerrate in den meisten Anwendungen gering ausfällt, müssen Fehler durch eine Wiederholung der Transaktion behandelt werden. Es gibt zwei Möglichkeiten, Wiederholungslogik zu implementieren:  
  
-   Wiederholungen auf Clientseite. Im Allgemeinen empfiehlt es sich, Wiederholungslogik auf Clientseite zu implementieren. Die Clientanwendung fängt den von der Transaktion ausgelösten Fehler ab und wiederholt die Transaktion. Wenn eine vorhandene Clientanwendung über Wiederholungslogik zum Behandeln von Deadlocks verfügt, können Sie die Anwendung für die Behandlung der neuen Fehlercodes erweitern.  
  
-   Verwenden einer gespeicherten Wrapperprozedur. Der Client ruft eine gespeicherte Prozedur mit interpretiertem [!INCLUDE[tsql](../includes/tsql-md.md)] auf, die die systemintern kompilierte gespeicherte Prozedur aufruft oder die Transaktion ausführt. Die Wrapperprozedur fängt den Fehler anschließend unter Verwendung von Try/Catch-Logik ab und wiederholt den Prozeduraufruf nach Bedarf. Es ist möglich, dass die Ergebnisse vor dem Fehler an den Client zurückgegeben werden und der Client nicht angewiesen wird, die Ergebnisse zu verwerfen. Zur Sicherheit empfiehlt es sich, diese Methode nur mit systemintern kompilierten gespeicherten Prozeduren zu verwenden, die keine Resultsets an den Client zurückgeben.  
  
 Die Wiederholungslogik kann entweder in [!INCLUDE[tsql](../includes/tsql-md.md)] oder im Anwendungscode auf der mittleren Ebene implementiert werden.  
  
 Zwei mögliche Gründe, Wiederholungslogik in Erwägung zu ziehen:  
  
-   Die Clientanwendung verfügt über Wiederholungslogik für andere Fehlercodes, wie 1205, die Sie erweitern können.  
  
-   Konflikte sind selten, und ist es wichtig, die End-to-End-Latenzzeit mithilfe einer vorbereiteten Ausführung zu reduzieren. Weitere Informationen zum Ausführen von systemintern kompilierten gespeicherten Prozeduren direkt, finden Sie unter [Natively Compiled Stored Procedures](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
  
 Das folgende Beispiel zeigt Wiederholungslogik in einer interpretierten gespeicherten [!INCLUDE[tsql](../includes/tsql-md.md)]-Prozedur, die einen Aufruf einer systemintern kompilierten gespeicherten Prozedur oder einer containerübergreifenden Transaktion enthält.  
  
```sql  
CREATE PROCEDURE usp_my_procedure @param1 type1, @param2 type2, ...  
AS  
BEGIN  
  -- number of retries - tune based on the workload  
  DECLARE @retry INT = 10  
  
  WHILE (@retry > 0)  
  BEGIN  
    BEGIN TRY  
  
      -- exec usp_my_native_proc @param1, @param2, ...  
  
      --       or  
  
      -- BEGIN TRANSACTION  
      --   ...  
      -- COMMIT TRANSACTION  
  
      SET @retry = 0  
    END TRY  
    BEGIN CATCH  
      SET @retry -= 1  
  
      -- the error number for deadlocks (1205) does not need to be included for   
      -- transactions that do not access disk-based tables  
      IF (@retry > 0 AND error_number() in (41302, 41305, 41325, 41301, 1205))  
      BEGIN  
        -- these error conditions are transaction dooming - rollback the transaction  
        -- this is not needed if the transaction spans a single native proc execution  
        --   as the native proc will simply rollback when an error is thrown   
        IF XACT_STATE() = -1  
          ROLLBACK TRANSACTION  
  
        -- use a delay if there is a high rate of write conflicts (41302)  
        --   length of delay should depend on the typical duration of conflicting transactions  
        -- WAITFOR DELAY '00:00:00.001'  
      END  
      ELSE  
      BEGIN  
        -- insert custom error handling for other error conditions here  
  
        -- throw if this is not a qualifying error condition  
        ;THROW  
      END  
    END CATCH  
  END  
END  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu Transaktionen in speicheroptimierten Tabellen](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [Transaktionen in speicheroptimierten Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md)   
 [Richtlinien für Transaktionsisolationsstufen mit speicheroptimierten Tabellen](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md)  
  
  
