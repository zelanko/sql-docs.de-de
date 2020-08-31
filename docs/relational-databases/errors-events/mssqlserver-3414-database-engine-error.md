---
description: MSSQLSERVER_3414
title: MSSQLSERVER_3414 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3414 (Database Engine error)
ms.assetid: f25852f9-b91c-4356-b817-78bec9ec8db4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a7a7d69c27ed422763c5c697f003ba9fb4c82286
ms.sourcegitcommit: a0245fdae1ff9045f587a3a67b72f34405d35a4f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2020
ms.locfileid: "88618096"
---
# <a name="mssqlserver_3414"></a>MSSQLSERVER_3414
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|3414|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|REC_GIVEUP|  
|Meldungstext|Fehler bei der Wiederherstellung. Die '%.*ls'-Datenbank (Datenbank-ID %d) kann daher nicht neu gestartet werden. Diagnostizieren und beheben Sie die Wiederherstellungsfehler, oder führen Sie eine Wiederherstellung von einer als fehlerfrei bekannten Sicherung aus. Falls die Fehler nicht behoben werden oder unerwartete Fehler auftreten, wenden Sie sich an den technischen Support.|  
  
## <a name="explanation"></a>Erklärung  
Die angegebene Datenbank wurde wiederhergestellt, konnte jedoch nicht gestartet werden, da Fehler bei der Wiederherstellung auftraten. Durch diesen Fehler wurde die Datenbank in den SUSPECT-Status versetzt. Die primäre Dateigruppe und möglicherweise weitere Dateigruppen sind fehlerverdächtig und u. U. beschädigt. Die Datenbank kann während Starts von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht wiederhergestellt werden und ist daher nicht verfügbar. Eine Aktion seitens des Benutzers ist erforderlich, um das Problem zu beheben. Der SUSPECT-Status wird sowohl im SQL Server Management Studio (neben dem Datenbanksymbol) als auch in der Spalte sys.databases.state_desc angezeigt. Der Versuch, eine Datenbank mit diesem Status zu verwenden, führt zu folgendem Fehler:

```
Msg 926, Level 14, State 1, Line 1 
Database 'mydb' cannot be opened. It has been marked SUSPECT by recovery. See the SQL Server errorlog for more information
```
  
Beachten Sie, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz heruntergefahren wird, wenn dieser Fehler für **tempdb** auftritt.  

## <a name="cause"></a>Ursache
Dieser Fehler kann auf vorübergehende Systemschwierigkeiten zurückzuführen sein, die beim Versuch, die Serverinstanz zu starten oder eine Datenbank wiederherzustellen, aufgetreten sind. Es kann jedoch auch ein dauerhafter Fehler vorliegen, der bei jedem Versuch auftritt, die Datenbank zu starten. Der Wiederherstellungsfehler ist in der Regel auf Fehler zurückzuführen, die vor dem Fehler 3414 im Fehlerprotokoll (ERRORLOG) oder Ereignisprotokoll zu finden sind. Der vorherige Fehler in der Protokolldatei enthält den gleichen spid<n>-Wert. Der folgende Wiederherstellungsfehler ist beispielsweise auf einen Prüfsummenfehler zurückzuführen, der beim Versuch, einen Protokollblock zu lesen, aufgetreten ist. Beachten Sie, dass *spid15s* in allen Zeilen enthalten ist:

```
2020-03-31 17:33:13.00 spid15s     Error: 824, Severity: 24, State: 4.  
2020-03-31 17:33:13.00 spid15s     SQL Server detected a logical consistency-based I/O error: (bad checksum). It occurred during a read of page (0:-1) in database ID 13 at offset 0x0000000000b800 in file 'C:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\DATA\mydb_log.LDF'.  Additional messages in the SQL Server error log or system event log may provide more detail. This is a severe error condition that threatens database integrity and must be corrected immediately. Complete a full database consistency check (DBCC CHECKDB). This error can be caused by many factors; for more information, see SQL Server Books Online.   
2020-03-31 17:33:13.16 spid15s     Error: 3414, Severity: 21, State: 1.  
2020-03-31 17:33:13.16 spid15s     An error occurred during recovery, preventing the database 'mydb' (database ID 13) from restarting. Diagnose the recovery errors and fix them, or restore from a known good backup. If errors are not corrected or expected, contact Technical Support
```


Es gibt eine große Bandbreite von Fehlern, die dazu führen können, dass ein Datenbank-Wiederherstellungsfehler auftritt. Auch wenn Sie jeden Fehler im Einzelfall auswerten müssen, können Datenbank-Wiederherstellungsfehler in der Regel wie im Abschnitt „Benutzeraktion“ weiter unten beschrieben behoben werden.

## <a name="user-action"></a>Benutzeraktion  
 
Überprüfen Sie das Windows-Ereignisprotokoll oder ERRORLOG auf einen vorherigen Fehler, der Aufschluss über den Fehler gibt, um Informationen darüber zu erhalten, warum der Fehler 3414 aufgetreten ist. Die entsprechende Benutzeraktion hängt davon ab, ob die Informationen im Windows-Ereignisprotokoll angeben, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehler durch eine vorübergehende Bedingung oder einen dauerhaften Fehler verursacht wurde. Die Fehlermeldung weist Sie an, wie folgt vorzugehen: „Diagnostizieren und beheben Sie die Wiederherstellungsfehler, oder führen Sie eine Wiederherstellung von einer als fehlerfrei bekannten Sicherung aus.“ Sie können folglich versuchen, den aufgetretenen Fehler zu beheben, damit die Wiederherstellung abgeschlossen werden kann. (Weitere Informationen finden Sie unter [Behebbare Fehler und verzögerte Transaktionen](#correctable-errors-and-deferred-transactions).)

Wenn die Fehler nicht behoben werden können, ist die erste Wahl und beste Möglichkeit für die Behebung dieses Problems die Wiederherstellung über eine fehlerfreie Sicherung. Wenn Sie jedoch keine Wiederherstellung aus einer Sicherung durchführen können, haben Sie zwei weitere Möglichkeiten, die keine vollständige Datenwiederherstellung garantieren: Verwenden Sie die Notfallreparatur mit [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md), oder versuchen Sie, so viele Daten wie möglich in eine andere Datenbank zu kopieren. 

 1. Führen Sie eine Wiederherstellung über die letzte als fehlerfrei bekannte Datenbanksicherung durch.
 1. Verwenden Sie die von [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) bereitgestellte Notfallreparaturmethode.
 1. Versuchen Sie, so viele Daten wie möglich in eine andere Datenbank zu kopieren.

Die erste Methode, das Wiederherstellen über eine fehlerfreie Datenbanksicherung, ist die beste Wahl, um eine Datenbank auf einen bekannten und konsistenten Stand zu bringen.  

Wenn keine Sicherung verfügbar ist, ist die zweitbeste Option, die Datenbank online zu stellen und zugänglich zu machen. Beachten Sie jedoch, dass aufgrund des Wiederherstellungsfehlers keine Transaktionskonsistenz garantiert werden kann. Es gibt keine Möglichkeit, zu ermitteln, für welche Transaktionen ein Rollback oder Rollforward hätte ausgeführt werden sollen, die jedoch aufgrund des Wiederherstellungsfehlers nicht zugelassen wurden. Die Schritte zum Durchführen der Notfallreparatur werden im Abschnitt [Beheben von Fehlern im Datenbank-Notfallmodus](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md#resolving-errors-in-database-emergency-mode) in der DBCC CHECKDB-Dokumentation beschrieben. 

Wenn die Notfallreparatur nicht funktioniert und Sie versuchen möchten, einige der Daten in eine andere Datenbank zu retten, ist die beste Möglichkeit, auf die Datenbank zuzugreifen, das Versetzen dieser Datenbank in den Notfallmodus über den Befehl ALTER DATABASE <dbname> SET EMERGENCY. Anschließend können Sie versuchen, Daten aus Tabellen zu kopieren.

### <a name="correctable-errors-and-deferred-transactions"></a>Behebbare Fehler und verzögerte Transaktionen
Nicht alle Fehler, die bei der Datenbankwiederherstellung auftreten, führen zu einem Wiederherstellungsfehler und einer Datenbank mit dem Status SUSPECT:

Fehler beim erstmaligen Öffnen der Datenbank und/oder der Transaktionsprotokolldateien treten vor der Wiederherstellung auf. Beispiele für solche Fehler sind [17204](mssqlserver-17204-database-engine-error.md) und [17207](mssqlserver-17207-database-engine-error.md). Wenn diese Fehler behoben wurden, kann die Wiederherstellung fortgesetzt werden. (Es ist allerdings nicht sicher, dass diese auch abgeschlossen werden kann, wenn andere Wiederherstellungsfehler auftreten.) Die Fehler 17204 und 17207 führen nicht zu einer Datenbank mit dem Status SUSPECT. Wenn diese Probleme auftreten, ist der Status der Datenbank RECOVERY_PENDING. 

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht ein Abschließen der Wiederherstellung auch dann, wenn ein Fehler auf Seitenebene auftritt, und wahrt dennoch die Transaktionskonsistenz. Dieser Prozess hat die Anzahl von Szenarios verringert, die zu einer Datenbank mit dem Status SUSPECT führen. Dieses Konzept wird [verzögerte Transaktionen](../backup-restore/deferred-transactions-sql-server.md) genannt.

Wenn der bei der Wiederherstellung aufgetretene Fehler auf ein Problem mit einer Datenbankseite hinweist, z. B. ein Prüfsummenfehler oder die Meldung 824, kann die Wiederherstellung ohne Fehlerbehebung abgeschlossen werden. Wenn eine Transaktion nicht committet wurde, kann ein Fehler auf einer Seite zu einer [verzögerten Transaktion](../backup-restore/deferred-transactions-sql-server.md) führen, was ein Abschließen der Wiederherstellung ermöglicht.  

Die folgenden ERRORLOG-Einträge zeigen ein Beispiel für einen Fehler mit der Meldung [824](mssqlserver-824-database-engine-error.md), der bei der Wiederherstellung aufgetreten ist. Die Wiederherstellung konnte jedoch mit einer verzögerten Transaktion abgeschlossen werden. Beachten Sie, dass in diesem Fall der Fehler 3414 nicht aufgetreten ist, sowie die Meldung, dass die Wiederherstellung der Datenbank abgeschlossen wurde:

```2010-03-31 19:17:18.45 spid7s      Error: 824, Severity: 24, State: 2.   
2010-03-31 19:17:18.45 spid7s      SQL Server detected a logical consistency-based I/O error: incorrect checksum (expected: 0xb2c87a0a; actual: 0xb6c0a5e2). It occurred during a read of page (1:153) in database ID 13 at offset 0x00000000132000 in file 'C:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\DATA\mydb.mdf'.  Additional messages in the SQL Server error log or system event log may provide more detail. This is a severe error condition that threatens database integrity and must be corrected immediately. Complete a full database consistency check (DBCC CHECKDB). This error can be caused by many factors; for more information, see SQL Server Books Online.   
2010-03-31 19:17:18.45 spid7s      Error: 3314, Severity: 21, State: 1.   
2010-03-31 19:17:18.45 spid7s      During undoing of a logged operation in database 'mydb', an error occurred at log record ID (25:100:19). Typically, the specific failure is logged previously as an error in the Windows Event Log service. Restore the database or file from a backup, or repair the database.
2010-03-31 19:17:18.45 spid7s      Errors occurred during recovery while rolling back a transaction. The transaction was deferred. Restore the bad page or file, and re-run recovery.   
2010-03-31 19:17:18.45 spid7s      Recovery completed for database mydb (database ID 13) in 2 second(s) (analysis 204 ms, redo 25 ms, undo 1832 ms.) This is an informational message only. No user action is required.   
```

Wenn für eine committete Transaktion ein Rollforward ausgeführt werden soll, kann die Seite mit „Kein Zugriff“ gekennzeichnet werden (bei zukünftigen Versuchen, auf die Seite zuzugreifen, wird dann die Meldung 829 ausgegeben), und die Wiederherstellung kann abgeschlossen werden. In diesem Fall muss der Fehler behoben werden, indem die Seite aus einer Sicherung wiederhergestellt wird oder die Zuordnung der Seite mit DBCC CHECKDB mit Reparatur aufgehoben wird.


  
## <a name="see-also"></a>Weitere Informationen  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](~/relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)  
[Verzögerte Transaktionen](../backup-restore/deferred-transactions-sql-server.md)  
[MSSQLSERVER_824](~/relational-databases/errors-events/mssqlserver-824-database-engine-error.md)  
[sys.databases &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)

  
