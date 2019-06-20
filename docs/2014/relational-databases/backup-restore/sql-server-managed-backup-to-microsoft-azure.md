---
title: SQLServer Managed Backup für Windows Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: afa01165-39e0-4efe-ac0e-664edb8599fd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b4071bee5e13f415be90328bb7ff0b55ff91087c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62877129"
---
# <a name="sql-server-managed--backup-to-windows-azure"></a>SQL Server Managed Backup für Windows Azure
  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verwaltet und automatisiert SQL Server-Sicherungen im Windows Azure-BLOB-Speicherdienst. Die von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verwendete Sicherungsstrategie richtet sich nach dem Beibehaltungszeitraum und der Arbeitsauslastung der Datenbank (Transaktionsvolumen). [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] unterstützt die Wiederherstellung zu einem bestimmten Zeitpunkt für den angegebenen Beibehaltungszeitraum.   
[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] kann auf Datenbankebene oder auf Instanzebene aktiviert werden, um alle Datenbanken in der Instanz von SQL Server zu verwalten. Der SQL-Server kann lokal oder in gehosteten Umgebungen wie dem virtuellen Windows Azure-Computer ausgeführt werden. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] wird für SQL Server auf Windows Azure-Computern empfohlen.  
  
## <a name="benefits-of-automating-sql-server-backup-using-includesssmartbackupincludesss-smartbackup-mdmd"></a>Vorteile der Automatisierung der SQL Server-Sicherung mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
-   Für die Automatisierung von Sicherungen für mehrere Datenbanken sind derzeit die Entwicklung einer Sicherungsstrategie, das Schreiben von eigenem Code und eine Planung der Sicherungen erforderlich. Mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] müssen Sie nur die Beibehaltungsdauereinstellungen und den Speicherort angeben. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] plant, ausführt und Verwaltung der Sicherungen.  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] kann auf Datenbankebene konfiguriert werden oder mit den Standardeinstellungen für eine SQL Server-Instanz. Automatisierung der Sicherung mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] hat die folgenden Vorteile:  
  
    -   Durch die Festlegung der Standardwerte auf Instanzebene können Sie diese Einstellungen auf jede nachfolgend erstellte Datenbank anwenden. Damit vermeiden Sie das Risiko, dass neue Datenbanken nicht gesichert werden und Daten verloren gehen.  
  
    -   Durch die Aktivierung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] und die Festlegung der Beibehaltungsdauer auf Datenbankebene können Sie die Standardeinstellungen auf Instanzebene überschreiben. So können Sie die Wiederherstellbarkeit einer spezifischen Datenbank präziser steuern.  
  
-   Mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] müssen Sie weder den Sicherungstyp noch die Sicherungshäufigkeit für eine Datenbank angeben.  Sie geben den Beibehaltungszeitraum und [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] bestimmt die Art und Häufigkeit der Sicherungen für eine Datenbank die Sicherungen im Windows Azure-Blob-Speicherdienst gespeichert. Weitere Informationen zu den Satz von Kriterien, die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verwendet, um die Sicherungsstrategie, zu erstellen, finden Sie die [Komponenten und Konzepte](#Concepts) in diesem Thema.  
  
-   Wenn die Verwendung der Verschlüsselung konfiguriert ist, haben Sie zusätzliche Sicherheit für Sicherungsdaten. Weitere Informationen finden Sie unter [Sicherungsverschlüsselung](backup-encryption.md)  
  
 Weitere Informationen zu den Vorteilen der Verwendung von Windows Azure-Blob-Speicher für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen finden Sie unter [SQL Server-Sicherung und-Wiederherstellung mit dem Windows Azure-Blob-Speicherdienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
## <a name="terms-and-definitions"></a>Begriffe und Definitionen  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
 Eine SQL Server-Funktion zur Automatisierung von Datenbanksicherungen und zur Verwaltung der Sicherungen auf Basis der Beibehaltungsdauer.  
  
 Beibehaltungsdauer  
 Anhand der Beibehaltungsdauer ermittelt [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], welche Sicherungsdateien im Speicher behalten werden sollen, damit eine Datenbank zu einem gezielten Zeitpunkt innerhalb des angegebenen Zeitraums wiederhergestellt werden kann.  Die unterstützten Werte liegen im Bereich zwischen 1 und 30 Tagen.  
  
 Protokollkette  
 Eine fortlaufende Abfolge von Protokollsicherungen wird als Protokollkette bezeichnet. Eine Protokollkette beginnt mit einer vollständigen Sicherung der Datenbank.  
  
##  <a name="Concepts"></a> Anforderungen, Komponenten und Konzepte  
  
  
###  <a name="Security"></a> Berechtigungen  
 Transact-SQL ist die Hauptschnittstelle für die Konfiguration und Überwachung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Im Allgemeinen um die Konfiguration ausgeführt werden die gespeicherten Prozeduren, **Db_backupoperator** Datenbankrolle mit **ALTER ANY CREDENTIAL** Berechtigungen und `EXECUTE` Berechtigungen für **Sp_delete_ Backuphistory** gespeicherte Prozedur ist erforderlich.  Gespeicherte Prozeduren und Funktionen zur Überprüfung von Informationen erfordern in der Regel `Execute`-Berechtigungen für die gespeicherte Prozedur bzw. `Select`-Berechtigungen für die Funktion.  
  
###  <a name="Prereqs"></a> Erforderliche Komponenten  
 **Voraussetzungen:**  
  
 **Windows Azure Storage-Dienst** dient der [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] zum Speichern der Sicherungsdateien.    Die Konzepte, die Struktur und die Anforderungen für das Erstellen eines Windows Azure-Speicherkontos werden ausführlich in die [Introduction to Key Components and Concepts](sql-server-backup-to-url.md#intorkeyconcepts) Teil der **SQL Server Backup to URL** In diesem Thema.  
  
 **SQL-Anmeldeinformationen** dient zum Speichern der Informationen erforderlich, um das Windows Azure-Speicherkonto zu authentifizieren. In Objekt mit den SQL-Anmeldeinformationen werden der Kontoname und der Zugriffsschlüssel gespeichert. Weitere Informationen finden Sie unter den [Introduction to Key Components and Concepts](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) im Abschnitt der **SQL Server Backup to URL** Thema. Eine exemplarische Vorgehensweise zum Erstellen von SQL-Anmeldeinformationen zum Speichern von Authentifizierungsinformationen für die Windows Azure-Speicher finden Sie unter [Lektion 2: Erstellen Sie eine SQL Server-Anmeldeinformation](../../tutorials/lesson-2-create-a-sql-server-credential.md).  
  
###  <a name="Concepts_Components"></a> Komponenten und Konzepte  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ist eine Funktion zur Verwaltung der Sicherungsvorgänge. Er speichert die Metadaten in die **Msdb** -Datenbank und verwendet Systemaufträge zum Schreiben vollständiger datenbanksicherungen und Transaktions-protokollsicherungen.  
  
#### <a name="components"></a>Komponenten  
 Transact-SQL ist die Hauptschnittstelle für die Interaktion mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Gespeicherte Systemprozeduren werden für die Aktivierung, Konfiguration und Überwachung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]verwendet. Systemfunktionen werden zum Abrufen vorhandener Konfigurationseinstellungen, Parameterwerte und Sicherungsdateiinformationen verwendet. Erweiterte Ereignisse dienen der Überwachung von Fehlern und Warnungen. Warnmechanismen werden über SQL Agent-Aufträge und die richtlinienbasierte Verwaltung in SQL Server aktiviert. Es folgt eine Liste der Objekte und eine Beschreibung ihrer Funktionen im Hinblick auf [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 PowerShell-Cmdlets sind ebenfalls verfügbar zur Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. SQL Server Management Studio unterstützt das Wiederherstellen von Sicherungen, die mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] erstellt wurden, über die Aufgabe **Datenbank wiederherstellen** .  
  
|||  
|-|-|  
|Systemobjekt|Description|  
|**MSDB**|Speichert die Metadaten und den Sicherungsverlauf für alle von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]erstellten Sicherungen.|  
|[smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)|Gespeicherte Systemprozedur für die Aktivierung und Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für eine Datenbank.|  
|[smart_admin.set_instance_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451009(v=sql.120).aspx)|Gespeicherte Systemprozedur zum Aktivieren und Konfigurieren von Einstellungen der Standardrichtlinie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für SQL Server-Instanz.|  
|[smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)|Gespeicherte Systemprozedur zum Pausieren und Wiederaufnehmen von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]|  
|[smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)|Gespeicherte Systemprozedur zur Aktivierung und Konfiguration der Überwachung für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Beispiele: Aktivierung erweiterter Ereignisse, E-Mail-Einstellungen für Benachrichtigungen|  
|[smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)|Gespeicherte Systemprozedur, die verwendet wird, um eine Ad-hoc-Sicherung für eine Datenbank auszuführen, die aktiviert ist, verwenden [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ohne Unterbrechung der Protokollkette.|  
|[smart_admin.fn_backup_db_config &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-backup-db-config-transact-sql)|Systemfunktion, die die aktuelle zurückgibt [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Status und die Konfigurationswerte für eine Datenbank oder für alle Datenbanken auf der Instanz.|  
|[smart_admin.fn_is_master_switch_on &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-is-master-switch-on-transact-sql)|Systemfunktion, die den Status des Hauptschalters zurückgibt|  
|[smart_admin.sp_get_backup_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-get-backup-diagnostics-transact-sql)|Gespeicherte Systemprozedur für die Rückgabe der von den erweiterten Ereignissen protokollierten Ereignisse|  
|[smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)|Systemfunktion, die die aktuellen Werte für die Sicherungssystemeinstellungen zurückgibt, z. B. für die Überwachung oder für Warnungs-E-Mail-Einstellungen|  
|[smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql)|Gespeicherte Prozedur zum Abrufen der verfügbaren Sicherungsoptionen für eine angegebene Datenbank bzw. für alle Datenbanken einer Instanz|  
|[smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)|Systemfunktion, die die aktuellen Einstellungen für die erweiterten Ereignisse zurückgibt|  
|[smart_admin.fn_get_health_status &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-health-status-transact-sql)|Systemfunktion, die die aggregierte Anzahl der Fehler zurückgibt, die von den erweiterten Ereignissen für einen bestimmten Zeitraum protokolliert wurden|  
|[Überwachen von SQL Server Managed Backup für Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)|Erweiterte Ereignisse für die Überwachung, E-Mail-Benachrichtigung von Fehlern und Warnungen, richtlinienbasierte SQL Server-Verwaltung für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
  
#### <a name="backup-strategy"></a>Sicherungsstrategie  
 **Von verwendete Sicherungsstrategie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]:**  
  
 Der Typ der geplanten Sicherungen und die Sicherungshäufigkeit richten sich nach der Arbeitsauslastung der Datenbank. Anhand der Beibehaltungsdauereinstellungen wird ermittelt, wie lange eine Sicherungsdatei im Speicher gehalten werden soll. Außerdem wird die Wiederherstellbarkeit der Datenbank zu einem bestimmten Zeitpunkt innerhalb der Beibehaltungsdauer geprüft.  
  
 **Sicherungscontainer und Dateinamenkonventionen:**  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] benennt den Windows Azure-Speichercontainer nach dem SQL Server-Instanznamen für alle Datenbanken mit Ausnahme von Verfügbarkeitsdatenbanken.  Für Verfügbarkeitsdatenbanken wird die Verfügbarkeitsgruppen-GUID für die Benennung des Windows Azure-Speichercontainers verwendet.  
  
 Die Sicherungsdatei für nicht-verfügbarkeitsdatenbanken werden mithilfe der folgenden Konvention benannt: Der Name wird erstellt, mit der ersten 40 Zeichen des Datenbanknamens, der Datenbank-GUID ohne das "-", und dem Zeitstempel. Der Unterstrich wird zwischen Segmenten als Trennzeichen eingefügt. Als Dateierweiterung wird **.bak** bei einer vollständigen Sicherung und **.log** für Protokollsicherungen verwendet. Bei Datenbanken in Verfügbarkeitsgruppen gilt neben der oben beschriebenen Dateinamenskonvention, dass nach den 40 Zeichen des Datenbanknamens die GUID der Verfügbarkeitsgruppen-Datenbank angehängt wird. Der Wert für die GUID der Verfügbarkeitsgruppen-Datenbank entspricht dem group_database_id-Wert in sys.databases.  
  
 **Vollständige Datenbanksicherung:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Agent plant eine vollständige datenbanksicherung aus, wenn eine der folgenden Bedingungen wahr ist.  
  
-   Eine Datenbank wird zum ersten Mal für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] aktiviert, oder [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] wird mit den Standardeinstellungen auf Instanzebene aktiviert.  
  
-   Das Anwachsen der Protokollgröße seit der letzten vollständigen Datenbanksicherung entspricht 1 GB oder mehr.  
  
-   Das maximale Zeitintervall von einer Woche seit der letzten vollständigen Datenbanksicherung wurde überschritten.  
  
-   Die Protokollkette ist unterbrochen. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] prüft in regelmäßigen Abständen, ob die Protokollkette intakt ist, indem die erste und die letzte LSN der Sicherungsdateien miteinander verglichen werden. Sollte die Protokollkette aus irgendeinem Grund unterbrochen sein, plant [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] eine vollständige Datenbanksicherung. Die häufigste Ursache für die Unterbrechung einer Protokollkette ist ein Sicherungsbefehl, der entweder mit Transact-SQL oder über eine Sicherungsaufgabe in SQL Server Management Studio ausgeführt wurde.  Weitere häufige Szenarien sind das versehentliche Löschen der Sicherungsprotokolldateien oder das versehentliche Überschreiben von Sicherungen.  
  
 **Transaktionsprotokollsicherung:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] plant eine protokollsicherung, wenn eine der folgenden Aussagen zutrifft:  
  
-   Es wurde kein Protokollsicherungsverlauf gefunden. Dies trifft in der Regel dann zu, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] das erste Mal aktiviert wird.  
  
-   Der belegte Speicher für die Transaktionsprotokolle beträgt 5 MB oder mehr.  
  
-   Das maximale Zeitintervall von 2 Stunden seit der letzten Protokollsicherung wurde erreicht.  
  
-   Immer, wenn die Transaktionsprotokollsicherung hinter einer vollständigen Datenbanksicherung zurückliegt. Das Ziel besteht darin, die Protokollkette vor der vollständigen Sicherung zu halten.  
  
#### <a name="retention-period-settings"></a>Beibehaltungsdauereinstellungen  
 Beim Aktivieren der Sicherung müssen Sie die Beibehaltungsdauer in Tagen festlegen: Der Mindestwert ist 1 Tag und Maximalwert ist 30 Tage.  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] bewertet anhand der Beibehaltungsdauereinstellungen die Wiederherstellbarkeit der Datenbank zu einem bestimmten Zeitpunkt im angegebenen Zeitraum, um zu ermitteln, welche Sicherungsdateien behalten und welche gelöscht werden sollen. Über backup_finish_date der Sicherung wird die in den Beibehaltungsdauereinstellungen angegebene Zeit ermittelt und abgeglichen.  
  
#### <a name="important-considerations"></a>Wichtige Überlegungen  
 Es müssen einige Überlegungen getroffen werden, um die entsprechenden Auswirkungen auf die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Vorgänge der intelligenten Sicherung zu verstehen. Sie sind im Folgenden aufgeführt:  
  
-   Wenn für eine Datenbank ein Auftrag für eine vollständige Datenbanksicherung ausgeführt wird, wartet [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] , bis der aktuelle Auftrag abgeschlossen ist, bevor eine weitere vollständige Datenbanksicherung für dieselbe Datenbank ausgeführt wird. Entsprechend kann nur eine Transaktionsprotokollsicherung zu einem bestimmten Zeitpunkt ausgeführt werden. Eine vollständige Datenbanksicherung und eine Transaktionsprotokollsicherung können jedoch gleichzeitig ausgeführt werden. Fehler werden als erweiterte Ereignisse protokolliert.  
  
-   Wenn mehr als 10 gleichzeitige vollständige Datenbanksicherungen geplant werden, wird über den Debug-Kanal der erweiterten Ereignisse eine Warnung ausgegeben. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verwaltet dann eine Prioritätswarteschlange für die verbliebenen zu sichernden Datenbanken, bis alle Sicherungen geplant und abgeschlossen sind.  
  
###  <a name="support_limits"></a> Einschränkungen bei der Unterstützung  
 Für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] gelten die folgenden Einschränkungen:  
  
-   [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Agent unterstützt nur: Vollständige Sicherungen und Protokollsicherungen.  Die Dateisicherungsautomatisierung wird nicht unterstützt.  
  
-   [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Vorgänge werden derzeit unterstützt unter Verwendung von Transact-SQL. Die Überwachung und Problembehandlung kann mithilfe von erweiterten Ereignissen erfolgen. Die PowerShell- und SMO-Unterstützung beschränkt sich auf die Konfiguration des Speichers und der Beibehaltungsdauer-Standardeinstellungen einer SQL-Server-Instanz sowie die Überwachung des Sicherungsstatus und der Gesamtintegrität auf der Basis der richtlinienbasierten SQL Server-Verwaltung.  
  
-   Systemdatenbanken werden nicht unterstützt.  
  
-   Der Windows Azure-BLOB-Speicherdienst ist die einzige Möglichkeit zum Speichern von Sicherungen. Sicherungen auf Datenträger oder Band werden nicht unterstützt.  
  
-   Aktuell ist die maximale Dateigröße, die für ein Seiten-BLOB im Windows Azure-Speicher zulässig ist, 1 TB. Sicherungsdateien größer als 1 TB schlagen fehl. Um diese Situation zu vermeiden, wird für große Datenbanken die Verwendung der Komprimierung und das Testen der Sicherungsdateigröße vor dem Installieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] empfohlen. Sie können entweder testen, indem Sie auf einem lokalen Datenträger sichern, oder manuell mit Windows Azure-Speicher und der Transact-SQL-Anweisung `BACKUP TO URL`. Weitere Informationen finden Sie unter [SQL Server Backup to URL](sql-server-backup-to-url.md).  
  
-   Wiederherstellungsmodelle: Es werden nur Datenbanken mit vollständigen oder massenprotokollierten Modell unterstützt.  Datenbanken mit einfachem Wiederherstellungsmodell werden nicht unterstützt.  
  
-   Für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] gelten ggf. bestimmte Einschränkungen, wenn eine Konfiguration in Kombination mit anderen Technologien erfolgt, die Sicherungen, Hochverfügbarkeit und eine Wiederherstellung im Notfall unterstützen. Weitere Informationen finden Sie unter [SQL Server Managed Backup für Windows Azure: Interoperabilität und Koexistenz](../../database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
|||  
|-|-|  
|**Taskbeschreibungen**|**Thema**|  
|Grundlegende Aufgaben wie die Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für eine Datenbank, die Konfiguration der Standardeinstellungen auf Instanzebene, die Deaktivierung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf Instanz- oder Datenbankebene, das Pausieren oder Neustarten von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]|[SQL Server Managed Backup für Microsoft Azure: Beibehaltungs- und Speichereinstellungen](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|  
|**Tutorial:** Schritt-für-Schritt-Anweisungen zum Konfigurieren und Überwachen [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Einrichten von SQL Server Managed Backup für Microsoft Azure](enable-sql-server-managed-backup-to-microsoft-azure.md)|  
|**Tutorial:** Schritt-für-Schritt-Anweisungen zum Konfigurieren und Überwachen [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für Datenbanken in Verfügbarkeitsgruppen.|[Einrichten von SQL Server Managed Backup für Microsoft Azure für Verfügbarkeitsgruppen](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)|  
|Tools und Konzepte und Aufgaben zur Überwachung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Überwachen von SQL Server Managed Backup für Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)|  
|Tools und Schritte zur [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Problembehandlung|[Problembehandlung für SQL Server Managed Backup für Microsoft Azure](../../database-engine/troubleshooting-sql-server-managed-backup-to-windows-azure.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Sicherung und-Wiederherstellung mit dem Windows Azure-Blob-Speicherdienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
 [SQL Server Backup to URL](sql-server-backup-to-url.md)   
 [SQL Server Managed Backup für Windows Azure: Interoperabilität und Koexistenz](../../database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)   
 [Problembehandlung für SQL Server Managed Backup für Microsoft Azure](../../database-engine/troubleshooting-sql-server-managed-backup-to-windows-azure.md)  
  
  
