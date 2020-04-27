---
title: Transaktionsprotokollsicherungen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], transaction logs
- transaction log backups [SQL Server], creating
- log backups [SQL Server[
- transaction log backups [SQL Server], sequencing
ms.assetid: f4a44a35-0f44-4a42-91d5-d73ac658a3b0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6dc94409e607c91944a2263ac5dfb3e8a3f4ce54
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62920689"
---
# <a name="transaction-log-backups-sql-server"></a>Transaktionsprotokollsicherungen (SQL Server)
  Dieses Thema ist nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken relevant, die das vollständige oder das massenprotokollierte Wiederherstellungsmodell verwenden. In diesem Thema wird das Sichern des Transaktionsprotokolls einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank erläutert.  
  
 Vor dem Erstellen von Protokollsicherungen muss bereits mindestens eine vollständige Sicherung durchgeführt worden sein. Danach kann das Transaktionsprotokoll jederzeit gesichert werden, es sei denn, das Protokoll wurde gerade gesichert. Es empfiehlt sich, Protokollsicherungen häufig auszuführen, damit auf diese Weise die Gefahr von Datenverlusten verringert und das Abschneiden des Transaktionsprotokolls angewendet werden kann. In der Regel erstellt ein Datenbankadministrator von Zeit zu Zeit eine vollständige Datenbanksicherung, z. B. einmal pro Woche, sowie optional in kürzeren Abständen eine Reihe von differenziellen Datenbanksicherungen, z. B. täglich. Unabhängig von den Datenbanksicherungen sichert der Datenbankadministrator das Transaktionsprotokoll sehr häufig, z. B. alle 10 Minuten. Der optimale Abstand zwischen Sicherungen ist abhängig von Faktoren wie der Wichtigkeit der Daten, der Größe der Datenbank und der Arbeitsauslastung des Servers.  
  
 **In diesem Thema:**  
  
-   [Funktionsweise einer Protokollsicherungssequenz](#LogBackupSequence)  
  
-   [Empfehlungen](#Recommendations)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="how-a-sequence-of-log-backups-works"></a><a name="LogBackupSequence"></a>Funktionsweise einer Sequenz von Protokoll Sicherungen  
 Die Sequenz der Transaktionsprotokollsicherungen ( *Protokollkette* ) ist unabhängig von den Datensicherungen. Stellen Sie sich z. B. folgende Ereignissequenz vor.  
  
|Zeit|Ereignis|  
|----------|-----------|  
|8:00 Uhr|Sichern der Datenbank.|  
|12:00 Uhr|Sichern des Transaktionsprotokolls.|  
|16:00 Uhr|Sichern des Transaktionsprotokolls.|  
|18:00 Uhr|Sichern der Datenbank.|  
|20:00 Uhr|Sichern des Transaktionsprotokolls.|  
  
 Die um 20:00 Uhr erstellte Sicherung des Transaktionsprotokolls enthält Transaktionsprotokoll-Datensätze von 16:00 Uhr bis 20:00 Uhr, wobei der Zeitpunkt eingeschlossen ist, zu dem um 18:00 Uhr die vollständige Sicherung der Datenbank erstellt wurde. Die Sequenz der Transaktionsprotokollsicherungen reicht ohne Unterbrechung von der um 08:00 Uhr erstellten ersten vollständigen Datenbanksicherung bis zur letzten Sicherung des Transaktionsprotokolls um 20:00 Uhr. Informationen zum Anwenden dieser Protokollsicherungen finden Sie im Beispiel unter [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Wenn ein Transaktionsprotokoll beschädigt wird, gehen die Änderungen seit der letzten gültigen Sicherung verloren. Daher empfehlen wir dringend, Protokolldateien auf einem fehlertoleranten Datenträger zu speichern.  
  
-   Wenn eine Datenbank beschädigt ist oder in Kürze wiederhergestellt werden soll, ist es ratsam, eine [Sicherung des Protokollfragments](tail-log-backups-sql-server.md) zu erstellen, damit Sie den aktuellen Stand der Datenbank wiederherstellen können.  
  
-   Standardmäßig wird bei jedem erfolgreichen Sicherungsvorgang dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und dem Systemereignisprotokoll ein Eintrag hinzugefügt. Wenn Sie das Protokoll regelmäßig sichern, kann die Anzahl dieser Erfolgsmeldungen schnell ansteigen, d. h., es entstehen sehr große Fehlerprotokolle, die das Suchen nach anderen Meldungen erschweren können. In solchen Fällen können Sie diese Protokolleinträge mithilfe des Ablaufverfolgungsflags 3226 unterdrücken, wenn keines der Skripts von diesen Einträgen abhängig ist. Weitere Informationen finden Sie unter [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So erstellen Sie eine Transaktionsprotokollsicherung**  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)  
  
 Informationen zum Planen von Sicherungsaufträgen finden Sie unter [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
 Keine.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)   
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](back-up-and-restore-of-sql-server-databases.md)   
 [Protokollfragmentsicherungen &#40;SQL Server&#41;](tail-log-backups-sql-server.md)   
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)  
  
  
