---
title: Anwenden von Transaktionsprotokollsicherungen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7532f2a6f2c50f53e5af01c2cec979170b493147
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62922932"
---
# <a name="apply-transaction-log-backups-sql-server"></a>Anwenden von Transaktionsprotokollsicherungen (SQL Server)
  Dieses Thema ist nur für das vollständige und für das massenprotokollierte Wiederherstellungsmodell relevant.  
  
 In diesem Thema wird das Anwenden von Transaktionsprotokollsicherungen als Bestandteil der Wiederherstellung einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank erläutert.  
  
 **In diesem Thema:**  
  
-   [Anforderungen für die Wiederherstellung von Transaktionsprotokoll Sicherungen](#Requirements)  
  
-   [Wiederherstellungs-und Transaktionsprotokolle](#RecoveryAndTlogs)  
  
-   [Verwenden von Protokollsicherungen zum Wiederherstellen des Zustands vor dem Fehler](#PITrestore)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="Requirements"></a>Anforderungen für die Wiederherstellung von Transaktionsprotokoll Sicherungen  
 Für das Anwenden einer Transaktionsprotokollsicherung müssen folgende Voraussetzungen erfüllt sein:  
  
-   **Ausreichende Protokollsicherungen für eine Wiederherstellungssequenz:** Es müssen ausreichend Protokolldatensätze gesichert sein, damit eine Wiederherstellungssequenz abgeschlossen werden kann. Die erforderlichen Protokollsicherungen (einschließlich der [Sicherung des Protokollfragments](tail-log-backups-sql-server.md) , sofern erforderlich) müssen vor dem Start einer Wiederherstellungssequenz zur Verfügung stehen.  
  
-   **Richtige Wiederherstellungsreihenfolge:**  Als Erstes muss die unmittelbar vorherige vollständige oder differenzielle Datenbanksicherung wiederhergestellt werden. Alle nach dieser vollständigen oder differenziellen Datenbanksicherung erstellten Transaktionsprotokolle müssen dann in chronologischer Reihenfolge wiederhergestellt werden. Wenn eine Transaktionsprotokollsicherung in dieser Protokollkette verloren gegangen oder beschädigt ist, können Sie nur Transaktionsprotokolle vor dem fehlenden wiederherstellen.  
  
-   **Noch nicht wiederhergestellte Datenbank:**  Die Datenbank kann erst wiederhergestellt werden, nachdem das letzte Transaktionsprotokoll angewendet wurde. Wenn Sie die Datenbank nach dem Wiederherstellen einer der Zwischen-Transaktionsprotokollsicherungen (einer Sicherung vor dem Ende der Protokollkette) wiederherstellen, können Sie die Datenbank nicht zu einem späteren Zeitpunkt als diesem wiederherstellen, ohne die gesamte Wiederherstellungssequenz, beginnend mit der vollständigen Datenbanksicherung, neu zu starten.  
  
    > [!TIP]  
    >  Eine bewährte Methode besteht darin, alle Protokollsicherungen (RESTORE LOG *Datenbankname* WITH NORECOVERY) wiederherzustellen. Stellen Sie nach dem Wiederherstellen der letzten Protokollsicherung die Datenbank in einem separaten Vorgang (RESTORE DATABASE *Datenbankname* WITH RECOVERY) wieder her.  
  
##  <a name="RecoveryAndTlogs"></a>Wiederherstellungs-und Transaktionsprotokolle  
 Wenn Sie den Wiederherstellungsvorgang abschließen und die Datenbank wiederherstellen, wird während der Wiederherstellung für alle unvollständigen Transaktionen ein Rollback ausgeführt. Dies wird als *Rollbackphase*bezeichnet. Das Rollback ist erforderlich, um die Integrität der Datenbank wiederherzustellen. Nach dem Rollback wird die Datenbank online geschaltet, und es können keine weiteren Transaktionsprotokollsicherungen auf die Datenbank angewendet werden.  
  
 So kann z. B. eine Reihe von Transaktionsprotokollsicherungen eine lang andauernde Transaktion enthalten. Der Start der Transaktion wird in der ersten Transaktionsprotokollsicherung, das Ende der Transaktion jedoch in der zweiten Transaktionsprotokollsicherung aufgezeichnet. Es gibt keinen Datensatz für einen Commit- oder Rollbackvorgang in der ersten Transaktionsprotokollsicherung. Wenn ein Wiederherstellungsvorgang nach dem Anwenden der ersten Transaktionsprotokollsicherung ausgeführt wird, wird die lang andauernde Transaktion als unvollständig behandelt, und für die in der ersten Transaktionsprotokollsicherung aufgezeichneten Datenänderungen dieser Transaktion wird ein Rollback ausgeführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist das Anwenden einer zweiten Transaktionsprotokollsicherung nach diesem Zeitpunkt nicht zulässig.  
  
> [!NOTE]  
>  Unter bestimmten Umständen können Sie eine Datei während der Protokollwiederherstellung explizit hinzufügen.  
  
##  <a name="PITrestore"></a>Verwenden von Protokoll Sicherungen zur Wiederherstellung bis zum Zeitpunkt des Fehlers  
 Nehmen Sie die folgende Ereignissequenz an.  
  
|Time|Ereignis|  
|----------|-----------|  
|8:00 Uhr|Sichern der Datenbank zum Erstellen einer vollständigen Datenbanksicherung.|  
|12:00 Uhr|Sichern des Transaktionsprotokolls.|  
|16:00 Uhr|Sichern des Transaktionsprotokolls.|  
|18:00 Uhr|Sichern der Datenbank zum Erstellen einer vollständigen Datenbanksicherung.|  
|20:00 Uhr|Sichern des Transaktionsprotokolls.|  
|21:45 Uhr|Fehler tritt auf.|  
  
> [!NOTE]  
>  Eine Erklärung dieser Beispielsequenz von Sicherungen finden Sie unter [Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).  
  
 Zum Wiederherstellen des Datenbankzustands von 21:45 Uhr (Zeitpunkt des Fehlers) kann eines der folgenden Verfahren verwendet werden:  
  
 **Alternative 1: Wiederherstellen der Datenbank mithilfe der letzten vollständigen Datenbanksicherung**  
  
1.  Erstellen Sie eine Sicherung des Protokollfragments des aktuell aktiven Transaktionsprotokolls zum Zeitpunkt des Fehlers.  
  
2.  Stellen Sie nicht die vollständige Datenbanksicherung von 8:00 Uhr von 18:00 Uhr. Stellen Sie stattdessen die neuere vollständige Datenbanksicherung von 18:00 Uhr wieder her, und wenden Sie dann die Transaktionsprotokollsicherung von 20:00 Uhr und die Sicherung des Protokollfragments an.  
  
 **Alternative 2: Wiederherstellen der Datenbank mithilfe einer früheren vollständigen Datenbanksicherung**  
  
> [!NOTE]  
>  Dieser alternative Vorgang ist nützlich, wenn Sie aufgrund eines Problems die vollständige Datenbanksicherung von 18:00 Uhr von 18:00 Uhr. Dieser Vorgang dauert länger als das Wiederherstellen der vollständigen Datenbanksicherung von 18:00 Uhr.  
  
1.  Erstellen Sie eine Sicherung des Protokollfragments des aktuell aktiven Transaktionsprotokolls zum Zeitpunkt des Fehlers.  
  
2.  Stellen Sie die vollständige Datenbanksicherung von 8:00 Uhr und anschließend alle vier Transaktionsprotokollsicherungen in der chronologischen Reihenfolge wieder her. Dadurch wird ein Rollforward für alle abgeschlossenen Transaktionen bis 21:45 Uhr ausgeführt.  
  
     Diese Alternative verdeutlicht, welche redundante Sicherheit eine zwischen eine Folge vollständiger Datenbanksicherungen geschaltete Kette von Transaktionsprotokollsicherungen bietet.  
  
> [!NOTE]  
>  In einigen Fällen können Sie auch mit Transaktionsprotokollen eine Datenbank zu einem bestimmten Zeitpunkt wiederherstellen. Informationen finden Sie unter [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)bezeichnet.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So wenden Sie eine Transaktionsprotokollsicherung an**  
  
-   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
 **So stellen Sie einen Wiederherstellungspunkt wieder her**  
  
-   [Wiederherstellen einer Datenbank bis zum Fehlerzeitpunkt im vollständigen Wiederherstellungsmodell &#40;Transact-SQL&#41;](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)  
  
-   [Wiederherstellen verwandter Datenbanken mit einer markierten Transaktion](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [Wiederherstellen zu einer Protokollfolgenummer &#40;SQL Server&#41;](recover-to-a-log-sequence-number-sql-server.md)  
  
 **So stellen Sie eine Datenbank wieder her, nachdem Sie Sicherungen mit WITH NORECOVERY wiederhergestellt haben**  
  
-   [Wiederherstellen einer Datenbank ohne Wiederherstellung von Daten &#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)  
  
  
