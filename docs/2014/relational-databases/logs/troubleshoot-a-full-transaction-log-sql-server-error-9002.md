---
title: Problembehandlung bei vollen Transaktionsprotokollen (SQL Server-Fehler 9002) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-transaction-log
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], full
- troubleshooting [SQL Server], full transaction log
- 9002 (Database Engine error)
- transaction logs [SQL Server], truncation
- backing up transaction logs [SQL Server], full logs
- transaction logs [SQL Server], full log
- full transaction logs [SQL Server]
ms.assetid: 0f23aa84-475d-40df-bed3-c923f8c1b520
caps.latest.revision: 54
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0adfc6e8f46a916244ddbaf81383ed8c3c169f1e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162253"
---
# <a name="troubleshoot-a-full-transaction-log-sql-server-error-9002"></a>Problembehandlung bei vollen Transaktionsprotokollen (SQL Server-Fehler 9002)
  In diesem Thema werden mögliche Lösungen für volle Transaktionsprotokolle erörtert und Vermeidungsstrategien vorgeschlagen. Wenn das Transaktionsprotokoll voll ist, wird von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] der Fehler 9002 ausgegeben. Das Protokoll kann sich füllen, wenn die Datenbank online ist oder wiederhergestellt wird. Wenn das Protokoll gefüllt wird, während die Datenbank online ist, bleibt die Datenbank online, sie kann aber nur gelesen und nicht aktualisiert werden. Wird das Protokoll während einer Wiederherstellung gefüllt, wird die Datenbank von [!INCLUDE[ssDE](../../includes/ssde-md.md)] als RESOURCE PENDING (ausstehende Ressource) markiert. In beiden Fällen ist eine Aktion seitens des Benutzers erforderlich, um Speicherplatz im Protokoll verfügbar zu machen.  
  
## <a name="responding-to-a-full-transaction-log"></a>Mögliche Vorgehensweisen bei einem vollen Transaktionsprotokoll  
 Die richtige Reaktion auf ein volles Transaktionsprotokoll hängt zum Teil davon ab, aufgrund welcher Bedingungen das Protokoll gefüllt wurde. Mithilfe der Spalten **log_reuse_wait** und **log_reuse_wait_desc** der **sys.database**-Katalogsicht können Sie feststellen, wodurch eine Protokollkürzung verhindert wurde. Weitere Informationen finden Sie unter [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql). Eine Beschreibung von Faktoren, die eine Protokollkürzung verzögern können, finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](the-transaction-log-sql-server.md).  
  
> [!IMPORTANT]  
>  Wenn die Datenbank im Wiederherstellungsmodus befand, wenn der Fehler 9002 nach Behebung des Problems, die Datenbank wiederherstellen, indem Sie mithilfe von ALTER DATABASE *Database_name* SET ONLINE.  
  
 Alternativ sind als Reaktion auf ein volles Transaktionsprotokoll auch folgende Aktionen möglich:  
  
-   Sichern des Protokolls.  
  
-   Freigeben von Speicherplatz, damit das Protokoll automatisch vergrößert werden kann.  
  
-   Verschieben der Protokolldatei auf einen Datenträger mit ausreichendem Speicherplatz.  
  
-   Vergrößern einer Protokolldatei.  
  
-   Hinzufügen einer Protokolldatei auf einem anderen Datenträger.  
  
-   Abschließen oder Abbrechen einer Transaktion mit langer Ausführungszeit.  
  
 Diese Alternativen werden in den folgenden Abschnitten erläutert. Wählen Sie diejenige Aktion aus, die sich am besten für Ihre Situation eignet.  
  
### <a name="backing-up-the-log"></a>Sichern des Protokolls  
 Falls bei Verwendung des vollständigen oder massenprotokollierten Wiederherstellungsmodells das Transaktionsprotokoll nicht vor kurzem gesichert wurde, kann durch die Sicherung eine Protokollkürzung verhindert werden. Wenn das Protokoll noch nie gesichert wurde, müssen Sie zwei protokollsicherungen erstellen die [!INCLUDE[ssDE](../../includes/ssde-md.md)] zum Abschneiden des Protokolls zum Zeitpunkt der letzten Sicherung. Durch Kürzen des Protokolls wird Speicherplatz für neue Protokolldatensätze freigegeben. Sichern Sie das Protokoll in kürzeren Abständen, damit es nicht wieder so schnell aufgefüllt wird.  
  
 **So erstellen Sie eine Transaktionsprotokollsicherung**  
  
> [!IMPORTANT]  
>  Wenn die Datenbank beschädigt ist, gehen Sie unter [Protokollfragmentsicherungen &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)  
  
### <a name="freeing-disk-space"></a>Freigeben von Speicherplatz  
 Möglicherweise können Sie durch Löschen oder Verschieben anderer Dateien Speicherplatz auf dem Datenträger freigeben, das die Transaktionsprotokolldatei für die Datenbank enthält. Aufgrund des freigegebenen Speicherplatzes kann die Protokolldatei dann durch den Wiederherstellungsmechanismus automatisch vergrößert werden.  
  
### <a name="moving-the-log-file-to-a-different-disk"></a>Verschieben der Protokolldatei auf einen anderen Datenträger  
 Wenn Sie auf dem Datenträger, auf dem die Protokolldatei aktuell gespeichert ist, nicht genügend Speicherplatz freigeben können, können Sie die Datei auf einen anderen Datenträger mit ausreichendem Speicherplatz verschieben.  
  
> [!IMPORTANT]  
>  Protokolldateien sollten unter keinen Umständen in komprimierten Dateisystemen gespeichert werden.  
  
 **So verschieben Sie eine Protokolldatei.**  
  
-   [Verschieben von Datenbankdateien](../databases/move-database-files.md)  
  
### <a name="increasing-the-size-of-a-log-file"></a>Vergrößern einer Protokolldatei  
 Wenn auf dem Protokolldatenträger Speicherplatz vorhanden ist, können Sie die Protokolldatei vergrößern. Die maximale Größe für Protokolldateien beträgt zwei Terabyte (TB) pro Protokolldatei.  
  
 **Um die Dateigröße zu erhöhen.**  
  
 Wenn die automatische Vergrößerung deaktiviert ist, die Datenbank online ist und auf dem Datenträger ausreichend Speicherplatz verfügbar ist, führen Sie einen der folgenden Schritte aus:  
  
-   Erhöhen Sie die Dateigröße manuell, um die Datei einmalig um einen bestimmten Wert zu vergrößern.  
  
-   Aktivieren Sie die automatische Vergrößerung, indem Sie mit der ALTER DATABASE-Anweisung für die Option FILEGROWTH ein Vergrößerungsinkrement ungleich Null festlegen.  
  
> [!NOTE]  
>  Erhöhen Sie in beiden Fällen den MAXSIZE-Wert, wenn die aktuelle Größenbeschränkung erreicht wurde.  
  
### <a name="adding-a-log-file-on-a-different-disk"></a>Hinzufügen einer Protokolldatei auf einem anderen Datenträger  
 Fügen Sie der Datenbank mithilfe von ALTER DATABASE <database_name> ADD LOG FILE eine neue Protokolldatei auf einem anderen Datenträger hinzu, auf dem ausreichend Speicherplatz vorhanden ist.  
  
 **So fügen Sie eine Protokolldatei hinzu**  
  
-   [Hinzufügen von Daten- oder Protokolldateien zu einer Datenbank](../databases/add-data-or-log-files-to-a-database.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [Verwalten der Größe der Transaktionsprotokolldatei](manage-the-size-of-the-transaction-log-file.md)   
 [Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md)   
 [sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql)  
  
  
