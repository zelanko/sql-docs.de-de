---
title: Übersicht zu Sicherungen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], backing up data
- backups [SQL Server]
- database backups [SQL Server]
- backup types [SQL Server]
- data backups [SQL Server]
- backing up tables [SQL Server]
- database restores [SQL Server], backups
- backing up [SQL Server], about backing up
- restoring [SQL Server], backup types
- backups [SQL Server], about
- backups [SQL Server], table-level backups unsupported
ms.assetid: 09a6e0c2-d8fd-453f-9aac-4ff24a97dc1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60fbd0341c4e29c6f98cc4d5fe5a2cfabc9b703f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84959063"
---
# <a name="backup-overview-sql-server"></a>Backup Overview (SQL Server)
  Dieses Thema bietet eine Einführung in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungskomponente. Die Sicherung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank ist wichtig für den Schutz Ihrer Daten. In dieser Diskussion werden Sicherungstypen und Sicherungseinschränkungen behandelt. Darüber hinaus bietet das Thema eine Einführung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungsmedien und -Sicherungsgeräte.  
  
 **In diesem Thema:**  
  
-   [Komponenten und Konzepte](#TermsAndDefinitions)  
  
-   [Sicherungs Komprimierung](#BackupCompression)  
  
-   [Einschränkungen für Sicherungsvorgänge in SQL Server](#Restrictions)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a>Komponenten und Konzepte  
 Sichern [Verb]  
 Kopiert die Daten oder Protokolldatensätze aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank oder aus deren Transaktionsprotokoll auf ein Sicherungsmedium, z. B. einen Datenträger, um eine Datensicherung oder Protokollsicherung zu erstellen.  
  
 Sicherung [Substantiv]  
 Eine Kopie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten, die zum Wiederherstellen der Daten nach einem Fehler verwendet werden kann. Eine Sicherung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten wird auf Datenbankebene für Dateien oder Dateigruppen erstellt. Sicherungen auf Tabellenebene können nicht erstellt werden. Zusätzlich zu Datensicherungen ist beim vollständigen Wiederherstellungsmodell die Erstellung von Sicherungen des Transaktionsprotokolls erforderlich.  
  
 [Wiederherstellungsmodell](recovery-models-sql-server.md)  
 Eine Datenbankeigenschaft, die die Pflege der Transaktionsprotokolle auf einer Datenbank steuert. Es stehen drei Wiederherstellungsmodelle zur Verfügung: einfach, vollständig und massenprotokolliert. Das Wiederherstellungsmodell der Datenbank bestimmt die Sicherungs- und Wiederherstellungsanforderungen.  
  
 [restore](restore-and-recovery-overview-sql-server.md)  
 Ein aus mehreren Phasen bestehender Prozess, in dem alle Daten und Protokollseiten aus einer angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherung in eine angegebene Datenbank kopiert werden und ein Rollforward für alle Transaktionen ausgeführt wird, die in der Sicherung protokolliert sind. Dies wird erreicht, indem die Daten durch die Übernahme protokollierter Änderungen aktualisiert werden.  
  
 **Typen von Sicherungen**  
  
 [Kopiesicherung](copy-only-backups-sql-server.md)  
 Eine Sicherung zur besonderen Verwendung, die unabhängig von der normalen Sequenz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen erstellt wird.  
  
 Datensicherung  
 Eine Sicherung von Daten einer vollständigen Datenbank (Datenbanksicherung), einer partiellen Datenbank (partielle Sicherung) oder einem Satz von Datendateien oder Dateigruppen (Dateisicherung).  
  
 [Datenbanksicherung](full-database-backups-sql-server.md)  
 Eine Sicherung einer Datenbank. Vollständige Datenbanksicherungen stellen die gesamte Datenbank zum Zeitpunkt dar, an dem die Sicherung abgeschlossen wurde. Differenzielle Datenbanksicherungen enthalten nur Änderungen, die seit der letzten vollständigen Datenbanksicherung an der Datenbank vorgenommen wurden.  
  
 [Differenzielle Sicherung](full-database-backups-sql-server.md)  
 Eine Datensicherung, die auf der letzten vollständigen Sicherung einer vollständigen oder partiellen Datenbank oder einem Satz von Datendateien oder Dateigruppen ( *differenzielle Basis*) basiert und nur die Datenblöcke enthält, die sich seit der differenziellen Basis geändert haben.  
  
 Bei einer differenziellen Teilsicherung werden nur die Datenblöcke aufgezeichnet, die seit der vorherigen Teilsicherung geändert wurden, die als Basis der differenziellen Sicherung bezeichnet wird.  
  
 Vollständige Sicherung  
 Eine Datensicherung, die alle Daten in einer bestimmten Datenbank oder einem Satz von Dateigruppen oder Dateien enthält. Außerdem muss die Sicherung genügend Protokolle enthalten, um die Wiederherstellung dieser Daten zu ermöglichen.  
  
 [Protokollsicherung](transaction-log-backups-sql-server.md)  
 Eine Sicherung von Transaktionsprotokollen, die alle Protokolldatensätze enthält, die nicht in einer vorherigen Protokollsicherung gesichert wurden. (Vollständiges Wiederherstellungsmodell)  
  
 [Dateisicherung](full-file-backups-sql-server.md)  
 Eine Sicherung aller Datenbankdateien oder -dateigruppen.  
  
 [Teilsicherung](partial-backups-sql-server.md)  
 Enthält Daten aus nur einigen der Dateigruppen in einer Datenbank, einschließlich Daten in der primären Dateigruppe, alle Dateigruppen mit Lese-/Schreibzugriff und aller optional angegebenen schreibgeschützten Dateien.  
  
 **Begriffe und Definitionen für Sicherungsmedien**  
  
 [Sicherungsgerät](backup-devices-sql-server.md)  
 Ein Datenträger oder Bandmedium, auf den bzw. das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen geschrieben werden und von dem sie wiederhergestellt werden können. SQL Server-Sicherungen können auch in einen Azure Blob Storage-Dienst geschrieben werden. Das **URL**-Format wird verwendet, um das Ziel und den Namen der Sicherungsdatei anzugeben. Weitere Informationen finden Sie im Artikel zu [SQL Server-Sicherung und -Wiederherstellung mit dem Azure Blob Storage-Dienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 [Sicherungsmedien](media-sets-media-families-and-backup-sets-sql-server.md)  
 Bänder oder Datenträgerdateien, auf die Sicherungen geschrieben wurden.  
  
 [Sicherungssatz](media-sets-media-families-and-backup-sets-sql-server.md)  
 Der Sicherungsinhalt, der bei einem erfolgreichen Sicherungsvorgang einem Mediensatz hinzugefügt wird.  
  
 [Medienfamilie](media-sets-media-families-and-backup-sets-sql-server.md)  
 Sicherungen, die auf einem einzelnen, nicht gespiegelten Medium oder auf einem Satz gespiegelter Medien in einem Mediensatz erstellt wurden.  
  
 [Mediensatz](media-sets-media-families-and-backup-sets-sql-server.md)  
 Eine geordnete Auflistung von Sicherungsmedien, Bändern oder Dateien auf Datenträgern, die in mindestens einem Sicherungsvorgang mithilfe eines festen Typs sowie einer festen Anzahl von Sicherungsmedien beschrieben wurden.  
  
 [Gespiegelter Mediensatz](mirrored-backup-media-sets-sql-server.md)  
 Mehrere Kopien (Spiegel) eines Mediensatzes.  
  
##  <a name="backup-compression"></a><a name="BackupCompression"></a>Sicherungs Komprimierung  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] können Sicherungen komprimiert werden, und ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ist die Wiederherstellung komprimierter Sicherungen möglich. Weitere Informationen finden Sie unter [Sicherungskomprimierung &#40;SQL Server&#41;](backup-compression-sql-server.md).  
  
##  <a name="restrictions-on-backup-operations-in-sql-server"></a><a name="Restrictions"></a>Einschränkungen für Sicherungs Vorgänge in SQL Server  
 Eine Sicherung kann erfolgen, während die Datenbank online ist und verwendet wird. Es gelten dabei jedoch folgende Einschränkungen.  
  
### <a name="offline-data-cannot-be-backed-up"></a>Offlinedaten können nicht gesichert werden  
 Wenn im Rahmen eines Sicherungsvorgangs implizit oder explizit auf Offlinedaten verwiesen wird, tritt bei diesem Vorgang ein Fehler auf. Einige typische Fälle:  
  
-   Sie fordern eine vollständige Datenbanksicherung an, wobei eine Dateigruppe der Datenbank offline ist. Da bei der vollständigen Datenbanksicherung implizit alle Dateigruppen berücksichtigt werden, ist der Vorgang fehlerhaft.  
  
     Zum Sichern dieser Datenbank können Sie eine Dateisicherung verwenden und nur die Dateigruppen angeben, die online sind.  
  
-   Sie fordern eine Teilsicherung an, wobei eine Dateigruppe mit Lese-/Schreibzugriff offline ist. Da bei der Teilsicherung alle Dateigruppen mit Lese-/Schreibzugriff berücksichtigt werden müssen, tritt ein Fehler auf.  
  
-   Sie fordern eine Sicherung bestimmter Dateien an, wobei eine Datei nicht online ist. Dabei tritt ein Fehler auf. Wenn Sie Onlinedateien sichern möchten, können Sie die Offlinedatei in der Dateiliste auslassen und den Vorgang wiederholen.  
  
 Im Allgemeinen wird eine Protokollsicherung erfolgreich ausgeführt, selbst wenn eine oder mehrere Datendateien nicht verfügbar sind. Wenn in einer Datei jedoch massenprotokollierte Änderungen enthalten sind, die im massenprotokollierten Wiederherstellungsmodell erfolgt sind, müssen alle Dateien online sein, damit die Sicherung erfolgreich ausgeführt werden kann.  
  
### <a name="concurrency-restrictions-during-backup"></a>Einschränkungen hinsichtlich der Parallelität bei Sicherungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird ein Onlinesicherungsprozess verwendet, um das Ausführen einer Datenbanksicherung zu ermöglichen, während die Datenbank weiterhin verwendet wird. Bei einer Sicherung sind die meisten Vorgänge möglich, so sind z. B. die Anweisungen INSERT, UPDATE oder DELETE bei einem Sicherungsvorgang zulässig. Beim Versuch, einen Sicherungsvorgang zu starten, während eine Datenbankdatei erstellt oder gelöscht wird, wird der Sicherungsvorgang so lange verzögert, bis der Erstellungs- oder Löschvorgang abgeschlossen ist oder das Timeout für die Sicherung erreicht ist.  
  
 Folgende Vorgänge können nicht ausgeführt werden, während eine Datenbank oder ein Transaktionsprotokoll gesichert wird:  
  
-   Vorgänge, die die Dateiverwaltung betreffen, z. B. die ALTER DATABASE-Anweisung mit der Option ADD FILE oder REMOVE FILE.  
  
-   Vorgänge zum Verkleinern der Datenbank oder von Dateien. Dazu gehören auch Vorgänge zum automatischen Verkleinern.  
  
-   Wenn Sie versuchen, eine Datenbankdatei während des Sicherungsvorgangs zu erstellen oder zu löschen, tritt beim Erstellungs- oder Löschvorgang ein Fehler auf.  
  
 Wenn sich ein Sicherungsvorgang mit einem Dateiverwaltungsvorgang oder einem Verkleinerungsvorgang überschneidet, tritt ein Konflikt auf. Unabhängig davon, welcher am Konflikt beteiligte Vorgang zuerst begonnen hat, wartet der zweite Vorgang auf das Timeout der Sperre, die vom ersten Vorgang festgelegt wurde. (Der Timeoutzeitraum wird durch eine Timeouteinstellung für die Sitzung gesteuert.) Wenn die Sperre während des Timeoutzeitraums aufgehoben wird, wird der zweite Vorgang fortgesetzt. Wenn das Timeout für die Sperre eintritt, erzeugt der zweite Vorgang einen Fehler.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So arbeiten Sie mit Sicherungsgeräten und Sicherungsmedien**  
  
-   [Definieren eines logischen Sicherungsmediums für eine Datenträgerdatei &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [Angeben eines Datenträgers oder ein Bands als Sicherungsziel &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [Löschen eines Sicherungsmediums &#40;SQL Server&#41;](delete-a-backup-device-sql-server.md)  
  
-   [Festlegen des Ablaufdatums für eine Sicherung &#40;SQL Server&#41;](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [Anzeigen der Inhalte eines Sicherungsbands oder einer -datei &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Anzeigen der Daten und Protokolldateien in einem Sicherungssatz &#40;SQL Server&#41;](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [Wiederherstellung einer Sicherung von einem Medium &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)  
  
-   [Tutorial: SQL Server-Sicherung und -Wiederherstellung mit dem Azure Blob Storage-Dienst](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
 **So erstellen Sie eine Sicherung**  
  
> [!NOTE]  
>  Verwenden Sie für Teilsicherungen oder Kopiesicherungen die [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) -Anweisung mit der Option PARTIAL bzw. COPY_ONLY.  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   [Sichern von Dateien und Dateigruppen &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)  
  
-   [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
-   [Sichern des Transaktionsprotokolls bei beschädigter Datenbank &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [Aktivieren oder deaktivieren von Sicherungsprüfsummen während der Sicherung oder Wiederherstellung &#40;SQL Server&#41;](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [Angeben, ob ein Sicherungs- oder Wiederherstellungsvorgang fortgesetzt wird, nachdem ein Fehler festgestellt wurde &#40;SQL Server&#41;](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
-   [Einschränken der CPU-Nutzung durch die Sicherungskomprimierung mithilfe der Ressourcenkontrolle &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [Tutorial: SQL Server-Sicherung und -Wiederherstellung mit dem Azure Blob Storage-Dienst](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](back-up-and-restore-of-sql-server-databases.md)   
 [Übersicht über Wiederherstellungsvorgänge &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)   
 [Wartungspläne](../maintenance-plans/maintenance-plans.md)   
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)   
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](recovery-models-sql-server.md)  
  
  
