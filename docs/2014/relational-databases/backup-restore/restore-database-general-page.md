---
title: Datenbank wiederherstellen (Seite „Allgemein“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.general.f1
ms.assetid: 160cf58c-b06a-475f-9a69-2b051e5767ab
caps.latest.revision: 85
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 79929bf3f9bebec61605ad173a460fbdbe2269f3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219480"
---
# <a name="restore-database-general-page"></a>Datenbank wiederherstellen (Seite 'Allgemein')
  Verwenden Sie die Seite **Allgemein** , um Informationen zu Ziel- und Quelldatenbanken für einen Wiederherstellungsvorgang der Datenbank anzugeben.  
  
 **So verwenden Sie SQL Server Management Studio zum Wiederherstellen einer Datenbanksicherung**  
  
-   [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  Wenn Sie einen wiederherstellungstask angeben, indem [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], können Sie die entsprechende generieren [!INCLUDE[tsql](../../includes/tsql-md.md)] [wiederherstellen](/sql/t-sql/statements/restore-statements-transact-sql) Skript durch Klicken auf **Skript** und anschließend ein Ziel für das Skript auswählen.  
  
## <a name="permissions"></a>Berechtigungen  
 Ist die wiederherzustellende Datenbank nicht vorhanden, muss der Benutzer über CREATE DATABASE-Berechtigungen verfügen, um RESTORE ausführen zu können. Ist die Datenbank vorhanden, werden RESTORE-Berechtigungen standardmäßig den Mitgliedern der festen Serverrollen **sysadmin** und **dbcreator** sowie dem Besitzer (**dbo**) der Datenbank erteilt.  
  
 RESTORE-Berechtigungen werden Rollen erteilt, in denen Mitgliedsinformationen immer für den Server verfügbar sind. Da die Mitgliedschaft in einer festen Datenbankrolle nur bei unbeschädigten und zugänglichen Datenbanken geprüft werden kann (was beim Ausführen von RESTORE nicht immer der Fall ist), verfügen Mitglieder der festen Datenbankrolle **db_owner** nicht über RESTORE-Berechtigungen.  
  
 Wiederherstellen aus einer verschlüsselten Sicherung benötigt `VIEW DEFINITION` Berechtigungen auf das Zertifikat oder asymmetrischen Schlüssel verwendet, um während der Sicherung zu verschlüsseln.  
  
## <a name="options"></a>Tastatur  
  
### <a name="source"></a>Quelle  
 Mit den Optionen des Bereichs **Wiederherstellen von**kann der Speicherort der Sicherungssätze für die Datenbank identifiziert und bestimmt werden, welche Sicherungssätze wiederhergestellt werden sollen.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Datenbank**|Wählen Sie die wiederherzustellende Datenbank aus der Dropdownliste aus. Die Liste enthält nur Datenbanken, die entsprechend dem Sicherungsverlauf von **msdb** gesichert wurden.|  
|**Sicherungsmedium**|Wählen Sie die logischen oder physischen Sicherungsmedien (Bänder, URL oder Dateien) aus, die die Sicherung oder Sicherungen enthalten, die Sie wiederherstellen möchten. Dies ist erforderlich, wenn die Datenbanksicherung auf einer anderen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aufgezeichnet wurde.<br /><br /> Klicken Sie auf die Schaltfläche „...“. Das Dialogfeld **Sicherungsmedien auswählen** wird geöffnet, in dem Sie mindestens ein logisches oder physisches Sicherungsmedien auswählen können. In diesem Dialogfeld können Sie bis zu 64 Medien auswählen, die zu einem einzigen Mediensatz gehören. Bandmedien müssen physisch mit dem Computer verbunden sein, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird. Eine Sicherungsdatei kann sich auf einem lokalen Datenträger oder auf einem Wechseldatenträger befinden. Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)aufgezeichnet wurde. Sie können auch **URL** als Gerätetyp für Sicherungsdateien auswählen, die in Microsoft Azure Storage gespeichert sind.<br /><br /> Wenn Sie das Dialogfeld **Sicherungsmedien auswählen** schließen, wird das ausgewählte Medium in Form von schreibgeschützten Werten in der Liste **Sicherungsmedium** angezeigt.|  
|**Datenbank**|Wählen Sie in der Dropdownliste den Namen der Datenbank aus, von der die Sicherungen wiederhergestellt werden sollen.<br /><br /> Hinweis: Diese Liste ist nur verfügbar, wenn **Sicherungsmedium** ausgewählt wird. Nur Datenbanken mit Sicherungen auf den ausgewählten Sicherungsmedien stehen zur Verfügung.|  
  
### <a name="destination"></a>Ziel  
 Mit den Optionen des Bereichs **Ziel** werden die Datenbank und der Wiederherstellungspunkt identifiziert.  
  
|Begriff|Definition|  
|----------|----------------|  
|**Datenbank**|Geben Sie die wiederherzustellende Datenbank in die Liste ein. Sie können eine neue Datenbank eingeben oder eine vorhandene Datenbank aus der Dropdownliste auswählen. Die Liste umfasst alle Datenbanken auf dem Server, mit Ausnahme der Datenbanken **master** und **tempdb**.<br /><br /> Hinweis: Verwenden Sie die [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) -Anweisung, um eine kennwortgeschützte Sicherung wiederherzustellen.|  
|**Ziel**|Das Feld **Wiederherstellen** wird standardmäßig auf „To the last backup taken“ (Bis zur zuletzt erstellten Sicherung) festgelegt. Sie können auch auf **Zeitachse** klicken, um das Dialogfeld **Sicherungszeitachse** anzuzeigen, das den Datenbanksicherungsverlauf in Form einer Zeitachse anzeigt. Klicken Sie auf **Zeitachse** festlegen einen bestimmten `datetime` , den die Datenbank wiederhergestellt werden soll. Die Datenbank wird dann in dem Zustand wiederhergestellt, in dem sie sich zum betreffenden Zeitpunkt befunden hat. Weitere Informationen finden Sie unter [Sicherungszeitachse](backup-timeline.md).|  
  
### <a name="restore-plan"></a>Wiederherstellungsplan  
  
|Begriff|Definition|  
|----------|----------------|  
|**Wiederherzustellende Sicherungssätze**|Zeigt die verfügbaren Sicherungssätze für den angegebenen Ort an. Jeder Sicherungssatz, das Ergebnis eines einzelnen Sicherungsvorgangs, wird auf alle Medien des Mediensatzes verteilt. Standardmäßig wird ein Wiederherstellungsplan vorgeschlagen, um das Ziel des Wiederherstellungsvorgangs zu erreichen, der auf der Auswahl der erforderlichen Sicherungssätze basiert. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwendet den Sicherungsverlauf in **msdb** , um festzustellen, welche Sicherungen zum Wiederherstellen einer Datenbank erforderlich sind, und erstellt einen Wiederherstellungsplan. Für eine Datenbankwiederherstellung beispielsweise werden die neueste vollständige Datenbanksicherung und anschließend die neueste nachfolgende differenzielle Datenbanksicherung (soweit vorhanden) vom Wiederherstellungsplan ausgewählt. Bei Verwendung des vollständigen Wiederherstellungsmodells werden dann alle nachfolgenden Protokollsicherungen vom Wiederherstellungsplan ausgewählt.<br /><br /> Um den vorgeschlagenen Wiederherstellungsplan zu überschreiben, können Sie die folgenden Optionen im Raster ändern. Für Sicherungen, die von einer Sicherung abhängig sind, für die die Auswahl aufgehoben wurde, wird die Auswahl automatisch aufgehoben.<br /><br /> **Wiederherstellen**:<br />                          Die aktivierten Kontrollkästchen zeigen die wiederherzustellenden Sicherungssätze an.<br />**Namen**: der Name des Sicherungssatzes.<br />**Komponente**: die gesicherte Komponente: **Datenbank**, **Datei**, oder  **\<leer >** (bei Transaktionsprotokollen).<br />**Typ**: Der Typ der ausgeführten Sicherung: **Vollständig**, **Differenziell**oder **Transaktionsprotokoll**.<br />**Server**: Der Name der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz, die den Sicherungsvorgang ausführt.<br />**Datenbank**: der Name der am Sicherungsvorgang beteiligten Datenbank.<br />**Position**: Position des Sicherungssatzes auf dem Volume.<br />**Erste LSN**: die protokollfolgenummer der ersten Transaktion im Sicherungssatz. Bei Dateisicherungen leer.<br />**LSN des letzten**: die protokollfolgenummer der letzten Transaktion im Sicherungssatz. Bei Dateisicherungen leer.<br />**Prüfpunkt-LSN**: die protokollfolgenummer (LSN) des letzten Prüfpunkts zum Zeitpunkt der Sicherung erstellt wurde.<br />**Vollständige LSN**: die protokollfolgenummer der neuesten vollständigen datenbanksicherung.<br />**Startdatum**: Datum und-Zeit des Sicherungsvorgangs, entsprechend in den ländereinstellungen des Clients.<br />**Beendigungsdatum**: Datum und Uhrzeit, die nach des Sicherungsvorgangs Abschluss angezeigt, in den ländereinstellungen des Clients.<br />**Größe**: die Größe des Sicherungssatzes in Byte festgelegt.<br />**Benutzername**: der Name des Benutzers, der den Sicherungsvorgang ausgeführt hat.<br /><br /> **Ablauf des**: das Datum und Uhrzeit, zu der Sicherungssatz abläuft.<br /><br /> Die Kontrollkästchen werden nur aktiviert, wenn das Kontrollkästchen **Manuelle Auswahl** aktiviert ist. Dies ermöglicht Ihnen die Auswahl der wiederherzustellenden Sicherungssätze.<br /><br /> Wenn das Kontrollkästchen **Manuelle Auswahl** aktiviert wird, wird die Genauigkeit des Wiederherstellungsplans bei jeder Änderung überprüft. Wenn die Abfolge der Sicherungen falsch ist, wird eine Fehlermeldung angezeigt.|  
|**Sicherungsmedien überprüfen**|Ruft eine RESTORE VERIFY_ONLY-Anweisung für die ausgewählten Sicherungssätze auf.<br /><br /> Hinweis: Dabei handelt es sich um einen längeren Vorgang, und der Status kann mithilfe des Fortschrittsmonitors im Dialogfeld-Framework nachverfolgt und der Vorgang abgebrochen werden.<br /><br /> Mit dieser Schaltfläche können Sie die Integrität der ausgewählten Sicherungsdateien vor der Wiederherstellung überprüfen.<br /><br /> Wenn die Integrität von Sicherungssätzen überprüft wird, lautet der Status links unten im Dialogfeld "Wird überprüft" anstatt "Wird ausgeführt".|  
  
## <a name="compatibility-support"></a>Kompatibilitätsunterstützung  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]können Sie eine Benutzerdatenbank von einer Datenbanksicherung wiederherstellen, die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder einer höheren Version erstellt wurde. Sicherungen von **master**, **model** und **msdb** , die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] bis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] erstellt wurden, können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]jedoch nicht wiederhergestellt werden. Auch in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erstellte Sicherungen können nicht mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wiederhergestellt werden.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendet im Vergleich zu früheren Versionen einen anderen Standardpfad. Daher muss zum Wiederherstellen einer Datenbank, die am Standardspeicherort einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt wurde, die MOVE-Option verwendet werden.  
  
 Nachdem Sie eine Datenbank einer früheren Version in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wiederhergestellt haben, wird die Datenbank automatisch aktualisiert. In der Regel ist die Datenbank sofort verfügbar. Wenn eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbank Volltextindizes aufweist, werden diese beim Upgrade entweder importiert, zurückgesetzt oder neu erstellt, je nach der Einstellung der Servereigenschaft **Volltextupgrade-Option** . Wenn die Upgradeoption auf **Importieren** oder **Neu erstellen**festgelegt ist, sind die Volltextindizes während des Upgrades nicht verfügbar. Je nach Menge der indizierten Daten kann der Importvorgang mehrere Stunden dauern; die Neuerstellung sogar bis zu zehnmal länger. Wenn die Upgradeoption auf **Importieren**festgelegt und kein Volltextkatalog verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt.  
  
## <a name="restoring-from-an-encrypted-backup"></a>Wiederherstellen aus einer verschlüsselten Sicherung  
 Für die Wiederherstellung muss das Zertifikat oder der asymmetrische Schlüssel, mit dem die Datenbank ursprünglich erstellt wurde, auf der Instanz verfügbar sein, auf der die Wiederherstellung erfolgen soll. Das Konto, das Durchführen der Wiederherstellung müssen `VIEW DEFINITIONS` für das Zertifikat oder asymmetrischen Schlüssel. Zertifikate, die zum Verschlüsseln von Sicherungen verwendet wurden, sollten nicht erneuert oder aktualisiert werden.  
  
## <a name="restoring-from-windows-azure-storage"></a>Wiederherstellen aus dem Windows Azure-Speicher  
 Wenn Sie eine Sicherung wiederherstellen, die im Windows Azure-Speicher gespeichert ist, weist die Wiederherstellungsbenutzeroberfläche eine neue Sicherungsmedienoption auf. **URL** auf die **Sicherungsmedien auswählen** Dialogfeld. Beim Klicken auf **hinzufügen**, dadurch gelangen Sie auf die **Herstellen einer Verbindung mit Windows Azure** Dialogfeld, das Ihnen ermöglicht, geben Sie die SQL-Anmeldeinformationen für das Speicherkonto zu authentifizieren.  Nachdem mit dem Speicherkonto hergestellt wurde, werden die Sicherungsdateien angezeigt, der **eine Sicherungsdatei in Windows Azure suchen** Dialogfeld, in dem Sie die Datei für die Verwendung für die Wiederherstellung auswählen können.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Wiederherstellung einer Sicherung von einem Medium &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)   
 [Wiederherstellen einer Datenbank bis zu einer markierten Transaktion &#40;SQL Server Management Studio&#41;](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)   
 [Anzeigen der Inhalte eines Sicherungsbands oder einer -datei &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)   
 [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)   
 [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE-Argumente &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)   
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)  
  
  
