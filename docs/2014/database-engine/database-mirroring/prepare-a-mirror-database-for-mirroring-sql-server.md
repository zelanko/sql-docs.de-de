---
title: Vorbereiten einer Spiegeldatenbank auf die Spiegelung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], preparing for mirroring
- logins [SQL Server], database mirroring
- mirror database [SQL Server]
ms.assetid: 8676f9d8-c451-419b-b934-786997d46c2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf46b4f6fd8e7af55e1930ef6063c4754673fa79
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934089"
---
# <a name="prepare-a-mirror-database-for-mirroring-sql-server"></a>Vorbereiten einer Spiegeldatenbank auf die Spiegelung (SQL Server)
  Eine Datenbank-Spiegelungssitzung kann erst beginnen, nachdem der Datenbankbesitzer oder Systemadministrator sichergestellt hat, dass die Spiegeldatenbank erstellt und auf die Spiegelung vorbereitet wurde. Zum Erstellen einer neuen Spiegeldatenbank sind zumindest eine vollständige Sicherung der Prinzipaldatenbank sowie eine nachfolgende Protokollsicherung erforderlich, wobei beide auf der Spiegelserverinstanz mithilfe von WITH NORECOVERY wiederhergestellt werden müssen.  
  
 In diesem Thema wird beschrieben, wie Sie eine Spiegeldatenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]vorbereiten.  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="requirements"></a><a name="Requirements"></a> Anforderungen  
  
-   Die Prinzipalserver- und Spiegelserverinstanz müssen unter derselben Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden. Obwohl der Spiegelserver eine höhere SQL Server-Version aufweisen darf, wird diese Konfiguration nur für einen sorgfältig geplanten Upgradeprozess empfohlen. In einer solchen Konfiguration laufen Sie Gefahr, ein automatisches Failover auszuführen, bei dem die Datenverschiebung automatisch angehalten wird, da Daten nicht zu einer niedrigeren SQL Server-Version verschoben werden können. Weitere Informationen finden Sie unter [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).  
  
-   Die Prinzipalserver- und Spiegelserverinstanz müssen unter derselben Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden. Informationen zur unterstützten Datenbankspiegelung in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] finden Sie unter [Von den SQL Server 2014-Editionen unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   Für die Datenbank muss das vollständige Wiederherstellungsmodell verwendet werden.  
  
     Weitere Informationen finden Sie unter [Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) oder [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) und [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
-   Der Name der Spiegeldatenbank muss mit dem Namen der Prinzipaldatenbank übereinstimmen.  
  
-   Damit die Spiegelung funktionsfähig ist, muss sich die Spiegeldatenbank im Wiederherstellungsstatus befinden. Beim Vorbereiten einer Spiegeldatenbank müssen Sie für jeden Wiederherstellungsvorgang RESTORE WITH NORECOVERY verwenden. Stellen Sie mindestens die vollständige Sicherung der Prinzipaldatenbank mit WITH NORECOVERY wieder her, und zwar gefolgt von allen nachfolgenden Protokollsicherungen.  
  
-   Stellen Sie sicher, dass das System, auf dem die Spiegeldatenbank erstellt werden soll, ein Laufwerk mit ausreichend Speicherplatz für die Spiegeldatenbank besitzen muss.  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Die **master**-, **msdb**-, **temp**- oder **model** -Systemdatenbanken können nicht gespiegelt werden.  
  
-   Eine Datenbank, die zu einem [AlwaysOn-Verfügbarkeitsgruppen gehört (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md), kann nicht gespiegelt werden.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Verwenden Sie entweder die letzte vollständige Datenbanksicherung oder eine aktuelle differenzielle Datenbanksicherung der Prinzipaldatenbank.  
  
-   Wenn eine sehr häufige Ausführung eines Protokollsicherungsauftrags in der Prinzipaldatenbank geplant ist, müssen Sie möglicherweise den Sicherungsauftrag deaktivieren, bis die Spiegelung beginnt.  
  
-   Wenn möglich sollte der Pfad (einschließlich des Laufwerkbuchstabens) der Spiegeldatenbank mit dem Pfad der Prinzipaldatenbank identisch sein.  
  
     Wenn sich die Pfade unterscheiden müssen, weil sich beispielsweise die Prinzipaldatenbank auf Laufwerk 'F': befindet, auf dem Spiegelsystem jedoch kein Laufwerk F: vorhanden ist, müssen Sie die MOVE-Option in die RESTORE-Anweisung einschließen.  
  
    > [!IMPORTANT]  
    >  Damit eine Datei während einer Spiegelungssitzung hinzugefügt werden kann, ohne dass sich dies auf die Sitzung auswirkt, muss der Pfad der Datei auf beiden Servern vorhanden sein. Wenn Sie die Datenbankdateien bei der Erstellung der Spiegeldatenbank verschieben, kann bei einem später durchgeführten Vorgang zum Hinzufügen einer Datei in der Spiegeldatenbank ein Fehler auftreten oder die Spiegelung wird möglicherweise angehalten. Informationen zum Umgang mit einem fehlerhaften Dateierstellungsvorgang finden Sie unter [Problembehandlung für die Datenbankspiegelungskonfiguration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md).  
  
-   Hat die Prinzipaldatenbank mindestens einen Volltextkatalog, sollten Sie [Datenbankspiegelung und Volltextkataloge &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md) lesen.  
  
-   Bei einer Produktionsdatenbank erstellen Sie die Sicherung stets auf einem separaten Medium.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 TRUSTWORTHY wird beim Sichern einer Datenbank auf OFF festgelegt. Deshalb ist TRUSTWORTHY bei einer neuen Spiegeldatenbank immer OFF. Muss die Datenbank nach einem Failover vertrauenswürdig sein, sind zusätzliche Installationsschritte erforderlich. Weitere Informationen finden Sie unter [Einrichten der TRUSTWORTHY-Eigenschaft für eine Spiegeldatenbank &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)vorbereiten.  
  
 Informationen zum Aktivieren der automatischen Verschlüsselung des Datenbank-Hauptschlüssels einer Spiegeldatenbank finden Sie unter [Einrichten einer verschlüsselten Spiegeldatenbank](set-up-an-encrypted-mirror-database.md).  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Datenbankbesitzer oder Systemadministrator.  
  
##  <a name="to-prepare-an-existing-mirror-database-to-restart-mirroring"></a><a name="PrepareToRestartMirroring"></a> So bereiten Sie eine vorhandene Spiegeldatenbank auf das erneute Starten der Spiegelung vor  
 Wenn die Spiegelung entfernt wurde und die Spiegeldatenbank sich weiterhin im RECOVERING-Status befindet, können Sie die Spiegelung erneut starten.  
  
1.  Erstellen Sie mindestens eine Protokollsicherung auf der Prinzipaldatenbank. Weitere Informationen finden Sie unter [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)bezeichnet) gesichert werden.  
  
2.  Verwenden Sie auf der Spiegeldatenbank RESTORE WITH NORECOVERY, um alle Protokollsicherungen wiederherzustellen, die seit dem Entfernen der Spiegelung auf der Prinzipaldatenbank erstellt wurden. Weitere Informationen finden Sie unter [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)vorbereiten.  
  
##  <a name="to-prepare-a-new-mirror-database"></a><a name="CombinedProcedure"></a>So bereiten Sie eine neue Spiegel Datenbank vor  
 **So bereiten Sie eine Spiegeldatenbank vor**  
  
> [!NOTE]  
>  Ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Beispiel für diese Prozedur finden Sie weiter unten in diesem Abschnitt unter [Beispiel (Transact-SQL)](#TsqlExample).  
  
1.  Stellen Sie eine Verbindung mit einer Prinzipalserverinstanz her.  
  
2.  Erstellen Sie entweder eine vollständige Datenbanksicherung oder eine differenzielle Datenbanksicherung der Prinzipaldatenbank.  
  
    -   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
    -   [Erstellen Sie eine differenzielle Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).  
  
3.  In der Regel müssen Sie mindestens eine Protokollsicherung auf der Prinzipaldatenbank erstellen. Eine Protokollsicherung ist jedoch möglicherweise nicht erforderlich, wenn die Datenbank erst kürzlich erstellt wurde und bisher keine Protokollsicherung vorgenommen wurde oder wenn das Wiederherstellungsmodell soeben von SIMPLE in FULL geändert wurde.  
  
    -   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
4.  Sofern sich die Sicherungen nicht auf einem Netzlaufwerk befinden, auf das von beiden Systemen zugegriffen werden kann, kopieren Sie die Datenbank- und Protokollsicherungen in das System, von dem die Spiegelserverinstanz gehostet wird.  
  
5.  Stellen Sie eine Verbindung zur Spiegelserverinstanz her.  
  
6.  Erstellen Sie mit RESTORE WITH NORECOVERY die Spiegeldatenbank, indem Sie die vollständige Datenbanksicherung und optional die letzte differenzielle Datenbanksicherung auf der Spiegelserverinstanz wiederherstellen.  
  
    > [!NOTE]  
    >  Wenn Sie die Datenbank dateigruppenweise wiederherstellen, stellen Sie sicher, dass Sie die vollständige Datenbank wiederherstellen.  
  
    -   [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
    -   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) und [RESTORE-Argumente &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)vorbereiten.  
  
7.  Wenden Sie unter Angabe von RESTORE WITH NORECOVERY alle ausstehenden Protokollsicherungen auf die Spiegeldatenbank an.  
  
    -   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Bevor Sie eine Datenbank-Spiegelungssitzung starten können, müssen Sie die Spiegeldatenbank erstellen. Dies sollte vor dem Starten der Spiegelungssitzung erfolgen.  
  
 In diesem Beispiel wird die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank verwendet, in der standardmäßig das einfache Wiederherstellungsmodell verwendet wird.  
  
1.  Damit die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank für die Datenbankspiegelung verwendet werden kann, ändern Sie sie so, dass das vollständige Wiederherstellungsmodell verwendet wird.  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  Nach dem Ändern des Wiederherstellungsmodells der Datenbank von SIMPLE in FULL erstellen Sie eine vollständige Sicherung, die zum Erstellen der Spiegeldatenbank verwendet werden kann. Da das Wiederherstellungsmodell soeben geändert wurde, wird die Option WITH FORMAT angegeben, um einen neuen Mediensatz zu erstellen. Dies ist hilfreich, um die Sicherungen unter dem vollständigen Wiederherstellungsmodell von vorherigen Sicherungen zu trennen, die unter dem einfachen Wiederherstellungsmodell erstellt wurden. Im Rahmen dieses Beispiels wird die Sicherungsdatei (`C:\AdventureWorks.bak`) auf dem gleichen Laufwerk wie die Datenbank erstellt.  
  
    > [!NOTE]  
    >  Bei einer Produktionsdatenbank sollten Sie die Sicherung stets auf einem separaten Medium erstellen.  
  
     Erstellen Sie auf der Prinzipalserverinstanz (auf `PARTNERHOST1`) folgendermaßen eine vollständige Sicherung der Prinzipaldatenbank:  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  Kopieren Sie die vollständige Sicherung auf den Spiegelserver.  
  
4.  Stellen Sie die vollständige Sicherung mit der Option RESTORE WITH NORECOVERY auf der Spiegelserverinstanz wieder her. Der Wiederherstellungsbefehl hängt davon ab, ob die Pfade der Prinzipal- und Spiegeldatenbanken identisch sind.  
  
    -   **Wenn die Pfade identisch sind, führen Sie Folgendes aus:**  
  
         Stellen Sie auf der Spiegelserverinstanz (auf `PARTNERHOST5`) folgendermaßen die vollständige Sicherung wieder her:  
  
        ```  
        RESTORE DATABASE AdventureWorks   
            FROM DISK = 'C:\AdventureWorks.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   **Wenn die Pfade unterschiedlich sind, führen Sie Folgendes aus:**  
  
         Wenn sich der Pfad der Spiegeldatenbank vom Pfad der Prinzipaldatenbank unterscheidet (z. B. wenn die Laufwerkbuchstaben unterschiedlich sind), ist es für das Erstellen der Spiegeldatenbank erforderlich, dass der Wiederherstellungsvorgang eine MOVE-Klausel einschließt.  
  
        > [!IMPORTANT]  
        >  Wenn die Pfadnamen der Prinzipal- und Spiegeldatenbanken unterschiedlich sind, können Sie keine Datei hinzufügen. Der Grund hierfür besteht darin, dass die Spiegelserverinstanz beim Empfangen des Protokolls für das Hinzufügen einer Datei versucht, die neue Datei an dem Speicherort abzulegen, der von der Prinzipaldatenbank verwendet wird.  
  
         So wird beispielsweise über den folgenden Befehl eine Sicherung einer Prinzipaldatenbank, die sich in „C:\Programme\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\“ befindet, an einem anderen Speicherort (D:\Programme\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`) erstellt, in dem sich die Spiegeldatenbank befinden soll.  
  
        ```  
        RESTORE DATABASE AdventureWorks  
           FROM DISK='C:\AdventureWorks.bak'  
           WITH NORECOVERY,   
              MOVE 'AdventureWorks_Data' TO   
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Data.mdf',   
              MOVE 'AdventureWorks_Log' TO  
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Log.ldf';  
        GO  
        ```  
  
5.  Nach dem Erstellen der vollständigen Sicherung müssen Sie eine Protokollsicherung in der Prinzipaldatenbank erstellen. Über die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung wird beispielsweise das Protokoll in derselben Datei gesichert, die auch bei der vorhergehenden vollständigen Sicherung verwendet wurde:  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  Sie können erst mit der Spiegelung beginnen, nachdem Sie die erforderliche Protokollsicherung (und alle nachfolgenden Protokollsicherungen) angewendet haben.  
  
     So wird beispielsweise mit der folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung das erste Protokoll von `C:\AdventureWorks.bak`wiederhergestellt:  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  Werden zusätzliche Protokollsicherungen vor dem Beginn der Spiegelung vorgenommen, müssen Sie auch all diese Protokollsicherungen nacheinander mithilfe von WITH NORECOVERY auf dem Spiegelserver wiederherstellen.  
  
     So werden beispielsweise mit der folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung zwei zusätzliche Protokolle von `C:\AdventureWorks.bak`wiederhergestellt:  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
 Ein vollständiges Beispiel für das Einrichten von Datenbankspiegelung, Anzeigen der Sicherheitseinrichtung, Vorbereiten der Spiegeldatenbank, Einrichten der Partner und Hinzufügen eines Zeugen finden Sie unter [Einrichten der Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)vorbereiten.  
  
##  <a name="follow-up-after-preparing-a-mirror-database"></a><a name="FollowUp"></a> Nachverfolgung: Nach der Vorbereitung einer Spiegeldatenbank  
  
1.  Wenn seit dem letzten RESTORE LOG-Vorgang Protokollsicherungen vorgenommen wurden, müssen Sie jede zusätzliche Protokollsicherung mit RESTORE WITH NORECOVERY manuell anwenden.  
  
2.  Starten Sie die Spiegelungssitzung. Weitere Informationen finden Sie unter [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) oder [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)vorbereiten.  
  
3.  Wenn Sie den Sicherungsauftrag für die Prinzipaldatenbank deaktiviert haben, aktivieren Sie den Auftrag erneut.  
  
4.  Muss die Datenbank nach einem Failover vertrauenswürdig sein, sind zusätzliche Installationsschritte nach dem Beginn der Spiegelung erforderlich. Weitere Informationen finden Sie unter [Einrichten der TRUSTWORTHY-Eigenschaft für eine Spiegeldatenbank &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)vorbereiten.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)  
  
-   [Einrichten einer verschlüsselten Spiegeldatenbank](set-up-an-encrypted-mirror-database.md)  
  
-   [Einrichten der TRUSTWORTHY-Eigenschaft für eine Spiegeldatenbank &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Daten Bank Spiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Transport Sicherheit für Daten Bank Spiegelung und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)   
 [Das Einrichten der Daten Bank Spiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Sichern und Wiederherstellen von Volltextkatalogen und Indizes](../../relational-databases/indexes/indexes.md)   
 [Daten Bank Spiegelung und voll Text Kataloge &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md)   
 [Daten Bank Spiegelung und Replikation &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [RESTORE-Argumente &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)  
  
  
