---
title: Sichern eines Transaktionsprotokolls | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie ein Transaktionsprotokoll in SQL Server mithilfe von SQL Server Management Studio, Transact-SQL oder PowerShell sichern.
ms.custom: ''
ms.date: 02/02/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction log backups [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- backing up transaction logs [SQL Server], SQL Server Management Studio
ms.assetid: 3426b5eb-6327-4c7f-88aa-37030be69fbf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c953e5a707bb197457d76e9d5d4f64635515ffce
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91807584"
---
# <a name="back-up-a-transaction-log"></a>Sichern eines Transaktionsprotokolls
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder PowerShell ein Transaktionsprotokoll sichern.  

## <a name="before-you-begin"></a>Vorbereitungen
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
Die `BACKUP`-Anweisung ist in einer expliziten oder [impliziten](../../t-sql/statements/set-implicit-transactions-transact-sql.md) Transaktion nicht zulässig. Eine explizite Transaktion ist eine Transaktion, in der Sie sowohl den Beginn als auch das Ende explizit definieren.

### <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
- Wenn eine Datenbank das vollständige oder das massenprotokollierte [Wiederherstellungsmodell](recovery-models-sql-server.md) verwendet, muss das Transaktionsprotokoll so oft gesichert werden, dass die Daten geschützt sind und das [Transaktionsprotokoll nicht aufgefüllt wird](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md). Dadurch wird das Protokoll gekürzt, und die Wiederherstellung der Datenbank zu einem bestimmten Zeitpunkt wird unterstützt. 
  
- Standardmäßig wird bei jedem erfolgreichen Sicherungsvorgang dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und dem Systemereignisprotokoll ein Eintrag hinzugefügt. Wenn Sie das Protokoll regelmäßig sichern, kann die Anzahl dieser Erfolgsmeldungen schnell ansteigen, d.h., es entstehen sehr große Fehlerprotokolle, die das Suchen nach anderen Meldungen erschweren können. In solchen Fällen können Sie diese Protokolleinträge mithilfe des Ablaufverfolgungsflags 3226 unterdrücken, wenn keines der Skripts von diesen Einträgen abhängig ist. Weitere Informationen hierzu finden Sie unter [Trace Flags &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   
  
### <a name="permissions"></a><a name="Permissions"></a> Berechtigungen

Die erforderlichen Berechtigungen `BACKUP DATABASE` und `BACKUP LOG` werden standardmäßig den Mitgliedern der festen Serverrolle **sysadmin** und den festen Datenbankrollen **db_owner** und **db_backupoperator** gewährt. Überprüfen Sie, ob die richtigen Berechtigungen vorliegen, bevor Sie beginnen.
  
 Besitz- und Berechtigungsprobleme im Zusammenhang mit der physischen Datei des Sicherungsmediums können den Sicherungsvorgang beeinträchtigen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss über Lese- und Schreibberechtigungen für das Medium verfügen. Das Konto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst ausgeführt wird, muss Schreibberechtigungen haben. Allerdings prüft die gespeicherte Prozedur [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md), die den Systemtabellen einen Eintrag für ein Sicherungsmedium hinzufügt, nicht die Dateizugriffsberechtigungen. Berechtigungsprobleme mit der physischen Datei des Sicherungsmediums werden möglicherweise erst sichtbar, wenn auf die [physische Ressource](backup-devices-sql-server.md) zugegriffen wird, um einen Sicherungs- oder Wiederherstellungsvorgang auszuführen. Daher überprüfen Sie erneut, ob die richtigen Berechtigungen vorliegen, bevor Sie beginnen.

## <a name="using-sql-server-management-studio"></a>Verwendung von SQL Server Management Studio

1. Stellen Sie eine Verbindung mit der entsprechenden Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und klicken Sie danach im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
1. Erweitern Sie **Datenbanken**, und wählen Sie je nach Datenbank eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken** , und wählen Sie eine Systemdatenbank aus.  
  
1. Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Tasks**, und klicken Sie dann auf **Sichern**. Das Dialogfeld **Datenbank sichern** wird angezeigt.  
 
1. Überprüfen Sie den Datenbanknamen im Listenfeld **Datenbank** . Sie können optional eine andere Datenbank aus der Liste auswählen.  
  
1. Überprüfen Sie, ob als Wiederherstellungsmodell entweder **FULL** oder **BULK_LOGGED**ausgewählt wurde.  
  
1. Wählen Sie im Listenfeld **Sicherungstyp** den Eintrag **Transaktionsprotokoll**aus.  
  
1. Wählen Sie (optional) **Nur Sicherung kopieren** aus, um eine Kopiesicherung zu erstellen. Eine *Kopiesicherung* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung, die unabhängig von der Sequenz von herkömmlichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen erstellt wird. Weitere Informationen hierzu finden Sie unter [Kopiesicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).   
  
    > [!NOTE]
    > Wenn die Option **Differenziell** aktiviert ist, können Sie keine Kopiesicherung erstellen.  
  
1. Akzeptieren Sie entweder den im Textfeld **Name** vorgeschlagenen Standardnamen für den Sicherungssatz, oder geben Sie einen anderen Namen für den Sicherungssatz ein.  
  
1. Geben Sie (optional) in das Textfeld **Beschreibung** eine Beschreibung des Sicherungssatzes ein.  
  
1. Geben Sie an, wann der Sicherungssatz ablaufen soll:  
  
    - Wenn der Sicherungssatz nach einer bestimmten Anzahl von Tagen ablaufen soll, klicken Sie auf **Nach** (die Standardoption), und geben Sie an, nach wie vielen Tagen der Sicherungssatz abläuft. Dieser Wert kann zwischen 0 und 99999 Tagen liegen. Ein Wert von 0 Tagen bedeutet, dass der Sicherungssatz nicht abläuft.  
  
         Der Standardwert wird im Dialogfeld **Servereigenschaften** (Seite **Datenbankeinstellungen** ) über die Option**Standardbeibehaltung für Sicherungsmedien (in Tagen)** festgelegt. Klicken Sie zum Zugreifen auf dieses Dialogfeld im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und wählen Sie „Eigenschaften“ aus. Wählen Sie anschließend die Seite **Datenbankeinstellungen** aus.  
  
    - Zum Speichern des Sicherungssatzes an einem bestimmten Datum klicken Sie auf **Am**. Geben Sie das Datum ein, an dem der Sicherungssatz abläuft.  
  
1. Wählen Sie den Sicherungszieltyp aus, indem Sie auf **Datenträger**, **URL** oder **Band**klicken. Klicken Sie auf **Hinzufügen**, um die Pfade von bis zu 64 Datenträgern oder Bandlaufwerken, die einen einzelnen Mediensatz enthalten, auszuwählen. Die ausgewählten Pfade werden im Listenfeld **Sichern auf** angezeigt.  
  
     Um einen Sicherungsziel zu entfernen, wählen Sie ihn aus, und klicken Sie auf **Entfernen**. Zum Anzeigen des Inhalts eines Sicherungsziels wählen Sie es aus, und klicken Sie auf **Inhalt**.  
  
1. Zum Anzeigen oder Auswählen der erweiterten Optionen klicken Sie auf **Optionen** im Bereich **Seite auswählen** .  
  
1. Wählen Sie eine Option von **Medium überschreiben** aus, indem Sie auf eine der folgenden Optionen klicken:  
  
    - **Auf vorhandenen Mediensatz sichern**  
  
         Klicken Sie bei dieser Option entweder auf **An vorhandenen Sicherungssatz anfügen** oder auf **Alle vorhandenen Sicherungssätze überschreiben**. Weitere Informationen hierzu finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md).  
  
         - Aktivieren Sie (optional) das Kontrollkästchen **Mediensatznamen und Ablaufzeit des Sicherungssatzes überprüfen**, damit beim Sicherungsvorgang das Datum und die Uhrzeit überprüft werden, an dem bzw. zu der der Mediensatz und der Sicherungssatz ablaufen.  
  
         - Geben Sie (optional) einen Namen in das Textfeld **Mediensatzname** ein. Wenn kein Name angegeben wurde, wird ein Mediensatz mit leerem Namen erstellt. Wenn Sie einen Mediensatznamen angeben, wird überprüft, ob der tatsächliche Name des Mediums (Band oder Datenträger) mit dem eingegebenen Namen übereinstimmt.  
  
         Wenn Sie den Mediennamen leer lassen und das Kontrollkästchen aktivieren, um ihn anhand des Mediums zu überprüfen, ist die Prüfung erfolgreich, wenn der Medienname auf dem Medium ebenfalls leer ist.  
  
    - **Auf neuen Mediensatz sichern und alle vorhandenen Sicherungssätze löschen**  
  
         Geben Sie bei dieser Option einen Namen in das Textfeld **Name für neuen Mediensatz** und optional eine Beschreibung des Mediensatzes in das Textfeld **Beschreibung für neuen Mediensatz** ein. Weitere Informationen finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md).   
  
1. Im Bereich **Zuverlässigkeit** können Sie folgende Optionen aktivieren:  
  
    - **Sicherung nach dem Abschluss überprüfen**.  
  
    - **Vor dem Schreiben auf die Medien Prüfsumme bilden**, und optional **Continue on checksum error** (bei Prüfsummenfehler fortsetzen).
    
       Weitere Informationen finden Sie unter [Mögliche Medienfehler während der Sicherung und Wiederherstellung &#40;SQL Server&#41;](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md).  
  
1. Gehen Sie unter **Transaktionsprotokoll** wie folgt vor:  
  
    - Bei normalen Protokollsicherungen behalten Sie die Standardauswahl bei, also **Transaktionsprotokoll durch Entfernen inaktiver Einträge abschneiden**.  
  
    - Soll das Protokollfragment gesichert werden (das aktive Protokoll), aktivieren Sie **Protokollfragment sichern und Datenbank im Wiederherstellungsstatus belassen**.  
  
         Eine Protokollfragmentsicherung wird angefertigt, wenn das Protokollfragment nicht gesichert werden konnte, um so einen Datenverlust zu vermeiden. Sichern Sie das aktive Protokoll (Protokollfragmentsicherung) jeweils nach einem Fehler, vor dem Wiederherstellen der Datenbank oder beim Failover auf eine sekundäre Datenbank. Wenn Sie diese Option auswählen, entspricht dies der Option NORECOVERY in der BACKUP LOG-Anweisung von Transact-SQL.
         
         Weitere Informationen zu Sicherungen des Protokollfragments finden Sie unter [Protokollfragmentsicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).  
  
1. Wenn Sie auf ein Bandlaufwerk sichern (gemäß der Konfiguration im Abschnitt **Ziel** der Seite **Allgemein** ), ist die Option **Band nach dem Sichern entladen** aktiviert. Wenn Sie auf diese Option klicken, wird die Option **Band vor dem Entladen zurückspulen** aktiviert.  
  
1. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] und höheren Versionen wird die [Sicherungskomprimierung](../../relational-databases/backup-restore/backup-compression-sql-server.md). Ob eine Sicherung standardmäßig komprimiert wird, ist abhängig vom Wert der Serverkonfigurationsoption **backup-compression default** . Sie können jedoch unabhängig von der aktuellen Standardeinstellung auf Serverebene eine Sicherung komprimieren, indem Sie die Option **Sicherung komprimieren**aktivieren, oder die Komprimierung verhindern, indem Sie die Option **Sicherung nicht komprimieren**aktivieren.  
  
     Zur Ansicht der Standardeinstellung für die Sicherungskomprimierung gelangen Sie unter [Anzeigen oder Konfigurieren der Serverkonfigurationsoption](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).
  
     Um die Sicherungsdatei zu verschlüsseln, aktivieren Sie das Kontrollkästchen **Sicherung verschlüsseln** . Wählen Sie einen Verschlüsselungsalgorithmus aus, der zum Verschlüsseln der Sicherungsdatei verwendet werden soll, und geben Sie ein Zertifikat oder einen asymmetrischen Schlüssel an. Folgende Algorithmen stehen für die Verschlüsselung zur Verfügung:  
  
   - AES 128  
  
   - AES 192  
  
   - AES 256  
  
   - Triple DES  

## <a name="using-transact-sql"></a>Verwenden von Transact-SQL  
  
Führen Sie die BACKUP LOG-Anweisung aus, um das Transaktionsprotokoll zu sichern, und geben Sie dabei Folgendes an:  
  
- Den Namen der Datenbank, zu der das zu sichernde Transaktionsprotokoll gehört.  
  
- Das Sicherungsmedium, auf das die Transaktionsprotokollsicherung geschrieben wird.  
  
> [!IMPORTANT]
> In diesem Beispiel wird die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank verwendet, in der das einfache Wiederherstellungsmodell eingesetzt wird. Um Protokollsicherungen zu ermöglichen, wurde für die Datenbank vor dem Erstellen einer vollständigen Datenbanksicherung die Verwendung des vollständigen Wiederherstellungsmodells festgelegt.
>
> Weitere Informationen finden Sie unter [Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
 In diesem Beispiel wird eine Transaktionsprotokollsicherung für die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank auf dem zuvor erstellten, benannten Sicherungsmedium `MyAdvWorks_FullRM_log1`erstellt.  
  
```sql  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell

Richten Sie den [SQL Server PowerShell-Anbieter ein](../../powershell/sql-server-powershell-provider.md), und verwenden Sie ihn. Verwenden Sie das Cmdlet **Backup-SqlDatabase** , und geben Sie **Log** als Wert für den Parameter **-BackupAction** an.  
  
Im folgenden Beispiel wird eine Protokollsicherung der `<myDatabase>` -Datenbank am standardmäßigen Sicherungsspeicherort der Serverinstanz `Computer\Instance`erstellt.  
  
```powershell
Backup-SqlDatabase -ServerInstance Computer\Instance -Database <myDatabase> -BackupAction Log  
```
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Related tasks  
  
- [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
- [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
- [Problembehandlung bei vollen Transaktionsprotokollen &#40;SQL Server-Fehler 9002&#41;](../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a>Weitere Informationen

 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Vollständige Dateisicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-file-backups-sql-server.md)