---
title: Wiederherstellen einer Datenbanksicherung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.locatebackupfileazure.f1
- sql12.swb.specifybackup.f1
helpviewer_keywords:
- full backups [SQL Server]
- database restores [SQL Server], full backups
- backing up databases [SQL Server], full backups
- database backups [SQL Server], full backups
- restoring databases [SQL Server], full backups
ms.assetid: 24b3311d-5ce0-4581-9a05-5c7c726c7b21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3d20276a90a64ca414b8bb6253b03df08908a1f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62921237"
---
# <a name="restore-a-database-backup-sql-server-management-studio"></a>Wiederherstellen einer Datenbanksicherung (SQL Server Management Studio)
  In diesem Thema wird erläutert, wie eine vollständige Datenbanksicherung wiederhergestellt wird.  
  
> [!IMPORTANT]  
>  Im vollständigen oder im massenprotokollierten Wiederherstellungsmodell muss das Protokoll der aktiven Transaktion (wird als Protokollfragment bezeichnet) gesichert werden, bevor eine Datenbank in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] wiederhergestellt werden kann. Weitere Informationen finden Sie unter [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)bezeichnet) gesichert werden. Um eine verschlüsselte Datenbank wiederherstellen zu können, muss das Zertifikat oder der asymmetrische Schlüssel verfügbar sein, das oder der zum Verschlüsseln der Datenbank verwendet wurde. Ohne das Zertifikat oder den asymmetrischen Schlüssel kann die Datenbank nicht wiederhergestellt werden. Darum muss das Zertifikat, das zur Verschlüsselung des Verschlüsselungsschlüssels für die Datenbank verwendet wurde, so lange beibehalten werden, wie die Sicherung benötigt wird. Weitere Informationen finden Sie unter [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).  
  
 Wenn Sie eine Datenbank aus [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wiederherstellen, wird die Datenbank automatisch aktualisiert. In der Regel ist die Datenbank sofort verfügbar. Wenn eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbank Volltextindizes aufweist, werden diese beim Upgrade entweder importiert, zurückgesetzt oder neu erstellt, je nach der Einstellung der Servereigenschaft **Volltextupgrade-Option** . Wenn die Upgradeoption auf **Importieren** oder **Neu erstellen**festgelegt ist, sind die Volltextindizes während des Upgrades nicht verfügbar. Je nach Menge der indizierten Daten kann der Importvorgang mehrere Stunden dauern; die Neuerstellung sogar bis zu zehnmal länger. Wenn die Upgradeoption auf **Importieren**festgelegt und kein Volltextkatalog verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt. Informationen zum Anzeigen oder Ändern der Einstellung der Eigenschaft **Volltextupgrade-Option** finden Sie unter [Verwalten und Überwachen der Volltextsuche auf einer Serverinstanz](../search/manage-and-monitor-full-text-search-for-a-server-instance.md).  
  
### <a name="to-restore-a-full-database-backup"></a>So stellen Sie eine vollständige Datenbanksicherung wieder her  
  
1.  Stellen Sie eine Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und klicken Sie danach im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**. Wählen Sie je nach Datenbank entweder eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken**, und wählen Sie eine Systemdatenbank aus.  
  
3.  Mit der rechten Maustaste in der Datenbank, zeigen Sie auf **Aufgaben**, zeigen Sie auf **wiederherstellen**, und klicken Sie dann auf **Datenbank**, daraufhin die **Restore Database** Das Dialogfeld.  
  
4.  Legen Sie Quelle und Speicherort der wiederherzustellenden Sicherungssätze auf der Seite **Allgemein** mithilfe des Abschnitts **Quelle** fest. Wählen Sie eine der folgenden Optionen aus:  
  
    -   **Datenbank**  
  
         Wählen Sie die wiederherzustellende Datenbank aus der Dropdownliste aus. Die Liste enthält nur Datenbanken, die entsprechend dem Sicherungsverlauf von **msdb** gesichert wurden.  
  
    > [!NOTE]  
    >  Wenn die Sicherung von einem anderen Server abgerufen wird, verfügt der Zielserver über keine Sicherungsverlaufsinformationen für die angegebene Datenbank. Wählen Sie in diesem Fall **Sicherungsmedium** aus, um die wiederherzustellende Datei oder das Medium manuell anzugeben.  
  
    -   **Sicherungsmedium**  
  
         Klicken Sie auf die Schaltfläche zum Durchsuchen ( **...** ), um das Dialogfeld **Sicherungsmedien auswählen** zu öffnen. Wählen Sie im Feld **Sicherungsmedientyp** einen der aufgeführten Medientypen aus. Wenn Sie ein oder mehrere Medien für das Feld **Sicherungsmedien** auswählen möchten, klicken Sie auf **Hinzufügen**.  
  
         Klicken Sie nach dem Hinzufügen der gewünschten Medien zum Listenfeld **Sicherungsmedien** auf **OK** , um zur Seite **Allgemein** zurückzukehren.  
  
         Wählen Sie im Listenfeld **Quelle: Sicherungsmedium: Datenbank** den Namen der Datenbank aus, die wiederhergestellt werden soll.  
  
        > [!NOTE]  
        >  Diese Liste steht nur zur Verfügung, wenn **Sicherungsmedium** ausgewählt ist. Nur Datenbanken mit Sicherungen auf dem ausgewählten Medium stehen zur Verfügung.  
  
         **Sicherungsmedien**  
         Wählen Sie das Medium für den Wiederherstellungsvorgang frei: **Datei**, **Band**, **URL**oder **Sicherungsmedium**. Die Option **Band** ist nur verfügbar, wenn ein Bandlaufwerk auf dem Computer bereitgestellt ist. Die Option **Sicherungsmedium** wird nur angezeigt, wenn mindestens ein Sicherungsmedium vorhanden ist.  
  
         **Sicherungsspeicherort**  
         Hier können Sie Medien für die Wiederherstellung anzeigen, hinzufügen oder entfernen. Die Liste kann bis zu 64 Dateien, Bänder oder Sicherungsmedien enthalten.  
  
         **Hinzufügen**  
         Fügt den Speicherort eines Sicherungsmediums auf die **Sicherungsspeicherort** Liste. Abhängig vom Medientyp, den Sie im Feld **Sicherungsmedium** ausgewählt haben, wird durch das Klicken auf **Hinzufügen** eins der folgenden Dialogfelder geöffnet.  
  
        |Medientyp|Dialogfeld|Beschreibung|  
        |----------------|----------------|-----------------|  
        |**File**|**Sicherungsdatei suchen**|In diesem Dialogfeld können Sie eine lokale Datei aus der Struktur auswählen oder eine Remotedatei mithilfe des vollqualifizierten UNC-Namens (Universal Naming Convention) angeben. Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)aufgezeichnet wurde.|  
        |**Gerät**|**Sicherungsmedium auswählen**|In diesem Dialogfeld können Sie aus einer Liste logischer Sicherungsmedien auswählen, die auf der Serverinstanz definiert sind.|  
        |**Band**|**Sicherungsband auswählen**|In diesem Dialogfeld können Sie aus einer Liste der Bandlaufwerke auswählen, die physisch mit dem Computer verbunden sind, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird.|  
        |**URL**|Die folgenden beiden Dialogfelder werden angezeigt:<br /><br /> 1) **Verbinden mit Windows Azure-Speicher**<br /><br /> 2) **Sicherungsdatei in Windows Azure suchen**|Wählen Sie im Dialogfeld **Mit Windows Azure-Speicher verbinden**  vorhandene SQL-Anmeldeinformationen aus, die den Namen des Windows Azure-Speicherkontos und den Zugriffsschlüssel enthalten, oder erstellen Sie neue SQL-Anmeldeinformationen, indem Sie den Namen des Speicherkontos und den Zugriffsschlüssel angeben. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Windows Azure-Speicher &#40;wiederherstellen&#41;](connect-to-microsoft-azure-storage-restore.md).<br /><br /> Im Dialogfeld **Sicherungsdatei suchen** können Sie im linken Bereich aus der Liste der Container eine Datei auswählen.|  
  
         Wenn die Liste voll ist, ist die Schaltfläche **Hinzufügen** nicht verfügbar.  
  
         **Entfernen**  
         Entfernt eine oder mehrere ausgewählte Dateien, Bänder oder logische Sicherungsmedien.  
  
         **Inhalt**  
         Zeigt den Medieninhalt von ausgewählten Dateien, Bändern oder logischen Sicherungsmedien an.  
  
5.  Im Abschnitt **Ziel** wird das Feld **Datenbank** automatisch mit dem Namen der Datenbank aufgefüllt, die wiederhergestellt werden soll. Geben Sie zum Ändern des Datenbanknamens den neuen Namen ins Feld **Datenbank** ein.  
  
6.  Übernehmen Sie im Feld **Wiederherstellen in** den Standardwert **Bis zur zuletzt erstellten Sicherung** , oder klicken Sie auf **Zeitachse** , um auf das Dialogfeld **Sicherungszeitachse** zuzugreifen und darin manuell einen Zeitpunkt zum Beenden des Wiederherstellungsvorgangs auszuwählen. Weitere Informationen zum Festlegen eines bestimmten Zeitpunkts finden Sie unter [Backup Timeline](backup-timeline.md).  
  
7.  Wählen Sie im Raster **Wiederherzustellende Sicherungssätze** die wiederherzustellenden Sicherungen aus. Mit diesem Raster werden die Sicherungen angezeigt, die für den angegebenen Speicherort verfügbar sind. Standardmäßig wird ein Wiederherstellungsplan vorgeschlagen. Sie können die Auswahl im Raster ändern, um den vorgeschlagenen Wiederherstellungsplan zu überschreiben. Die Auswahl von Sicherungen, die von der Wiederherstellung einer früheren Sicherung abhängig sind, wird automatisch aufgehoben, wenn die Auswahl der früheren Sicherung aufgehoben wird. Weitere Informationen zu den Spalten des Rasters **Wiederherzustellende Sicherungssätze** finden Sie unter [Datenbank wiederherstellen &#40;Seite „Allgemein“&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)bezeichnet) gesichert werden.  
  
8.  Klicken Sie optional im Bereich **Seite auswählen** auf **Dateien** , um auf das Dialogfeld **Dateien** zuzugreifen. Hier können Sie die Datenbank an einem neuen Ort wiederherstellen, indem Sie für die einzelnen Dateien im Raster **Datenbankdateien wiederherstellen als** ein neues Wiederherstellungsziel angeben. Weitere Informationen zu diesem Raster finden Sie unter [Datenbank wiederherstellen &#40;Seite „Dateien“&#41;](restore-database-files-page.md).  
  
9. Zum Anzeigen oder Auswählen der erweiterten Optionen können Sie auf der Seite **Optionen** im Bereich **Wiederherstellungsoptionen** die folgenden für Ihre Situation zutreffenden Optionen auswählen:  
  
    1.  `WITH`-Optionen (nicht erforderlich):  
  
        -   **Vorhandene Datenbank überschreiben (WITH REPLACE)**  
  
        -   **Replikationseinstellungen beibehalten (WITH KEEP_REPLICATION)**  
  
        -   **Zugriff auf die wiederhergestellte Datenbank einschränken (WITH RESTRICTED_USER)**  
  
    2.  Aktivieren Sie eine Option für das Feld **Wiederherstellungsstatus** . In diesem Feld wird der Status der Datenbank nach dem Wiederherstellungsvorgang bestimmt.  
  
        -   **RESTORE WITH RECOVERY** ist das Standardverhalten, das die Datenbank betriebsbereit belässt, indem für Transaktionen ohne Commit ein Rollback ausgeführt wird. Zusätzliche Transaktionsprotokolle können nicht wiederhergestellt werden. Wählen Sie diese Option nur aus, wenn Sie alle benötigten Sicherungen jetzt wiederherstellen möchten.  
  
        -   **RESTORE WITH NORECOVERY** belässt die Datenbank nicht betriebsbereit und führt kein Rollback für Transaktionen ohne Commit aus. Zusätzliche Transaktionsprotokolle können wiederhergestellt werden. Die Datenbank kann erst verwendet werden, wenn sie wiederhergestellt wurde.  
  
        -   **RESTORE WITH STANDBY** belässt die Datenbank im schreibgeschützten Modus. Diese Option macht Transaktionen rückgängig, für die noch kein Commit ausgeführt wurde, speichert die Umkehraktionen aber in einer Standbydatei, damit die Auswirkungen der Wiederherstellung rückgängig gemacht werden können.  
  
    3.  **Erstellen der Sicherung des Protokollfragments vor dem Wiederherstellen** wird ausgewählt, wenn es für den ausgewählten Zeitpunkt erforderlich ist. Sie müssen diese Einstellung nicht ändern, können das Protokollfragment jedoch sichern, auch wenn es nicht erforderlich ist. Dateiname hier? Wenn sich der erste Sicherungssatz auf der Seite **Allgemein** in Windows Azure befindet, wird in demselben Speichercontainer auch das Protokollfragment gesichert.  
  
    4.  Bei Wiederherstellungsvorgängen treten möglicherweise Fehler auf, wenn aktive Verbindungen zur Datenbank bestehen. Aktivieren Sie die Option **Bestehende Verbindungen schließen** , um sicherzustellen, dass alle aktiven Verbindungen zwischen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] und der Datenbank geschlossen werden. Durch die Aktivierung dieses Kontrollkästchens wechselt die Datenbank in einen Einzelbenutzermodus, bevor Wiederherstellungsvorgänge ausgeführt werden. Außerdem wird dadurch die Datenbank auf einen Multibenutzermodus festgelegt, wenn der Vorgang abgeschlossen ist.  
  
    5.  Wählen Sie **Bestätigung vor Wiederherstellen jeder einzelnen Sicherung** aus, wenn Sie zwischen jedem Wiederherstellungsvorgang zur Bestätigung aufgefordert werden möchten. Dies ist in der Regel nur bei großen Datenbanken und bei der gewünschten Überwachung des Status des Wiederherstellungsvorgangs erforderlich.  
  
     Weitere Informationen zu diesen Wiederherstellungsoptionen finden Sie unter [Datenbank wiederherstellen &#40;Seite „Optionen“&#41;](restore-database-options-page.md)bezeichnet) gesichert werden.  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)   
 [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)   
 [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Datenbank wiederherstellen &#40;Seite „Optionen“&#41;](restore-database-options-page.md)   
 [Datenbank wiederherstellen &#40;Seite „Allgemein“&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
