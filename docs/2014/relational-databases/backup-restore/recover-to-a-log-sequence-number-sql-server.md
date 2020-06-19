---
title: Wiederherstellen zu einer Protokollfolgenummer (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4df55c3468fc009d86cffd58a837d6935f5ce14b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84957505"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a>Wiederherstellen zu einer Protokollfolgenummer (SQL Server)
  Dieses Thema ist nur für Datenbanken relevant, die das vollständige oder das massenprotokollierte Wiederherstellungsmodell verwenden.  
  
 Sie können eine Protokollfolgenummer (Log Sequence Number, LSN) zum Definieren des Wiederherstellungspunkts für einen Wiederherstellungsvorgang verwenden. Hierbei handelt es sich jedoch um eine auf Anbieter von Tools zugeschnittene Funktion, die nur in speziellen Fällen nutzbringend anzuwenden ist.  
  
##  <a name="overview-of-log-sequence-numbers"></a><a name="LSNs"></a> Übersicht der Protokollfolgenummern  
 Mit LSNs wird intern während einer RESTORE-Sequenz der Zeitpunkt nachverfolgt, bis zu dem Daten wiederhergestellt wurden. Wenn eine Sicherung wiederhergestellt wird, werden die Daten bis zu der LSN wiederhergestellt, die dem Zeitpunkt entspricht, an dem die Sicherung erstellt wurde. Durch differenzielle Sicherungen und Protokollsicherungen wird ein späterer Status der Datenbank wiederhergestellt, was wiederum einer höheren LSN entspricht.  
  
 Jeder Datensatz im Transaktionsprotokoll wird eindeutig durch eine Protokollfolgenummer (Log Sequence Number, LSN) identifiziert. LSNs halten sich an eine bestimmte Reihenfolge. Wenn LSN2 größer als LSN1 ist, erfolgte die durch den Protokolldatensatz von LSN2 beschriebene Änderung nach der durch den Protokolldatensatz von LSN1 beschriebenen Änderung.  
  
 Die LSN eines Protokolldatensatzes, bei dem ein wichtiges Ereignis aufgetreten ist, kann zum Erstellen richtiger Wiederherstellungssequenzen hilfreich sein. Da LSNs geordnet sind, können Sie auf Gleichheit und Ungleichheit (d. h., **\<**, **>** **=** ,) verglichen werden **\<=**, **>=** . Solche Vergleiche sind beim Erstellen von Wiederherstellungssequenzen hilfreich.  
  
> [!NOTE]  
>  LSNs sind Werte vom Datentyp `numeric`(25,0). Arithmetische Operationen (z. B. Addition oder Subtraktion) sind ohne Bedeutung und dürfen für LSNs nicht verwendet.  
  

  
## <a name="viewing-lsns-used-by-backup-and-restore"></a>Anzeigen von LSNs, die von der Sicherung und Wiederherstellung verwendet werden  
 Die LSN eines Protokolldatensatzes, bei dem ein bestimmtes Sicherungs- und Wiederherstellungsereignis aufgetreten ist, kann mithilfe der folgenden Methoden angezeigt werden:  
  
-   [backupset](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
-   [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql)  
  
-   [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql); [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
-   [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
> [!NOTE]  
>  LSNs werden auch in manchen Meldungstexten angezeigt.  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a>Transact-SQL-Syntax für die Wiederherstellung bis zu einer LSN  
 Mithilfe einer [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) -Anweisung können Sie an oder direkt vor der LSN stoppen, wie im Folgenden gezeigt:  
  
-   Verwenden Sie die WITH STOPATMARK **= '** LSN:_<lsn_number>_ **'** -Klausel, wobei LSN: *\<lsnNumber>* eine Zeichenfolge ist, die angibt, dass der Protokolldaten Satz mit der angegebenen LSN der Wiederherstellungspunkt ist.  
  
     Von STOPATMARK wird ein Rollforward zur LSN ausgeführt und dieser Protokolldatensatz im Rollforward eingeschlossen.  
  
-   Verwenden Sie die with STOPBEFOREMARK **= '** LSN:_<lsn_number>_ **'** -Klausel, wobei LSN: *\<lsnNumber>* eine Zeichenfolge ist, die angibt, dass der Protokolldaten Satz direkt vor dem Protokolldaten Satz, der die angegebene LSN-Nummer enthält, der Wiederherstellungspunkt ist.  
  
     Von STOPBEFOREMARK wird ein Rollforward bis zur LSN ausgeführt und dieser Protokolldatensatz aus dem Rollforward ausgeschlossen.  
  
 Typischerweise wird eine bestimmte Transaktion zum Einschließen oder Ausschließen ausgewählt. Praktisch handelt es sich bei dem angegebenen Protokolldatensatz um einen Transaktionscommitdatensatz, wobei diese Angabe nicht zwingend erforderlich ist.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird davon ausgegangen, dass die `AdventureWorks` -Datenbank so geändert wurde, dass das vollständige Wiederherstellungsmodell verwendet wird.  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
-   [Wiederherstellen einer Datenbank bis zum Fehlerzeitpunkt im vollständigen Wiederherstellungsmodell &#40;Transact-SQL&#41;](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Wiederherstellen einer Datenbank bis zu einer markierten Transaktion &#40;SQL Server Management Studio&#41;](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
