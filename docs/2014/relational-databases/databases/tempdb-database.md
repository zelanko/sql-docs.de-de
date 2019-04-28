---
title: tempdb-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0b1265d3ef58f6ef0946937b15411b0cb79a3c20
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916882"
---
# <a name="tempdb-database"></a>tempdb-Datenbank
  Die **tempdb** -Systemdatenbank ist eine globale Ressource, die für alle Benutzer verfügbar ist, die mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbunden sind. In der Datenbank sind die folgenden Elemente enthalten:  
  
-   Temporäre Benutzerobjekte, die explizit erstellt werden, z. B. globale oder lokale temporäre Tabellen, temporäre gespeicherte Prozeduren, Tabellenvariablen oder Cursor.  
  
-   Interne Objekte, die von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]erstellt werden, z. B. Arbeitstabellen zum Speichern von Zwischenergebnissen für Spool- und Sortiervorgänge.  
  
-   Zeilenversionen, die von Datenänderungstransaktionen in einer Datenbank generiert werden, die READ COMMITTED mit Zeilenversionsverwaltung oder Transaktionen der Momentaufnahmeisolation verwendet.  
  
-   Zeilenversionen, die von Datenänderungstransaktionen für Funktionen, wie z. B. Onlineindexvorgänge, Multiple Active Result Sets (MARS) und AFTER-Trigger, generiert wurden.  
  
 Die Operationen in **tempdb** werden minimal protokolliert. Hierdurch kann für die Transaktion ein Rollback ausgeführt werden. **tempdb** wird bei jedem Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu erstellt, sodass das System immer mit einer bereinigten Kopie der Datenbank startet. Temporäre Tabellen und gespeicherte Prozeduren werden beim Trennen der Verbindung automatisch gelöscht; es sind keine Verbindungen aktiv, wenn das System heruntergefahren wird. Daher wird zwischen den einzelnen Sitzungen von **nichts in** tempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert. Sicherungs- und Wiederherstellungsvorgänge sind in **tempdb**nicht zulässig.  
  
## <a name="physical-properties-of-tempdb"></a>physische Eigenschaften von tempdb  
 Die folgende Tabelle listet die anfänglichen Konfigurationswerte der **tempdb** -Daten- und Protokolldateien auf. Die Größe dieser Dateien kann sich in den verschiedenen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geringfügig unterscheiden.  
  
|Datei|Logischer Name (logical name)|Physischer Name (physical name)|Dateivergrößerung (file growth)|  
|----------|------------------|-------------------|-----------------|  
|Primäre Daten|tempdev|tempdb.mdf|Automatische Vergrößerung um 10 Prozent, bis der Datenträger voll ist|  
|Log|templog|templog.ldf|Automatische Vergrößerung um 10 Prozent bis maximal 2 TB|  
  
 Die Größe des **Tempdb** kann die Leistung eines Systems beeinträchtigen. Z. B. wenn die **Tempdb** ist zu klein, die systemverarbeitung ist möglicherweise zu systemverarbeitung mit anfallenden die Datenbank zur Unterstützung von den Anforderungen Ihrer Workload jedes Mal, den Sie starten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können diesen zusätzlichen Aufwand vermeiden, durch Erhöhen der Größe der **Tempdb**.  
  
## <a name="performance-improvements-in-tempdb"></a>Leistungsverbesserungen in tempdb  
 Die Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tempdb **wurde in** folgendermaßen verbessert:  
  
-   Temporäre Tabellen und Tabellenvariablen können zwischengespeichert werden. Das Zwischenspeichern ermöglicht das sehr schnelle Ausführen von Vorgängen zum Löschen und Erstellen der temporären Objekte und reduziert das Auftreten von Seitenzuordnungskonflikten.  
  
-   Das Latchprotokoll für Seitenzuordnungen wurde verbessert. Dadurch wird die Anzahl der verwendeten UP-Latches (Update) reduziert.  
  
-   Der Protokollierungsaufwand für **tempdb** wurde reduziert. Dadurch wird die für die **tempdb** -Protokolldatei verwendete Datenträger-E/A-Bandbreite reduziert.  
  
-   Der Algorithmus für die Zuordnung von gemischten Seiten in **Tempdb** wurde verbessert.  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>Verschieben der tempdb-Daten- und -Protokolldateien  
 Weitere Informationen zum Verschieben der **tempdb** -Daten- und -Protokolldateien finden Sie unter [Verschieben von Systemdatenbanken](system-databases.md).  
  
### <a name="database-options"></a>Datenbankoptionen  
 Die folgende Tabelle nennt die Standardwerte für die einzelnen Datenbankoptionen in der **tempdb** -Datenbank und gibt an, ob die entsprechende Option geändert werden kann. Zum Anzeigen der aktuellen Einstellungen dieser Optionen verwenden Sie die Katalogsicht [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Datenbankoption|Standardwert|Kann geändert werden.|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Ja|  
|ANSI_NULL_DEFAULT|OFF|Ja|  
|ANSI_NULLS|OFF|Ja|  
|ANSI_PADDING|OFF|Ja|  
|ANSI_WARNINGS|OFF|Ja|  
|ARITHABORT|OFF|Ja|  
|AUTO_CLOSE|OFF|Nein|  
|AUTO_CREATE_STATISTICS|ON|Ja|  
|AUTO_SHRINK|OFF|Nein|  
|AUTO_UPDATE_STATISTICS|ON|Ja|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Ja|  
|CHANGE_TRACKING|OFF|Nein|  
|CONCAT_NULL_YIELDS_NULL|OFF|Ja|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Ja|  
|CURSOR_DEFAULT|GLOBAL|Ja|  
|Datenbankverfügbarkeitsoptionen|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Nein<br /><br /> Nein<br /><br /> Nein|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Ja|  
|DB_CHAINING|ON|Nein|  
|ENCRYPTION|OFF|Nein|  
|NUMERIC_ROUNDABORT|OFF|Ja|  
|PAGE_VERIFY|CHECKSUM für neue Installationen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NONE für Upgrades von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Ja|  
|PARAMETERIZATION|SIMPLE|Ja|  
|QUOTED_IDENTIFIER|OFF|Ja|  
|READ_COMMITTED_SNAPSHOT|OFF|Nein|  
|RECOVERY|SIMPLE|Nein|  
|RECURSIVE_TRIGGERS|OFF|Ja|  
|Service Broker-Optionen|ENABLE_BROKER|Ja|  
|TRUSTWORTHY|OFF|Nein|  
  
 Eine Beschreibung dieser Datenbankoptionen finden Sie unter [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
## <a name="restrictions"></a>Restrictions  
 Die folgenden Operationen können mit der **tempdb** -Datenbank nicht ausgeführt werden:  
  
-   Hinzufügen von Dateigruppen.  
  
-   Sichern und Wiederherstellen der Datenbank.  
  
-   Ändern der Sortierung. Die Standardsortierung entspricht der Serversortierung.  
  
-   Ändern des Datenbankbesitzers Der Besitzer von**tempdb** ist **sa**.  
  
-   Erstellen einer Datenbankmomentaufnahme.  
  
-   Löschen der Datenbank.  
  
-   Löschen des **guest** -Benutzers aus der Datenbank.  
  
-   Aktivieren von Change Data Capture  
  
-   Teilnehmen an der Datenbankspiegelung.  
  
-   Entfernen der primären Dateigruppe, der primären Datendatei oder der Protokolldatei.  
  
-   Umbenennen der Datenbank oder der primären Dateigruppe.  
  
-   Ausführen von DBCC CHECKALLOC.  
  
-   Ausführen von DBCC CHECKCATALOG.  
  
-   Versetzen der Datenbank in den OFFLINE-Modus.  
  
-   Versetzen der Datenbank oder der primären Dateigruppe in den READ_ONLY-Modus.  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer ist berechtigt, temporäre Objekte in tempdb zu erstellen. Benutzer haben nur Zugriff auf ihre eigenen Objekte, es sei denn, ihnen wurden zusätzliche Berechtigungen zugewiesen. Die CONNECT-Berechtigung für tempdb kann widerrufen werden, um Benutzer daran zu hindern, die tempdb-Datenbank zu verwenden. Von diesem Schritt wird jedoch abgeraten, da einige Routinevorgänge auf die Verwendung von tempdb angewiesen sind.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [SORT_IN_TEMPDB-Option für Indizes](../indexes/indexes.md)  
  
 [Systemdatenbanken](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Verschieben von Datenbankdateien](move-database-files.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von tempdb in SQL Server 2005](https://chresandro.wordpress.com/2014/09/29/working-with-tempdb-in-sql-server-2005/)  
  
  
