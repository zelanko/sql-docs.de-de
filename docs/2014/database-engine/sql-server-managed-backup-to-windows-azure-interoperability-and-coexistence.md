---
title: 'SQL Server Managed Backup für Windows Azure: Interoperabilität und Koexistenz | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 78fb78ed-653f-45fe-a02a-a66519bfee1b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d4d883d54a1ad933d4e248f292d9b6a222915a00
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52509134"
---
# <a name="sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence"></a>SQL Server Managed Backup für Windows Azure: Interoperabilität und Koexistenz
  In diesem Thema wird [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Interoperabilität und -Koexistenz mit mehreren Funktionen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] beschrieben. Zu diesen Funktionen gehören folgende: AlwaysOn-Verfügbarkeitsgruppen, Datenbankspiegelung, Wartungspläne für Sicherungen, Protokollversand, Ad-hoc-Sicherungen, Datenbank trennen und Datenbank löschen.  
  
### <a name="alwayson-availability-groups"></a>AlwaysOn-Verfügbarkeitsgruppen  
 AlwaysOn-Verfügbarkeitsgruppen, die als reine Azure-Lösung unterstützt Windows konfiguriert sind [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Lokale oder gemischte Konfigurationen für AlwaysOn-Verfügbarkeitsgruppen werden nicht unterstützt. Weitere Informationen und Überlegungen finden Sie unter [zum Einrichten von SQL Server Managed Backup für Windows Azure-Verfügbarkeitsgruppen](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)  
  
### <a name="database-mirroring"></a>Datenbankspiegelung  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] wird nur für die Prinzipaldatenbank unterstützt. Wenn sowohl die Prinzipaldatenbank als auch der Spiegel für die Verwendung von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] konfiguriert wurden, wird die gespiegelte Datenbank übersprungen und nicht gesichert. Bei einem Failover startet [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] allerdings den Sicherungsprozess, sobald der Spiegel den Rollenwechsel abgeschlossen hat und online ist. In diesem Fall werden die Sicherungen in einem neuen Container gespeichert. Wenn die Spiegeldatenbank nicht konfiguriert wird, um [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] im Falle eines Failovers zu verwenden, werden keine Sicherungen vorgenommen. Es wird empfohlen, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf dem Prinzipalserver und dem Spiegelserver zu konfigurieren, sodass Sicherungen im Falle eines Failovers fortgesetzt werden.  
  
> [!TIP]  
>  Wenn Sie eine gespiegelte Datenbank auf einer Instanz mit [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Standardeinstellungen erstellen, kann es von Vorteil sein, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Instanzstandards zu deaktivieren, damit sie nicht auf die gespiegelte Datenbank angewendet werden. Dann werden die Instanzstandards nach dem Konfigurieren der Prinzipal- und der Spiegeldatenbank erneut aktiviert.  
  
### <a name="maintenance-plan"></a>Wartungsplan  
 Wartungspläne für das Erstellen von Sicherungen für eine Datenbank werden nicht unterstützt, wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert wurde. Wartungspläne führen zu fehlerhaften Protokollketten, und [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ist eventuell nicht in der Lage, eine garantierte Wiederherstellbarkeit der Datenbank bei einer Wiederherstellung zu gewährleisten. Dies gilt auch, wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene aktiviert wird.  
  
> [!TIP]  
>  Wartungspläne mit Kopiesicherungen werden unterstützt, wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für dieselbe Datenbank oder Instanz konfiguriert ist.  
  
### <a name="log-shipping"></a>Protokollversand  
 Protokollversand und [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] können nicht gleichzeitig für dieselbe Datenbank konfiguriert werden. Dies würde die Wiederherstellbarkeit der Datenbank beim Verwenden der Funktionen beeinträchtigen.  
  
### <a name="ad-hoc-backups-using-transact-sql-and-sql-server-management-studio"></a>Ad-hoc-Sicherungen mit Transact-SQL und SQL Server Management Studio  
 Einmalige oder Ad-hoc-Sicherungen, die mit Transact-SQL oder SQL Server Management Studio außerhalb von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] erstellt werden, können den [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Prozess beeinträchtigen, je nachdem, was für eine Sicherung durchgeführt und welches Speichermedium verwendet wird. Protokollsicherungen in ein anderes Windows Azure-Speicherkonto als das Konto, das von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet wird, oder ein beliebiges anderes Ziel als der Windows Azure-BLOB-Speicherdienst, führen zu Fehlern in der Protokollkette. Wir empfehlen die Verwendung der [smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql) gespeicherte Prozedur zum Initiieren von einer Sicherung für Datenbanken, die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert. Sie können entweder eine vollständige Datenbank- oder eine Protokollsicherung mithilfe dieser gespeicherten Prozedur initiieren.  
  
### <a name="drop-database-and-detach-database"></a>Löschen und Trennen von Datenbanken  
 Wenn eine Datenbank, für die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert wurde, getrennt oder gelöscht wird, werden, obwohl keine weiteren Sicherungen mehr möglich sind, alle vorherigen Sicherungen im Speicher beibehalten, bis die festgelegte Beibehaltungsdauer erreicht ist. Zu diesem Zeitpunkt werden die Sicherungen gelöscht.  
  
### <a name="changes-to-recovery-model"></a>Änderungen am Wiederherstellungsmodell  
  
-   Wenn Sie das Wiederherstellungsmodell einer Datenbank von ändern **einfache** zu **vollständige** oder **Bulk-Logged**, Sie haben die Möglichkeit der Konfiguration [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Datenbank. Aus Sicht von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] wird die Datenbank wie eine neue Datenbank behandelt.  
  
-   Wenn Sie das Wiederherstellungsmodell einer Datenbank von ändern **vollständige** oder **Bulk-Logged** zu **einfache**, bei dem [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert, werden Sicherungsvorgänge werden nicht mehr geplant. Die Beibehaltungszeitraumeinstellung bleibt weiterhin aktiv, und die Sicherungsdateien verbleiben im Speicherkonto, bis die Beibehaltungsdauer abgelaufen ist. Wenn Sie die Sicherungen über diesen Zeitraum hinaus beibehalten möchten, laden Sie die Dateien entweder in ein anderes Speicherkonto oder auf ein lokales Speichermedium herunter. Die Konfigurationseinstellungen werden beibehalten und kann wiederverwendet werden, wenn das Wiederherstellungsmodell wieder auf **vollständige** oder **Bulk-Logged** erneut aus.  
  
### <a name="log-backups-using-other-backup-tools-or-custom-scripts"></a>Protokollieren von Sicherungen mithilfe anderer Sicherungstools oder benutzerdefinierter Skripts  
 Wenn zwei Sicherungen konfiguriert werden, um Protokollsicherungen für dieselbe Datenbank auszuführen, führt dies zu einer Unterbrechung der Sicherungsprotokollkette. Obwohl [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] versucht, die Unterbrechung in der Sicherungskette zu beheben, indem bei Erkennung einer Unterbrechung eine vollständige Sicherung geplant wird, müssen in der Folge regelmäßig Unterbrechnungen und Protokollsicherungen von zwei konkurrierenden Tools behandelt werden. Das kann sich negativ auf die Wiederherstellbarkeit der Datenbank auswirken, da von keinem Tool erwartet werden kann, dass es über einen vollständigen Satz aufeinander folgender Sicherungen verfügt. Obwohl dies für zwei beliebige Protokollsicherungsfunktionen oder -tools gilt, ist es hilfreich, die unten beschriebenen, spezifischen Beispiele zu berücksichtigen. Diese bilden auch die Grundlage für die Erörterung weiterer Probleme, die bei der Konfiguration von Wartungsplänen oder dem Protokollversand auftreten, wie in früheren Abschnitten dieses Themas beschrieben.  
  
 **Data Protection Manager (DPM)-basierte Sicherungen:** Microsoft Data Protection Manager können Sie vollständige und inkrementelle Sicherungen. Die inkrementellen Sicherungen sind Protokollsicherungen, die nach der Erstellung einer T-Protokollsicherung Protokollkürzungen vornehmen. Daher wird die Konfiguration von DPM und [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für dieselbe Datenbank nicht unterstützt.  
  
 **Tools von Drittanbietern oder Skripts:** Alle von Drittanbietern oder Skripts, die protokollsicherungen ausführen, zu protokollkürzungen ist inkompatibel mit [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], und wird nicht unterstützt.  
  
 Wenn man [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbankinstanz aktiviert, und Sie einer ad-hoc-Sicherung können Sie verwenden möchten die [smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql) gespeicherte Prozedur aus, wie weiter oben beschrieben. Abschnitt. Wenn Sie Sicherungen außerdem regelmäßig außerhalb von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] planen oder ausführen müssen, können Sie Kopiesicherungen verwenden.  Weitere Informationen finden Sie unter [Kopiesicherungen &#40;SQL Server&#41;](../relational-databases/backup-restore/copy-only-backups-sql-server.md).  
  
  
