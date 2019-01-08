---
title: Das Transaktionsprotokoll (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/04/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], about
- databases [SQL Server], transaction logs
- logs [SQL Server], transaction logs
ms.assetid: d7be5ac5-4c8e-4d0a-b114-939eb97dac4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1b4a175ad850ccbb0711a0997c3658cf01497686
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52807012"
---
# <a name="the-transaction-log-sql-server"></a>Das Transaktionsprotokoll [SQL Server]
  Jede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank verfügt über ein Transaktionsprotokoll, in dem alle Transaktionen sowie die Datenbankänderungen aufgezeichnet werden, die von den einzelnen Transaktionen vorgenommen werden. Um das Überlaufen des Transaktionsprotokolls zu verhindern, muss es in regelmäßigen Abständen gekürzt werden. Einige Faktoren können die Protokollkürzung jedoch verzögern, sodass die Überwachung der Protokollgröße wichtig ist. Einige Vorgänge lassen sich minimal protokollieren, um deren Auswirkung auf die Größe des Transaktionsprotokolls zu reduzieren.  
  
 Das Transaktionsprotokoll ist eine wichtige Komponente der Datenbank und wird im Falle eines Systemfehlers ggf. benötigt, um einen konsistenten Status der Datenbank wiederherzustellen. Das Transaktionsprotokoll sollte nur dann gelöscht oder verschoben werden, wenn die Auswirkungen dieses Vorgangs vollständig bekannt sind.  
  
> [!NOTE]  
>  Einige bekannte gute Ausgangspunkte für das Anwenden von Transaktionsprotokollen während der Datenbankwiederherstellung werden durch Prüfpunkte vorgegeben. Weitere Informationen finden Sie unter [Datenbankprüfpunkte &#40;SQL Server&#41;](database-checkpoints-sql-server.md).  
  
 **In diesem Thema:**  
  
-   [Vorteile: Vorgänge, die durch das Transaktionsprotokoll unterstützt](#Benefits)  
  
-   [Kürzung des Transaktionsprotokolls](#Truncation)  
  
-   [Faktoren, die die Protokollkürzung verzögern können](#FactorsThatDelayTruncation)  
  
-   [Vorgänge, die minimal protokolliert werden können](#MinimallyLogged)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="Benefits"></a> Vorteile: Vom Transaktionsprotokoll unterstützte Operationen  
 Das Transaktionsprotokoll unterstützt die folgenden Vorgänge:  
  
-   Wiederherstellen einzelner Transaktionen.  
  
-   Wiederherstellen aller unvollständigen Transaktionen, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestartet wird.  
  
-   Ausführen eines Rollforwards für eine wiederhergestellte Datenbank, Datei, Dateigruppe oder Seite bis zu dem Punkt, an dem der Fehler aufgetreten ist.  
  
-   Unterstützen der Transaktionsreplikation.  
  
-   Lösungen zur Unterstützung von Hochverfügbarkeit und Notfallwiederherstellung: [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], Datenbankspiegelung und Protokollversand.  
  
##  <a name="Truncation"></a> Kürzung des Transaktionsprotokolls  
 Durch das Kürzen des Protokolls wird in der Protokolldatei Speicherplatz freigegeben, der vom Transaktionsprotokoll erneut verwendet werden kann. Die Protokollkürzung ist wichtig, um ein Auffüllen des Protokolls verhindern zu können. Durch die Protokollkürzung werden inaktive virtuelle Protokolldateien aus dem logischen Transaktionsprotokoll einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank gelöscht. Zudem wird Speicherplatz im logischen Protokoll zur Wiederverwendung durch das physische Transaktionsprotokoll freigegeben. Wird ein Transaktionsprotokoll nicht gekürzt, füllt sich dadurch möglicherweise der gesamte Speicherplatz des Datenträgers auf, der den zugehörigen physischen Protokolldateien zugeordnet ist.  
  
 Um dieses Problem zu vermeiden, erfolgt die Kürzung automatisch nach den folgenden Ereignissen, sofern die Protokollkürzung nicht aus bestimmten Gründen verzögert wird:  
  
-   Unter dem einfachen Wiederherstellungsmodell, nach einem Prüfpunkt.  
  
-   Unter dem vollständigen oder massenprotokollierten Wiederherstellungsmodell, wenn ein Prüfpunkt seit der vorherigen Sicherung ausgelöst wurde, erfolgt die Kürzung nach einer Protokollsicherung (sofern es sich nicht um eine Kopiesicherung handelt).  
  
 Weitere Informationen finden Sie unter [Faktoren, die die Protokollkürzung verzögern können](#FactorsThatDelayTruncation)weiter unten in diesem Thema.  
  
> [!NOTE]  
>  Die Protokollkürzung verringert nicht die Größe einer physischen Protokolldatei. Sie müssen zum Reduzieren der physischen Größe einer physischen Protokolldatei die Protokolldatei verkleinern. Informationen zum Verkleinern der Größe der physischen Protokolldatei finden Sie unter [Verwalten der Größe der Transaktionsprotokolldatei](manage-the-size-of-the-transaction-log-file.md).  
  
##  <a name="FactorsThatDelayTruncation"></a> Faktoren, die die Protokollkürzung verzögern können  
 Bleiben Protokolldatensätze lange aktiv, verzögert sich die Transaktionsprotokollkürzung. Dabei kann sich das Transaktionsprotokoll potenziell auffüllen.  
  
> [!IMPORTANT]  
>  Informationen zum Umgang mit einem voll aufgefüllten Transaktionsprotokoll finden Sie unter [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](troubleshoot-a-full-transaction-log-sql-server-error-9002.md).  
  
 Die Protokollkürzung kann durch verschiedene Faktoren verzögert werden. Sie können ermitteln, wodurch die Protokollkürzung verhindert wird, indem Sie die Spalten **log_reuse_wait** und **log_reuse_wait_desc** der Katalogsicht [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) abfragen. In der folgenden Tabelle werden die Werte dieser Spalten beschrieben.  
  
|log_reuse_wait value|log_reuse_wait_desc value|Description|  
|----------------------------|----------------------------------|-----------------|  
|0|NOTHING|Derzeit ist mindestens eine wiederverwendbare virtuelle Protokolldatei vorhanden.|  
|1|CHECKPOINT|Seit der letzten Protokollkürzung ist kein Prüfpunkt aufgetreten, oder der Kopf des Protokolls wurde noch nicht über eine virtuelle Protokolldatei hinaus verschoben. (Alle Wiederherstellungsmodelle)<br /><br /> Dies ist ein häufiger Grund für das verzögerte Kürzen von Protokollen. Weitere Informationen finden Sie unter [Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md).|  
|2|LOG_BACKUP|Eine Protokollsicherung ist erforderlich, bevor das Transaktionsprotokoll gekürzt werden kann. (nur vollständiges bzw. massenprotokolliertes Wiederherstellungsmodell)<br /><br /> Bei Abschluss der nächsten Protokollsicherung wird möglicherweise ein Teil des Protokollspeicherplatzes zur Wiederverwendung freigegeben.|  
|3|ACTIVE_BACKUP_OR_RESTORE|Es findet gerade eine Datensicherung oder eine Wiederherstellung statt (alle Wiederherstellungsmodelle).<br /><br /> Verhindert eine Datensicherung die Protokollkürzung, kann das unmittelbare Problem u. U. durch Abbrechen des Sicherungsvorgangs behoben werden.|  
|4|ACTIVE_TRANSACTION|Eine Transaktion ist aktiv (alle Wiederherstellungsmodelle).<br /><br /> Möglicherweise ist beim Starten der Protokollsicherung eine Transaktion mit langer Ausführungszeit vorhanden. In diesem Fall ist zum Freigeben von Speicherplatz möglicherweise eine weitere Protokollsicherung erforderlich. Beachten Sie, dass eine lang andauernde Transaktionen verhindern die protokollkürzung unter allen Wiederherstellungsmodellen, einschließlich des einfachen Wiederherstellungsmodells, unter dem im Allgemeinen das Transaktionsprotokoll an jedem automatischen Prüfpunkt gekürzt wird.<br /><br /> Eine Transaktion wird verzögert. Eine *verzögerte Transaktion* ist tatsächlich eine aktive Transaktion, deren Rollback aufgrund einer nicht verfügbaren Ressource blockiert ist. Weitere Informationen zu den Ursachen für verzögerte Transaktionen und zum Auflösen ihres verzögerten Zustands finden Sie unter [Verzögerte Transaktionen &#40;SQL Server&#41;](../backup-restore/deferred-transactions-sql-server.md). <br /><br />Lang andauernde Transaktionen können auch das Transaktionsprotokoll von „tempdb“ füllen. „tempdb“ wird implizit von Benutzertransaktionen für interne Objekte wie z.B. Arbeitstabellen zum Sortieren, Arbeitsdateien für Hashverfahren, Cursorarbeitstabellen und Zeilenversionsverwaltung verwendet. Auch wenn die Benutzertransaktion enthält nur Lesen von Daten (SELECT-Abfragen), möglicherweise interne Objekte erstellt und unter Benutzertransaktionen verwendet werden. Anschließend kann das tempdb-Transaktionsprotokoll gefüllt werden.|  
|5|DATABASE_MIRRORING|Die Datenbankspiegelung wurde angehalten, oder im Modus für hohe Leistung befindet sich die Spiegeldatenbank deutlich hinter der Prinzipaldatenbank. (nur vollständiges Wiederherstellungsmodell)<br /><br /> Weitere Informationen finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).|  
|6|REPLICATION|Während der Transaktionsreplikationen wurden für die Veröffentlichungen relevante Transaktionen noch immer nicht für die Verteilungsdatenbank bereitgestellt. (nur vollständiges Wiederherstellungsmodell)<br /><br /> Weitere Informationen zur Transaktionsreplikation finden Sie unter [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md).|  
|7|DATABASE_SNAPSHOT_CREATION|Eine Datenbank-Momentaufnahme wird erstellt. (Alle Wiederherstellungsmodelle)<br /><br /> Dies ist ein häufiger, im Allgemeinen jedoch nur kurz andauernder Grund für ein verzögertes Kürzen eines Protokolls.|  
|8|LOG_SCAN|Ein Protokollscan wird ausgelöst. (Alle Wiederherstellungsmodelle)<br /><br /> Dies ist ein häufiger, im Allgemeinen jedoch nur kurz andauernder Grund für ein verzögertes Kürzen eines Protokolls.|  
|9|AVAILABILITY_REPLICA|Ein sekundäres Replikat einer Verfügbarkeitsgruppe wendet Transaktionsprotokoll-Datensätze dieser Datenbank auf eine zugehörige sekundäre Datenbank an. (vollständiges Wiederherstellungsmodell)<br /><br /> Weitere Informationen finden Sie unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).|  
|10|-|Nur interne Verwendung|  
|11|-|Nur interne Verwendung|  
|12|-|Nur interne Verwendung|  
|13|OLDEST_PAGE|Ist eine Datenbank zur Verwendung von indirekten Prüfpunkten konfiguriert, ist die älteste Seite in der Datenbank u. U. älter als die Prüfpunkt-LSN. In diesem Fall kann die älteste Seite die Protokollkürzung verzögern. (Alle Wiederherstellungsmodelle)<br /><br /> Weitere Informationen zu indirekten Prüfpunkten finden Sie unter [Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md).|  
|14|OTHER_TRANSIENT|Dieser Wert wird derzeit nicht verwendet.|  
|16|XTP_CHECKPOINT|Wenn eine Datenbank eine speicheroptimierte Dateigruppe aufweist, wird das Transaktionsprotokoll möglicherweise nicht vor der Auslösung des automatischen [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -Prüfpunkts gekürzt (was immer nach Anwachsen des Protokolls um 512 MB erfolgt).<br /><br /> Hinweis: Um das Transaktionsprotokoll vor Erreichen der 512 MB-Größe zu kürzen, lösen Sie den Befehl „Checkpoint“ für die fragliche Datenbank manuell aus.|  
  
##  <a name="MinimallyLogged"></a> Vorgänge, die minimal protokolliert werden können  
 Bei der*minimalen Protokollierung* werden nur die Informationen protokolliert, die zum Wiederherstellen der Transaktion ohne Unterstützung der Zeitpunktwiederherstellung erforderlich sind. In diesem Thema werden die Vorgänge aufgeführt, die unter dem massenprotokollierten Wiederherstellungsmodell minimal protokolliert werden (sowie unter dem einfachen Wiederherstellungsmodell, es sei denn, es wird eine Sicherung ausgeführt).  
  
> [!NOTE]  
>  Die minimale Protokollierung wird für speicheroptimierte Tabellen nicht unterstützt.  
  
> [!NOTE]  
>  Unter dem vollständigen Wiederherstellungsmodell werden alle Massenvorgänge vollständig protokolliert. Sie können die Protokollierung für eine Reihe von Massenvorgängen jedoch verringern, indem Sie die Datenbank bei Massenvorgängen vorübergehend in das massenprotokollierte Wiederherstellungsmodell schalten. Die minimale Protokollierung ist effizienter als die vollständige Protokollierung und senkt die Wahrscheinlichkeit, dass ein umfangreicher Massenvorgang den verfügbaren Transaktionsprotokoll-Speicherplatz während einer Massentransaktion auffüllt. Wenn die Datenbank bei Aktivierung der minimalen Protokollierung jedoch beschädigt wird oder verloren geht, können Sie die Datenbank nicht bis zu dem Punkt wiederherstellen, an dem der Fehler aufgetreten ist.  
  
 Die folgenden Vorgänge, die unter dem vollständigen Wiederherstellungsmodell vollständig protokolliert werden, werden unter dem einfachen und massenprotokollierten Wiederherstellungsmodell minimal protokolliert:  
  
-   Massenimportvorgänge ([bcp](../../tools/bcp-utility.md), [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) und [INSERT... SELECT](/sql/t-sql/statements/insert-transact-sql)). Weitere Informationen zur minimalen Protokollierung eines Massenimports in eine Tabelle finden Sie unter [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
    > [!NOTE]  
    >  Wenn die Transaktionsreplikation aktiviert ist, werden BULK INSERT-Vorgänge auch unter dem massenprotokollierten Wiederherstellungsmodell vollständig protokolliert.  
  
-   SELECT [INTO](/sql/t-sql/queries/select-into-clause-transact-sql) -Vorgänge.  
  
    > [!NOTE]  
    >  Wenn die Transaktionsreplikation aktiviert ist, werden SELECT INTO-Vorgänge auch unter dem massenprotokollierten Wiederherstellungsmodell vollständig protokolliert.  
  
-   Teilupdates von Datentypen für hohe Werte mithilfe der .WRITE-Klausel in der [UPDATE](/sql/t-sql/queries/update-transact-sql) -Anweisung beim Einfügen oder Anfügen neuer Daten. Beachten Sie, dass die minimale Protokollierung nicht verwendet wird, wenn vorhandene Werte aktualisiert werden. Weitere Informationen zu Datentypen für hohe Werte finden Sie unter [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
-   [WRITETEXT](/sql/t-sql/queries/writetext-transact-sql) und [UPDATETEXT](/sql/t-sql/queries/updatetext-transact-sql) -Anweisung beim Einfügen oder Anfügen neuer Daten an die `text`, `ntext`, und `image` Spalten vom Typ. Beachten Sie, dass die minimale Protokollierung nicht verwendet wird, wenn vorhandene Werte aktualisiert werden.  
  
    > [!NOTE]  
    >  Die WRITETEXT-Anweisung und UPDATETEXT-Anweisung sind als veraltet markiert, sollten also in neuen Anwendungen nicht mehr verwendet werden.  
  
-   Wenn für die Datenbank das einfache oder massenprotokollierte Wiederherstellungsmodell festgelegt ist, werden einige Index-DDL-Vorgänge minimal protokolliert, unabhängig davon, ob der Vorgang offline oder online ausgeführt wird. Die minimal protokollierten Indexvorgänge sind nachfolgend aufgeführt:  
  
    -   [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) -Vorgänge (einschließlich indizierter Sichten).  
  
    -   [ALTER INDEX](/sql/t-sql/statements/alter-index-transact-sql) REBUILD- oder DBCC DBREINDEX-Vorgänge.  
  
        > [!NOTE]  
        >  Die DBCC DBREINDEX-Anweisung ist als veraltet markiert, sollte also in neuen Anwendungen nicht mehr verwendet werden.  
  
    -   Neuerstellungen neuer Heaps mit DROP INDEX (falls zutreffend).  
  
        > [!NOTE]  
        >  Aufhebungen von Indexseitenzuordnungen während eines [DROP INDEX](/sql/t-sql/statements/drop-index-transact-sql) -Vorgangs werden immer vollständig protokolliert.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 `Managing the transaction log`  
  
-   [Verwalten der Größe der Transaktionsprotokolldatei](manage-the-size-of-the-transaction-log-file.md)  
  
-   [Problembehandlung bei vollen Transaktionsprotokollen &#40;SQL Server-Fehler 9002&#41;](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
 **Sichern des Transaktionsprotokolls (vollständiges Wiederherstellungsmodell)**  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 **Wiederherstellen des Transaktionsprotokolls (vollständiges Wiederherstellungsmodell)**  
  
-  [Wiederherstellen einer Transaktionsprotokollsicherung](../backup-restore/restore-a-transaction-log-backup-sql-server.md)   
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Transaktionsdauerhaftigkeit](control-transaction-durability.md)   
 [Voraussetzungen für die minimale Protokollierung beim Massenimport](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)   
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Datenbankprüfpunkte &#40;SQL Server&#41;](database-checkpoints-sql-server.md)   
 [Anzeigen oder Ändern der Eigenschaften einer Datenbank](../databases/view-or-change-the-properties-of-a-database.md)   
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)  
  
  
