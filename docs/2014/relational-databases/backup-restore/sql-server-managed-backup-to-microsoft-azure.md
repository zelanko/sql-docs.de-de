---
title: SQL Server verwaltete Sicherung in Azure | Microsoft-Dokumentation
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
ms.openlocfilehash: 5ec5e3eeb9158363e34f708d1f36355ffcb06c6c
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154664"
---
# <a name="sql-server-managed--backup-to-azure"></a>SQL Server verwaltete Sicherung in Azure
  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]verwaltet und automatisiert SQL Server Sicherungen im Azure BLOB Storage-Dienst. Die von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verwendete Sicherungsstrategie richtet sich nach dem Beibehaltungszeitraum und der Arbeitsauslastung der Datenbank (Transaktionsvolumen). [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] unterstützt die Wiederherstellung zu einem bestimmten Zeitpunkt für den angegebenen Beibehaltungszeitraum.   
[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] kann auf Datenbankebene oder auf Instanzebene aktiviert werden, um alle Datenbanken in der Instanz von SQL Server zu verwalten. Der SQL Server kann lokal oder in gehosteten Umgebungen wie dem virtuellen Azure-Computer ausgeführt werden. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]wird für SQL Server empfohlen, die auf Azure Virtual Machines ausgeführt werden.  
  
## <a name="benefits-of-automating-sql-server-backup-using-includess_smartbackupincludesss-smartbackup-mdmd"></a>Vorteile der Automatisierung der SQL Server-Sicherung mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
-   Für die Automatisierung von Sicherungen für mehrere Datenbanken sind derzeit die Entwicklung einer Sicherungsstrategie, das Schreiben von eigenem Code und eine Planung der Sicherungen erforderlich. Mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] müssen Sie nur die Beibehaltungsdauereinstellungen und den Speicherort angeben. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]plant, führt und verwaltet die Sicherungen.  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] kann auf Datenbankebene konfiguriert werden oder mit den Standardeinstellungen für eine SQL Server-Instanz. Die Automatisierung der Sicherung [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] mit bietet folgende Vorteile:  
  
    -   Durch die Festlegung der Standardwerte auf Instanzebene können Sie diese Einstellungen auf jede nachfolgend erstellte Datenbank anwenden. Damit vermeiden Sie das Risiko, dass neue Datenbanken nicht gesichert werden und Daten verloren gehen.  
  
    -   Durch die Aktivierung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] und die Festlegung der Beibehaltungsdauer auf Datenbankebene können Sie die Standardeinstellungen auf Instanzebene überschreiben. So können Sie die Wiederherstellbarkeit einer spezifischen Datenbank präziser steuern.  
  
-   Mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] müssen Sie weder den Sicherungstyp noch die Sicherungshäufigkeit für eine Datenbank angeben.  Sie geben die Beibehaltungs Dauer an [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] und bestimmen den Typ und die Häufigkeit von Sicherungen für eine Datenbank, in der die Sicherungen im Azure-BLOB-Speicherdienst gespeichert werden. Weitere Informationen zu den Kriterien [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] , die von verwendet werden, um die Sicherungsstrategie zu erstellen, finden Sie im Abschnitt [Komponenten und Konzepte](#Concepts) in diesem Thema.  
  
-   Wenn die Verwendung der Verschlüsselung konfiguriert ist, haben Sie zusätzliche Sicherheit für Sicherungsdaten. Weitere Informationen finden Sie unter [Backup Encryption](backup-encryption.md) .  
  
 Weitere Informationen zu den Vorteilen der Verwendung von Azure BLOB Storage für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherungen finden Sie unter [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) .  
  
## <a name="terms-and-definitions"></a>Begriffe und Definitionen  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
 Eine SQL Server-Funktion zur Automatisierung von Datenbanksicherungen und zur Verwaltung der Sicherungen auf Basis der Beibehaltungsdauer.  
  
 Beibehaltungsdauer  
 Anhand der Beibehaltungsdauer ermittelt [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], welche Sicherungsdateien im Speicher behalten werden sollen, damit eine Datenbank zu einem gezielten Zeitpunkt innerhalb des angegebenen Zeitraums wiederhergestellt werden kann.  Die unterstützten Werte liegen im Bereich zwischen 1 und 30 Tagen.  
  
 Protokollkette  
 Eine fortlaufende Abfolge von Protokollsicherungen wird als Protokollkette bezeichnet. Eine Protokollkette beginnt mit einer vollständigen Sicherung der Datenbank.  
  
##  <a name="Concepts"></a>Anforderungen, Konzepte und Komponenten  
  
  
###  <a name="Security"></a> Berechtigungen  
 Transact-SQL ist die Hauptschnittstelle für die Konfiguration und Überwachung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Im Allgemeinen sind zum Ausführen der gespeicherten Konfigurations Prozeduren **db_backupoperator** Daten Bank Rolle mit **ALTER ANY CREDENTIAL** - `EXECUTE` Berechtigungen und Berechtigungen für die gespeicherte Prozedur **sp_delete_backuphistory** erforderlich.  Gespeicherte Prozeduren und Funktionen zur Überprüfung von Informationen erfordern in der Regel `Execute`-Berechtigungen für die gespeicherte Prozedur bzw. `Select`-Berechtigungen für die Funktion.  
  
###  <a name="Prereqs"></a> Erforderliche Komponenten  
 **Voraussetzungen:**  
  
 **Azure Storage Dienst** wird von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] zum Speichern der Sicherungsdateien verwendet.    Die Konzepte, Strukturen und Anforderungen für die Erstellung eines Azure-Speicher Kontos werden ausführlich im Abschnitt [Einführung in wichtige Komponenten und Konzepte](sql-server-backup-to-url.md#intorkeyconcepts) des Themas **SQL Server Backup to URL** erläutert.  
  
 **SQL** -Anmelde Informationen werden verwendet, um die Informationen zu speichern, die für die Authentifizierung beim Azure Storage-Konto erforderlich sind. In Objekt mit den SQL-Anmeldeinformationen werden der Kontoname und der Zugriffsschlüssel gespeichert. Weitere Informationen finden Sie im Abschnitt [Einführung in wichtige Komponenten und Konzepte](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) des Themas **SQL Server Backup to URL** . Eine exemplarische Vorgehensweise zum Erstellen von SQL-Anmelde Informationen zum Speichern von Azure Storage Authentifizierungsinformationen finden [Sie unter Lektion 2: Erstellen Sie eine SQL Server](../../tutorials/lesson-2-create-a-sql-server-credential.md)Anmelde Informationen.  
  
###  <a name="Concepts_Components"></a>Konzepte und Schlüsselkomponenten  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ist eine Funktion zur Verwaltung der Sicherungsvorgänge. Die Metadaten werden in der **msdb** -Datenbank gespeichert, und es werden Systemaufträge zum Schreiben von vollständigen Datenbank-und Transaktionsprotokoll Sicherungen verwendet.  
  
#### <a name="components"></a>Komponenten  
 Transact-SQL ist die Hauptschnittstelle für die Interaktion mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Gespeicherte Systemprozeduren werden für die Aktivierung, Konfiguration und Überwachung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]verwendet. Systemfunktionen werden zum Abrufen vorhandener Konfigurationseinstellungen, Parameterwerte und Sicherungsdateiinformationen verwendet. Erweiterte Ereignisse dienen der Überwachung von Fehlern und Warnungen. Warnmechanismen werden über SQL Agent-Aufträge und die richtlinienbasierte Verwaltung in SQL Server aktiviert. Es folgt eine Liste der Objekte und eine Beschreibung ihrer Funktionen im Hinblick auf [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 PowerShell-Cmdlets sind ebenfalls verfügbar zur Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. SQL Server Management Studio unterstützt das Wiederherstellen von Sicherungen, die mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] erstellt wurden, über die Aufgabe **Datenbank wiederherstellen** .  
  
|||  
|-|-|  
|Systemobjekt|Beschreibung|  
|**MSDB**|Speichert die Metadaten und den Sicherungsverlauf für alle von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]erstellten Sicherungen.|  
|[smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)|Gespeicherte Systemprozedur für die Aktivierung und Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für eine Datenbank.|  
|[smart_admin.set_instance_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451009(v=sql.120).aspx)|Gespeicherte System Prozedur zum Aktivieren und Konfigurieren von Standard [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Einstellungen für die SQL Server Instanz.|  
|[smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)|Gespeicherte Systemprozedur zum Pausieren und Wiederaufnehmen von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]|  
|[smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)|Gespeicherte Systemprozedur zur Aktivierung und Konfiguration der Überwachung für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Beispiele: Aktivierung erweiterter Ereignisse, E-Mail-Einstellungen für Benachrichtigungen|  
|[smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)|Gespeicherte System Prozedur, die verwendet wird, um eine Ad-hoc-Sicherung für eine Datenbank auszuführen, die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Verwendung ohne Unterbrechung der Protokoll Kette aktiviert ist.|  
|[smart_admin.fn_backup_db_config &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-backup-db-config-transact-sql)|Eine System Funktion, die den [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] aktuellen Status und die Konfigurationswerte für eine Datenbank oder für alle Datenbanken in der Instanz zurückgibt.|  
|[smart_admin.fn_is_master_switch_on &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-is-master-switch-on-transact-sql)|Systemfunktion, die den Status des Hauptschalters zurückgibt|  
|[smart_admin.sp_get_backup_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-get-backup-diagnostics-transact-sql)|Gespeicherte Systemprozedur für die Rückgabe der von den erweiterten Ereignissen protokollierten Ereignisse|  
|[smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)|Systemfunktion, die die aktuellen Werte für die Sicherungssystemeinstellungen zurückgibt, z. B. für die Überwachung oder für Warnungs-E-Mail-Einstellungen|  
|[smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql)|Gespeicherte Prozedur zum Abrufen der verfügbaren Sicherungsoptionen für eine angegebene Datenbank bzw. für alle Datenbanken einer Instanz|  
|[smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)|Systemfunktion, die die aktuellen Einstellungen für die erweiterten Ereignisse zurückgibt|  
|[smart_admin.fn_get_health_status &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-health-status-transact-sql)|Systemfunktion, die die aggregierte Anzahl der Fehler zurückgibt, die von den erweiterten Ereignissen für einen bestimmten Zeitraum protokolliert wurden|  
|[Überwachen SQL Server verwalteten Sicherung in Azure](sql-server-managed-backup-to-microsoft-azure.md)|Erweiterte Ereignisse für die Überwachung, E-Mail-Benachrichtigung von Fehlern und Warnungen, richtlinienbasierte SQL Server-Verwaltung für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
  
#### <a name="backup-strategy"></a>Sicherungsstrategie  
 **Von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]verwendete Sicherungsstrategie:**  
  
 Der Typ der geplanten Sicherungen und die Sicherungshäufigkeit richten sich nach der Arbeitsauslastung der Datenbank. Anhand der Beibehaltungsdauereinstellungen wird ermittelt, wie lange eine Sicherungsdatei im Speicher gehalten werden soll. Außerdem wird die Wiederherstellbarkeit der Datenbank zu einem bestimmten Zeitpunkt innerhalb der Beibehaltungsdauer geprüft.  
  
 **Namenskonventionen für Sicherungs Container und Dateien:**  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]benennt den Azure Storage-Container mit dem SQL Server Instanznamen für alle Datenbanken mit Ausnahme der Verfügbarkeits Datenbanken.  Für Verfügbarkeits Datenbanken wird die Verfügbarkeits Gruppen-GUID verwendet, um den Azure Storage-Container zu benennen.  
  
 Die Sicherungsdatei für nicht-Verfügbarkeits Datenbanken wird anhand der folgenden Konvention benannt: Der Name wird mit den ersten 40 Zeichen des Datenbanknamens, der Datenbank-GUID ohne das Zeichen „-“ und dem Zeitstempel erstellt. Der Unterstrich wird zwischen Segmenten als Trennzeichen eingefügt. Als Dateierweiterung wird **.bak** bei einer vollständigen Sicherung und **.log** für Protokollsicherungen verwendet. Bei Datenbanken in Verfügbarkeitsgruppen gilt neben der oben beschriebenen Dateinamenskonvention, dass nach den 40 Zeichen des Datenbanknamens die GUID der Verfügbarkeitsgruppen-Datenbank angehängt wird. Der Wert für die GUID der Verfügbarkeitsgruppen-Datenbank entspricht dem group_database_id-Wert in sys.databases.  
  
 **Vollständige Datenbanksicherung:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] der-Agent plant eine vollständige Datenbanksicherung, wenn eine der folgenden Punkte zutrifft:  
  
-   Eine Datenbank wird zum ersten Mal für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] aktiviert, oder [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] wird mit den Standardeinstellungen auf Instanzebene aktiviert.  
  
-   Das Anwachsen der Protokollgröße seit der letzten vollständigen Datenbanksicherung entspricht 1 GB oder mehr.  
  
-   Das maximale Zeitintervall von einer Woche seit der letzten vollständigen Datenbanksicherung wurde überschritten.  
  
-   Die Protokollkette ist unterbrochen. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] prüft in regelmäßigen Abständen, ob die Protokollkette intakt ist, indem die erste und die letzte LSN der Sicherungsdateien miteinander verglichen werden. Sollte die Protokollkette aus irgendeinem Grund unterbrochen sein, plant [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] eine vollständige Datenbanksicherung. Die häufigste Ursache für die Unterbrechung einer Protokollkette ist ein Sicherungsbefehl, der entweder mit Transact-SQL oder über eine Sicherungsaufgabe in SQL Server Management Studio ausgeführt wurde.  Weitere häufige Szenarien sind das versehentliche Löschen der Sicherungsprotokolldateien oder das versehentliche Überschreiben von Sicherungen.  
  
 **Transaktionsprotokoll Sicherung:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] plant eine Protokoll Sicherung, wenn eine der folgenden Punkte zutrifft:  
  
-   Es wurde kein Protokollsicherungsverlauf gefunden. Dies trifft in der Regel dann zu, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] das erste Mal aktiviert wird.  
  
-   Der belegte Speicher für die Transaktionsprotokolle beträgt 5 MB oder mehr.  
  
-   Das maximale Zeitintervall von 2 Stunden seit der letzten Protokollsicherung wurde erreicht.  
  
-   Immer, wenn die Transaktionsprotokollsicherung hinter einer vollständigen Datenbanksicherung zurückliegt. Das Ziel besteht darin, die Protokollkette vor der vollständigen Sicherung zu halten.  
  
#### <a name="retention-period-settings"></a>Beibehaltungsdauereinstellungen  
 Bei der Aktivierung der Sicherung müssen Sie die Beibehaltungsdauer in Tagen festlegen: Mindestwert ist 1 Tag, Maximalwert ist 30 Tage.  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] bewertet anhand der Beibehaltungsdauereinstellungen die Wiederherstellbarkeit der Datenbank zu einem bestimmten Zeitpunkt im angegebenen Zeitraum, um zu ermitteln, welche Sicherungsdateien behalten und welche gelöscht werden sollen. Über backup_finish_date der Sicherung wird die in den Beibehaltungsdauereinstellungen angegebene Zeit ermittelt und abgeglichen.  
  
#### <a name="important-considerations"></a>Wichtige Überlegungen  
 Es müssen einige Überlegungen getroffen werden, um die entsprechenden Auswirkungen auf die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Vorgänge der intelligenten Sicherung zu verstehen. Sie sind im Folgenden aufgeführt:  
  
-   Wenn für eine Datenbank ein Auftrag für eine vollständige Datenbanksicherung ausgeführt wird, wartet [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] , bis der aktuelle Auftrag abgeschlossen ist, bevor eine weitere vollständige Datenbanksicherung für dieselbe Datenbank ausgeführt wird. Entsprechend kann nur eine Transaktionsprotokollsicherung zu einem bestimmten Zeitpunkt ausgeführt werden. Eine vollständige Datenbanksicherung und eine Transaktionsprotokollsicherung können jedoch gleichzeitig ausgeführt werden. Fehler werden als erweiterte Ereignisse protokolliert.  
  
-   Wenn mehr als 10 gleichzeitige vollständige Datenbanksicherungen geplant werden, wird über den Debug-Kanal der erweiterten Ereignisse eine Warnung ausgegeben. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verwaltet dann eine Prioritätswarteschlange für die verbliebenen zu sichernden Datenbanken, bis alle Sicherungen geplant und abgeschlossen sind.  
  
###  <a name="support_limits"></a>Support Beschränkungen  
 Für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] gelten die folgenden Einschränkungen:  
  
-   [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]der-Agent unterstützt nur Datenbanksicherungen: Vollständige Sicherungen und Protokoll Sicherungen.  Die Dateisicherungsautomatisierung wird nicht unterstützt.  
  
-   [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Vorgänge werden derzeit unterstützt unter Verwendung von Transact-SQL. Die Überwachung und Problembehandlung kann mithilfe von erweiterten Ereignissen erfolgen. Die PowerShell- und SMO-Unterstützung beschränkt sich auf die Konfiguration des Speichers und der Beibehaltungsdauer-Standardeinstellungen einer SQL-Server-Instanz sowie die Überwachung des Sicherungsstatus und der Gesamtintegrität auf der Basis der richtlinienbasierten SQL Server-Verwaltung.  
  
-   Systemdatenbanken werden nicht unterstützt.  
  
-   Azure BLOB Storage-Dienst ist die einzige unterstützte Option zum Speichern von Sicherungen. Sicherungen auf Datenträger oder Band werden nicht unterstützt.  
  
-   Derzeit beträgt die maximal zulässige Dateigröße für ein seitenblob in Azure Storage 1 TB. Sicherungsdateien größer als 1 TB schlagen fehl. Um diese Situation zu vermeiden, wird für große Datenbanken die Verwendung der Komprimierung und das Testen der Sicherungsdateigröße vor dem Installieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] empfohlen. Sie können entweder testen, indem Sie eine Sicherung auf einem lokalen Datenträger durchgeführt oder in Azure `BACKUP TO URL` Storage manuell sichern, indem Sie die Transact-SQL-Anweisung verwenden. Weitere Informationen finden Sie unter [SQL Server Backup to URL](sql-server-backup-to-url.md).  
  
-   Wiederherstellungs Modelle: Es werden nur Datenbanken unterstützt, die auf das vollständige oder das Massen protokollierte Modell  Datenbanken mit einfachem Wiederherstellungsmodell werden nicht unterstützt.  
  
-   Für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] gelten ggf. bestimmte Einschränkungen, wenn eine Konfiguration in Kombination mit anderen Technologien erfolgt, die Sicherungen, Hochverfügbarkeit und eine Wiederherstellung im Notfall unterstützen. Weitere Informationen finden [Sie unter SQL Server Managed Backup to Azure: Interoperabilität und Koexistenz](../../database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
|||  
|-|-|  
|**Aufgabenbeschreibungen**|**Thema**|  
|Grundlegende Aufgaben wie die Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für eine Datenbank, die Konfiguration der Standardeinstellungen auf Instanzebene, die Deaktivierung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf Instanz- oder Datenbankebene, das Pausieren oder Neustarten von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]|[SQL Server verwaltete Sicherung in Azure-Beibehaltungs-und Speichereinstellungen](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|  
|**Tutorial:** Schritt-für-Schritt-Anweisungen zum [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]konfigurieren und Überwachen von.|[Einrichten SQL Server verwalteten Sicherung in Azure](enable-sql-server-managed-backup-to-microsoft-azure.md)|  
|**Tutorial:** Schritt-für-Schritt-Anweisungen zum [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfigurieren und Überwachen von Datenbanken in einer Verfügbarkeits Gruppe|[Einrichten SQL Server verwalteten Sicherung in Azure für Verfügbarkeits Gruppen](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)|  
|Tools und Konzepte und Aufgaben zur Überwachung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Überwachen SQL Server verwalteten Sicherung in Azure](sql-server-managed-backup-to-microsoft-azure.md)|  
|Tools und Schritte zur [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Problembehandlung|[Problembehandlung SQL Server verwalteten Sicherung in Azure](../../database-engine/troubleshooting-sql-server-managed-backup-to-windows-azure.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
 [SQL Server Sicherung auf URL](sql-server-backup-to-url.md)   
 [SQL Server verwaltete Sicherung in Azure: Interoperabilität und Koexistenz](../../database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)   
 [Problembehandlung SQL Server verwalteten Sicherung in Azure](../../database-engine/troubleshooting-sql-server-managed-backup-to-windows-azure.md)  
  
  
