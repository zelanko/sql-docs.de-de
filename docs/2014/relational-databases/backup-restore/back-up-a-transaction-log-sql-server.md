---
title: Sichern eines Transaktionsprotokolls (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 78472cf0a270ffbb83ddf744956e7d2c5a1a1f64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783122"
---
# <a name="back-up-a-transaction-log-sql-server"></a>Sichern eines Transaktionsprotokolls (SQL Server)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder PowerShell ein Transaktionsprotokoll sichern.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Sicherheit](#Security)  
  
-   **Sichern eines Transaktionsprotokolls mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  Alternativ können Sie den[Wartungsplanungs-Assistenten](../maintenance-plans/use-the-maintenance-plan-wizard.md)zum Erstellen von Sicherungen verwenden.  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die BACKUP-Anweisung ist nicht in einer expliziten oder implizierten Transaktion zulässig.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Wenn eine Datenbank das vollständige oder das massenprotokollierte Wiederherstellungsmodell verwendet, muss das Transaktionsprotokoll so oft gesichert werden, dass die Daten geschützt sind und das Transaktionsprotokoll nicht aufgefüllt wird. Dadurch wird das Protokoll gekürzt, und die Wiederherstellung der Datenbank zu einem bestimmten Zeitpunkt wird unterstützt.  
  
-   Standardmäßig wird bei jedem erfolgreichen Sicherungsvorgang dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und dem Systemereignisprotokoll ein Eintrag hinzugefügt. Wenn Sie das Protokoll regelmäßig sichern, kann die Anzahl dieser Erfolgsmeldungen schnell ansteigen, d. h., es entstehen sehr große Fehlerprotokolle, die das Suchen nach anderen Meldungen erschweren können. In solchen Fällen können Sie diese Protokolleinträge mithilfe des Ablaufverfolgungsflags 3226 unterdrücken, wenn keines der Skripts von diesen Einträgen abhängig ist. Weitere Informationen finden Sie unter [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Mitglieder der festen Serverrolle **sysadmin** und der festen Datenbankrollen **db_owner** und **db_backupoperator** verfügen standardmäßig über BACKUP DATABASE- und BACKUP LOG-Berechtigungen.  
  
 Besitz- und Berechtigungsprobleme im Zusammenhang mit der physischen Datei des Sicherungsmediums können den Sicherungsvorgang beeinträchtigen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss über Lese- und Schreibberechtigungen für das Medium verfügen. Das Konto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst ausgeführt wird, muss Schreibberechtigungen haben. Allerdings prüft die gespeicherte Prozedur [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), die den Systemtabellen einen Eintrag für ein Sicherungsmedium hinzufügt, nicht die Dateizugriffsberechtigungen. Solche Probleme mit der physischen Datei des Sicherungsmediums treten möglicherweise erst auf, wenn auf die physische Ressource zugegriffen wird, um einen Sicherungs- oder Wiederherstellungsvorgang auszuführen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-back-up-a-transaction-log"></a>So sichern Sie ein Transaktionsprotokoll  
  
1.  Stellen Sie eine Verbindung mit der entsprechenden Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und klicken Sie danach im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie je nach Datenbank eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken** , und wählen Sie eine Systemdatenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Aufgaben**, und klicken Sie dann auf **Sichern**. Das Dialogfeld **Datenbank sichern** wird angezeigt.  
  
4.  Überprüfen Sie den Datenbanknamen im Listenfeld **Datenbank** . Sie können optional eine andere Datenbank aus der Liste auswählen.  
  
5.  Überprüfen Sie, ob als Wiederherstellungsmodell entweder **FULL** oder **BULK_LOGGED**ausgewählt wurde.  
  
6.  Wählen Sie im Listenfeld **Sicherungstyp** den Eintrag **Transaktionsprotokoll**aus.  
  
7.  Sie können optional auch **Kopiesicherung** auswählen, um eine Kopiesicherung zu erstellen. Eine *Kopiesicherung* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherung, die unabhängig von der Sequenz von herkömmlichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen erstellt wird. Weitere Informationen finden Sie unter [Kopiesicherungen &#40;SQL Server&#41;](copy-only-backups-sql-server.md).  
  
    > [!NOTE]  
    >  Wenn die Option **Differenziell** aktiviert ist, können Sie keine Kopiesicherung erstellen.  
  
8.  Übernehmen Sie entweder den vorgeschlagenen Standardnamen für den Sicherungssatz im Textfeld **Name**, oder geben Sie einen anderen Namen für den Sicherungssatz ein.  
  
9. Geben Sie ggf. im Textfeld **Beschreibung** eine Beschreibung des Sicherungssatzes ein.  
  
10. Geben Sie an, wann der Sicherungssatz ablaufen soll:  
  
    -   Wenn der Sicherungssatz nach einer bestimmten Anzahl von Tagen ablaufen soll, klicken Sie auf **Nach** (Standardoption), und geben Sie die Anzahl von Tagen nach der Erstellung ein, nach der der Satz abläuft. Dieser Wert kann zwischen 0 und 99999 Tagen liegen. Ein Wert von 0 Tagen bedeutet, dass der Sicherungssatz nicht abläuft.  
  
         Der Standardwert wird in der Option **Standard Beibehaltungs Dauer für Sicherungsmedien (in Tagen)** des Dialog Felds **Server Eigenschaften** (Seite**Datenbankeinstellungen** ) festgelegt. Klicken Sie zum Zugreifen auf dieses Dialogfeld im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und wählen Sie „Eigenschaften“ aus. Wählen Sie anschließend die Seite **Datenbankeinstellungen** aus.  
  
    -   Wenn der Sicherungssatz an einem bestimmten Datum ablaufen soll, klicken Sie auf **Am** auf, und geben Sie das Datum ein, an dem der Satz abläuft.  
  
11. Wählen Sie den Sicherungszieltyp aus, indem Sie auf **Datenträger**, **URL** oder **Band**klicken. Klicken Sie auf **Hinzufügen**, um die Pfade von bis zu 64 Datenträgern oder Bandlaufwerken, die einen einzelnen Mediensatz enthalten, auszuwählen. Die ausgewählten Pfade werden im Listenfeld **Sichern auf** angezeigt.  
  
     Um einen Sicherungsziel zu entfernen, wählen Sie ihn aus, und klicken Sie auf **Entfernen**. Zum Anzeigen des Inhalts eines Sicherungsziels wählen Sie es aus, und klicken Sie auf **Inhalt**.  
  
12. Klicken Sie im Bereich **Seite auswählen** auf **Optionen**, um die erweiterten Optionen anzuzeigen oder auszuwählen.  
  
13. Klicken Sie auf eine der folgenden Optionen, um eine Einstellung für **Medium überschreiben** auszuwählen:  
  
    -   **Auf vorhandenen Medien Satz sichern**  
  
         Klicken Sie für diese Option auf **An vorhandenen Sicherungssatz anfügen** oder **Alle vorhandenen Sicherungssätze überschreiben**. Weitere Informationen finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md):  
  
         Sie können bei Bedarf das Kontrollkästchen **Mediensatznamen und Ablaufzeit des Sicherungssatzes überprüfen** aktivieren, damit beim Sicherungsvorgang das Datum und die Uhrzeit überprüft werden, an dem bzw. zu der der Mediensatz und der Sicherungssatz ablaufen.  
  
         Geben Sie optional einen Namen im Textfeld **Mediensatzname** ein. Wenn kein Name angegeben wurde, wird ein Mediensatz mit leerem Namen erstellt. Wenn Sie einen Mediensatznamen angeben, wird überprüft, ob der tatsächliche Name des Mediums (Band oder Datenträger) mit dem eingegebenen Namen übereinstimmt.  
  
         Wenn Sie den Mediennamen leer lassen und das Kontrollkästchen aktivieren, um ihn anhand des Mediums zu überprüfen, ist die Prüfung erfolgreich, wenn der Medienname auf dem Medium ebenfalls leer ist.  
  
    -   **Auf neuen Medien Satz sichern und alle vorhandenen Sicherungs Sätze löschen**  
  
         Geben Sie für diese Option einen Namen in das Textfeld **Name für neuen Mediensatz** und optional eine Beschreibung des Mediensatzes in das Textfeld **Beschreibung für neuen Mediensatz** ein. Weitere Informationen finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md):  
  
14. Aktivieren Sie im Abschnitt **Zuverlässigkeit** optional Folgendes:  
  
    -   **Sicherung nach dem Abschluss überprüfen**.  
  
    -   **Vor dem Schreiben auf die Medien Prüfsumme ausführen**und optional **den Prüfsummen Fehler fortsetzen**. Weitere Informationen finden Sie unter [Mögliche Medienfehler während der Sicherung und Wiederherstellung &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).  
  
15. Gehen Sie unter **Transaktionsprotokoll** wie folgt vor:  
  
    -   Bei normalen Protokollsicherungen behalten Sie die Standardauswahl bei, also **Transaktionsprotokoll durch Entfernen inaktiver Einträge abschneiden**.  
  
    -   Soll das Protokollfragment gesichert werden (also das aktive Protokoll), aktivieren Sie die Option **Protokollfragment sichern und Datenbank im Wiederherstellungsstatus belassen**.  
  
         Eine Protokollfragmentsicherung wird angefertigt, wenn das Protokollfragment nicht gesichert werden konnte, um so einen Datenverlust zu vermeiden. Sichern Sie das aktive Protokoll (Protokollfragmentsicherung) jeweils nach einem Fehler, vor dem Wiederherstellen der Datenbank oder beim Failover auf eine sekundäre Datenbank. Wenn Sie diese Option auswählen, entspricht dies der Option NORECOVERY in der BACKUP LOG-Anweisung von Transact-SQL. Weitere Informationen zu Sicherungen des Protokollfragments finden Sie unter [Protokollfragmentsicherungen &#40;SQL Server&#41;](tail-log-backups-sql-server.md).  
  
16. Wenn Sie auf ein Bandlaufwerk sichern (gemäß der Konfiguration im Abschnitt **Ziel** der Seite **Allgemein** ), ist die Option **Band nach dem Sichern entladen** aktiviert. Wenn Sie auf diese Option klicken, wird die Option **Band vor dem Entladen zurückspulen** aktiviert.  
  
17. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)]und höher unterstützt die [Sicherungs Komprimierung](backup-compression-sql-server.md). Standardmäßig bestimmt der Wert der Serverkonfigurationsoption **backup-compression default**, ob eine Sicherung komprimiert wird. Unabhängig vom aktuellen Standardwert auf Serverebene können Sie eine Sicherung jedoch komprimieren, indem Sie **Sicherung komprimieren** aktivieren, und die Komprimierung verhindern, indem Sie **Sicherung nicht komprimieren** aktivieren.  
  
     **So zeigen Sie den aktuellen Sicherungs Komprimierungs Standard an**  
  
    -   [Anzeigen oder Konfigurieren der Serverkonfigurationsoption Standardeinstellung für die Sicherungskomprimierung](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
 **Verschlüsselung**  
  
 Um die Sicherungsdatei zu verschlüsseln, aktivieren Sie das Kontrollkästchen **Sicherung verschlüsseln** . Wählen Sie einen Verschlüsselungsalgorithmus aus, der zum Verschlüsseln der Sicherungsdatei verwendet werden soll, und geben Sie ein Zertifikat oder einen asymmetrischen Schlüssel an. Folgende Algorithmen stehen für die Verschlüsselung zur Verfügung:  
  
-   AES 128  
  
-   AES 192  
  
-   AES 256  
  
-   Triple DES  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-back-up-a-transaction-log"></a>So sichern Sie ein Transaktionsprotokoll  
  
1.  Führen Sie die BACKUP LOG-Anweisung aus, um das Transaktionsprotokoll zu sichern, und geben Sie dabei Folgendes an:  
  
    -   Den Namen der Datenbank, zu der das zu sichernde Transaktionsprotokoll gehört.  
  
    -   Das Sicherungsmedium, auf das die Transaktionsprotokollsicherung geschrieben wird.  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
  
> [!IMPORTANT]  
>  In diesem Beispiel wird die [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] -Datenbank verwendet, in der das einfache Wiederherstellungsmodell eingesetzt wird. Um Protokollsicherungen zu ermöglichen, wurde für die Datenbank vor dem Erstellen einer vollständigen Datenbanksicherung die Verwendung des vollständigen Wiederherstellungsmodells festgelegt. Weitere Informationen finden Sie unter [Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
 In diesem Beispiel wird eine Transaktionsprotokollsicherung für die [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] -Datenbank auf dem zuvor erstellten, benannten Sicherungsmedium `MyAdvWorks_FullRM_log1`erstellt.  
  
```sql  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1;  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
  
Verwenden Sie das `Backup-SqlDatabase`-Cmdlet, und geben Sie `Log` als Wert für den `-BackupAction`-Parameter an.  
  
Im folgenden Beispiel wird eine Protokollsicherung der `MyDB` -Datenbank am standardmäßigen Sicherungsspeicherort der Serverinstanz `Computer\Instance`erstellt.  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Log  
    ```  
  
Informationen zum Einrichten und Verwenden des SQL Server PowerShell Anbieters finden Sie unter [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
-   [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [Problembehandlung bei vollen Transaktionsprotokollen &#40;SQL Server-Fehler 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Wartungspläne](../maintenance-plans/maintenance-plans.md)   
 [Vollständige Datei Sicherungen &#40;SQL Server&#41;](full-file-backups-sql-server.md)  
