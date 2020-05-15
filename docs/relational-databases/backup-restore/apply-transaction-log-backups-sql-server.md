---
title: Anwenden von Transaktionsprotokollsicherungen (SQL Server) | Microsoft-Dokumentation
description: In diesem Artikel wird das Anwenden von Transaktionsprotokollsicherungen im Rahmen der Wiederherstellung einer SQL Server-Datenbank im vollständigen Wiederherstellungsmodell oder massenprotokollierten Wiederherstellungsmodell beschrieben.
ms.custom: ''
ms.date: 10/23/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], log backups
- transaction log backups [SQL Server], applying backups
- online restores [SQL Server], log backups
- transaction log backups [SQL Server], quantity needed for restore sequence
- backups [SQL Server], log backups
ms.assetid: 9b12be51-5469-46f9-8e86-e938e10aa3a1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f70156f5f725b10af712d0d5e898367715e46394
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834540"
---
# <a name="apply-transaction-log-backups-sql-server"></a>Anwenden von Transaktionsprotokollsicherungen (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dieses Thema ist nur für das vollständige und für das massenprotokollierte Wiederherstellungsmodell relevant.  
  
 In diesem Thema wird das Anwenden von Transaktionsprotokollsicherungen als Bestandteil der Wiederherstellung einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank erläutert.  
 
##  <a name="requirements-for-restoring-transaction-log-backups"></a><a name="Requirements"></a> Anforderungen zum Wiederherstellen von Transaktionsprotokollsicherungen  
 Für das Anwenden einer Transaktionsprotokollsicherung müssen folgende Voraussetzungen erfüllt sein:  
  
-   **Ausreichende Protokollsicherungen für eine Wiederherstellungssequenz:** Es müssen ausreichend Protokolldatensätze gesichert sein, damit eine Wiederherstellungssequenz abgeschlossen werden kann. Die erforderlichen Protokollsicherungen (einschließlich der [Sicherung des Protokollfragments](../../relational-databases/backup-restore/tail-log-backups-sql-server.md) , sofern erforderlich) müssen vor dem Start einer Wiederherstellungssequenz zur Verfügung stehen.  
  
-   **Richtige Wiederherstellungsreihenfolge:**  Als Erstes muss die unmittelbar vorherige vollständige oder differenzielle Datenbanksicherung wiederhergestellt werden. Alle nach dieser vollständigen oder differenziellen Datenbanksicherung erstellten Transaktionsprotokolle müssen dann in chronologischer Reihenfolge wiederhergestellt werden. Wenn eine Transaktionsprotokollsicherung in dieser Protokollkette verloren gegangen oder beschädigt ist, können Sie nur Transaktionsprotokolle vor dem fehlenden wiederherstellen.  
  
-   **Datenbank noch nicht wiederhergestellt:**  Die Datenbank kann erst wiederhergestellt werden, nachdem das letzte Transaktionsprotokoll angewendet wurde. Wenn Sie die Datenbank nach dem Wiederherstellen einer der Zwischen-Transaktionsprotokollsicherungen (einer Sicherung vor dem Ende der Protokollkette) wiederherstellen, können Sie die Datenbank nicht zu einem späteren Zeitpunkt als diesem wiederherstellen, ohne die gesamte Wiederherstellungssequenz, beginnend mit der vollständigen Datenbanksicherung, neu zu starten.  
  
    > [!TIP]
    > Eine bewährte Methode besteht darin, alle Protokollsicherungen wiederherzustellen (`RESTORE LOG *database_name* WITH NORECOVERY`). Nach dem Wiederherstellen der letzten Protokollsicherung stellen Sie die Datenbank in einem separaten Vorgang wieder her: (`RESTORE DATABASE *database_name* WITH RECOVERY`).  
  
##  <a name="recovery-and-transaction-logs"></a><a name="RecoveryAndTlogs"></a> Wiederherstellungs- und Transaktionsprotokolle  
 Wenn der Wiederherstellungsvorgang abgeschlossen und die Datenbank wiederhergestellt wurde, wird der Wiederherstellungsprozess ausgeführt, um die Integrität der Datenbank zu gewährleisten. Informationen zum Wiederherstellungsprozess finden Sie unter [ (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#TlogAndRecovery).
 
 Nach Abschluss des Wiederherstellungsprozesses wird die Datenbank online geschaltet, und es können keine weiteren Transaktionsprotokollsicherungen auf die Datenbank angewendet werden. So kann z. B. eine Reihe von Transaktionsprotokollsicherungen eine lang andauernde Transaktion enthalten. Der Start der Transaktion wird in der ersten Transaktionsprotokollsicherung, das Ende der Transaktion jedoch in der zweiten Transaktionsprotokollsicherung aufgezeichnet. Es gibt keinen Datensatz für einen Commit- oder Rollbackvorgang in der ersten Transaktionsprotokollsicherung. Wenn ein Wiederherstellungsvorgang nach dem Anwenden der ersten Transaktionsprotokollsicherung ausgeführt wird, wird die lang andauernde Transaktion als unvollständig behandelt, und für die in der ersten Transaktionsprotokollsicherung aufgezeichneten Datenänderungen dieser Transaktion wird ein Rollback ausgeführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist das Anwenden einer zweiten Transaktionsprotokollsicherung nach diesem Zeitpunkt nicht zulässig.  
  
> [!NOTE]
> Unter bestimmten Umständen können Sie eine Datei während der Protokollwiederherstellung explizit hinzufügen.  
  
##  <a name="use-log-backups-to-restore-to-the-failure-point"></a><a name="PITrestore"></a> Verwenden von Protokollsicherungen zum Wiederherstellen des Zustands vor dem Fehler  
 Nehmen Sie die folgende Ereignissequenz an.  
  
|Time|Ereignis|  
|----------|-----------|  
|8:00 Uhr|Sichern der Datenbank zum Erstellen einer vollständigen Datenbanksicherung.|  
|12:00 Uhr|Sichern des Transaktionsprotokolls.|  
|16:00 Uhr|Sichern des Transaktionsprotokolls.|  
|18:00 Uhr|Sichern der Datenbank zum Erstellen einer vollständigen Datenbanksicherung.|  
|20:00 Uhr|Sichern des Transaktionsprotokolls.|  
|21:45 Uhr|Fehler tritt auf.|  
  
> Eine Erklärung dieser Beispielsequenz von Sicherungen finden Sie unter [Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md).  
  
 Zum Wiederherstellen des Datenbankzustands von 21:45 Uhr (Zeitpunkt des Fehlers) kann eines der folgenden Verfahren verwendet werden:  

 **Alternative 1: Wiederherstellen der Datenbank mithilfe der letzten vollständigen Datenbanksicherung**  
  
1.  Erstellen Sie eine Sicherung des Protokollfragments des aktuell aktiven Transaktionsprotokolls zum Zeitpunkt des Fehlers.  
  
2.  Stellen Sie nicht die vollständige Datenbanksicherung von 8:00 Uhr von 18:00 Uhr. Stellen Sie stattdessen die neuere vollständige Datenbanksicherung von 18:00 Uhr wieder her, und wenden Sie dann die Transaktionsprotokollsicherung von 20:00 Uhr und die Sicherung des Protokollfragments an.  
  
 **Alternative 2: Wiederherstellen der Datenbank mithilfe einer früheren vollständigen Datenbanksicherung**  
  
> Dieser alternative Vorgang ist nützlich, wenn Sie aufgrund eines Problems die vollständige Datenbanksicherung von 18:00 Uhr von 18:00 Uhr. Dieser Vorgang dauert länger als das Wiederherstellen der vollständigen Datenbanksicherung von 18:00 Uhr.  
  
1.  Erstellen Sie eine Sicherung des Protokollfragments des aktuell aktiven Transaktionsprotokolls zum Zeitpunkt des Fehlers.  
  
2.  Stellen Sie die vollständige Datenbanksicherung von 8:00 Uhr und anschließend alle vier Transaktionsprotokollsicherungen in der chronologischen Reihenfolge wieder her. Dadurch wird ein Rollforward für alle abgeschlossenen Transaktionen bis 21:45 Uhr ausgeführt.  
  
     Diese Alternative verdeutlicht, welche redundante Sicherheit eine zwischen eine Folge vollständiger Datenbanksicherungen geschaltete Kette von Transaktionsprotokollsicherungen bietet.  
  
> In einigen Fällen können Sie auch mit Transaktionsprotokollen eine Datenbank zu einem bestimmten Zeitpunkt wiederherstellen. Informationen finden Sie unter [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)bezeichnet.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Related tasks  
 **So wenden Sie eine Transaktionsprotokollsicherung an**  
  
-   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
 **So stellen Sie einen Wiederherstellungspunkt wieder her**  
  
-   [Wiederherstellen einer Datenbank bis zum Fehlerzeitpunkt im vollständigen Wiederherstellungsmodell &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)  
  
-   [Wiederherstellen verwandter Datenbanken mit einer markierten Transaktion](../../relational-databases/backup-restore/recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [Wiederherstellen zu einer Protokollfolgenummer &#40;SQL Server&#41;](../../relational-databases/backup-restore/recover-to-a-log-sequence-number-sql-server.md)  
  
 **So stellen Sie eine Datenbank wieder her, nachdem Sie Sicherungen mit WITH NORECOVERY wiederhergestellt haben**  
  
-   [Wiederherstellen einer Datenbank ohne Wiederherstellung von Daten &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)     
 [Handbuch zur Architektur und Verwaltung von Transaktionsprotokollen in SQL Server](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md)      
  
