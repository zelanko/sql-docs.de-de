---
title: Master-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], about
- master database [SQL Server]
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2ef7392b4e41271bacd91b5e1a9244bbfe1c1139
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558637"
---
# <a name="master-database"></a>master-Datenbank
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In der **master** -Datenbank werden alle Systemebeneninformationen für ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System aufgezeichnet. Dazu gehören instanzweite Metadaten wie Anmeldekonten, Endpunkte, Verbindungsserver und Systemkonfigurationseinstellungen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]werden Systemobjekte nicht mehr in der **master** -Datenbank gespeichert. Stattdessen werden sie in der [Resource-Datenbank](../../relational-databases/databases/resource-database.md)gespeichert. Die **master** -Datenbank bezeichnet die Datenbank, die das Vorhandensein aller anderen Datenbanken, einschließlich der Speicherorte der Datenbankdateien, sowie die Initialisierungsinformationen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aufzeichnet. Deshalb kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht starten, wenn die **master** -Datenbank nicht verfügbar ist.  

> [!IMPORTANT]
> Für den logischen Server von Azure SQL-Datenbank gelten nur die Masterdatenbank und die tempdb-Datenbank. Weitere Informationen zum Konzept eines logischen Servers und einer logischen Masterdatenbank finden Sie unter [Was ist ein logischer Azure SQL-Server?](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases#what-is-an-azure-sql-logical-server). Eine Erläuterung von tempdb im Kontext von Azure SQL-Datenbank finden Sie unter [tempdb-Datenbank in Azure SQL-Datenbank](tempdb-database.md#tempdb-database-in-sql-database). Für die verwaltete Azure SQL-Datenbank-Instanz gelten alle Systemdatenbanken. Weitere Informationen zu verwalteten Instanzen in Azure SQL-Datenbank finden Sie unter [Was ist eine verwaltete Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
## <a name="physical-properties-of-master"></a>physische Eigenschaften der master-Datenbank  
Die folgende Tabelle zeigt die Anfangskonfigurationswerte der **master**-Daten und -Protokolldateien für SQL Server und eine verwaltete Azure SQL-Datenbank-Instanz. Die Größe dieser Dateien kann sich in den verschiedenen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geringfügig unterscheiden.  
  
|File|Logischer Name (logical name)|Physischer Name (physical name)|Dateivergrößerung (file growth)|  
|----------|------------------|-------------------|-----------------|  
|Primäre Daten|master|master.mdf|Automatische Vergrößerung um 10 Prozent, bis der Speicherplatz auf dem Datenträger erschöpft ist.|  
|Log|mastlog|mastlog.ldf|Automatische Vergrößerung um 10 %, bis der Maximalwert von 2 TB erreicht wird.|  
  
Informationen zum Verschieben der **master** -Daten und -Protokolldateien finden Sie unter [Verschieben von Systemdatenbanken](../../relational-databases/databases/move-system-databases.md).  

> [!IMPORTANT]
> Beim logischen Azure SQL-Datenbank-Server hat der Benutzer keine Kontrolle über die Größe der **master**-Datenbank.
  
### <a name="database-options"></a>Datenbankoptionen  
Die folgende Tabelle zeigt den Standardwert jeder Datenbankoption in der **master**-Datenbank für SQL Server und eine verwaltete Azure SQL-Datenbank-Instanz und gibt an, ob die Option geändert werden kann. Zum Anzeigen der aktuellen Einstellungen dieser Optionen verwenden Sie die Katalogsicht [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) .  
  
> [!IMPORTANT]
> Beim logischen Azure SQL-Datenbank-Server hat der Benutzer keine Kontrolle über diese Datenbankoptionen.

|Datenbankoption|Standardwert|Kann geändert werden.|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|ON|nein|  
|ANSI_NULL_DEFAULT|OFF|Benutzerkontensteuerung|  
|ANSI_NULLS|OFF|Benutzerkontensteuerung|  
|ANSI_PADDING|OFF|Benutzerkontensteuerung|  
|ANSI_WARNINGS|OFF|Benutzerkontensteuerung|  
|ARITHABORT|OFF|Benutzerkontensteuerung|  
|AUTO_CLOSE|OFF|nein|  
|AUTO_CREATE_STATISTICS|ON|Benutzerkontensteuerung|  
|AUTO_SHRINK|OFF|nein|  
|AUTO_UPDATE_STATISTICS|ON|Benutzerkontensteuerung|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Benutzerkontensteuerung|  
|CHANGE_TRACKING|OFF|nein|  
|CONCAT_NULL_YIELDS_NULL|OFF|Benutzerkontensteuerung|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Benutzerkontensteuerung|  
|CURSOR_DEFAULT|GLOBAL|Benutzerkontensteuerung|  
|Datenbankverfügbarkeitsoptionen|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|nein<br /><br /> nein<br /><br /> nein|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Benutzerkontensteuerung|  
|DB_CHAINING|ON|nein|  
|ENCRYPTION|OFF|nein|  
|MIXED_PAGE_ALLOCATION|ON|nein|  
|NUMERIC_ROUNDABORT|OFF|Benutzerkontensteuerung|  
|PAGE_VERIFY|CHECKSUM|Benutzerkontensteuerung|  
|PARAMETERIZATION|SIMPLE|Benutzerkontensteuerung|  
|QUOTED_IDENTIFIER|OFF|Benutzerkontensteuerung|  
|READ_COMMITTED_SNAPSHOT|OFF|nein|  
|RECOVERY|SIMPLE|Benutzerkontensteuerung|  
|RECURSIVE_TRIGGERS|OFF|Benutzerkontensteuerung|  
|Service Broker-Optionen|DISABLE_BROKER|nein|  
|TRUSTWORTHY|OFF|Benutzerkontensteuerung|  
  
Eine Beschreibung dieser Datenbankoptionen finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="restrictions"></a>Restrictions  
Die folgenden Operationen können an der **master** -Datenbank nicht ausgeführt werden:  
  
- Hinzufügen von Dateien oder Dateigruppen.  
- Ändern der Sortierung. Die Standardsortierung entspricht der Serversortierung.  
- Ändern des Datenbankbesitzers Der Besitzer von**master** ist **sa**.  
- Erstellen eines Volltextkatalogs oder Volltextindex.  
- Erstellen von Triggern für Systemtabellen in der Datenbank.  
- Löschen der Datenbank.  
- Löschen des **guest** -Benutzers aus der Datenbank.  
- Aktivieren von Change Data Capture  
- Teilnehmen an der Datenbankspiegelung.  
- Entfernen der primären Dateigruppe, der primären Datendatei oder der Protokolldatei.  
- Umbenennen der Datenbank oder der primären Dateigruppe.  
- Versetzen der Datenbank in den OFFLINE-Modus.  
- Versetzen der Datenbank oder der primären Dateigruppe in den READ_ONLY-Modus.  
  
## <a name="recommendations"></a>Empfehlungen  
Beim Arbeiten mit der **master** -Datenbank sollten Sie die folgenden Empfehlungen beachten:  
  
- Stellen Sie sicher, dass Sie jederzeit über eine aktuelle Sicherungskopie der **master** -Datenbank verfügen.  
- Erstellen Sie nach den folgenden Operationen sobald wie möglich eine Sicherungskopie der **master** -Datenbank:  
  
  - Erstellen, Ändern oder Löschen einer Datenbank  
  - Ändern der Server- oder Datenbankkonfigurationswerte  
  - Ändern oder Hinzufügen von Anmeldekonten  
  
- Erstellen Sie in der **master**-Datenbank keine Benutzerobjekte. Andernfalls muss die **master** -Datenbank häufiger gesichert werden.  
- Legen Sie die Option TRUSTWORTHY für die **master** -Datenbank nicht auf ON fest.  
  
## <a name="what-to-do-if-master-becomes-unusable"></a>Erforderliche Aktionen, wenn "master" nicht mehr verwendbar ist  
 Wenn **master** nicht mehr verwendet werden kann, gibt es mehrere Methoden, um sie in einen verwendbaren Zustand zurückzuversetzen:  
  
- Wiederherstellen der **master** -Datenbank von einer aktuellen Datenbanksicherung.  
  
  Wenn Sie die Serverinstanz starten können, sollten Sie in der Lage sein, **master** aus einer vollständigen Datenbanksicherung wiederherzustellen. Weitere Informationen finden Sie unter [Wiederherstellen der master-Datenbank &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md).  
  
- Vollständige Neuerstellung der **master** -Datenbank.  
  
  Falls ernsthafte Schäden an der **master** -Datenbank das Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verhindern, müssen Sie die **master**-Datenbank neu erstellen. Weitere Informationen finden Sie unter [Neuerstellen von Systemdatenbanken](../../relational-databases/databases/rebuild-system-databases.md).  
  
  > [!IMPORTANT]  
  >  Beim Neuerstellen der **master** -Datenbank werden alle Systemdatenbanken neu erstellt.  
  
## <a name="related-content"></a>Verwandte Inhalte  
- [Neuerstellen von Systemdatenbanken](../../relational-databases/databases/rebuild-system-databases.md)  
- [Systemdatenbanken](../../relational-databases/databases/system-databases.md)  
- [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
- [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
- [Verschieben von Datenbankdateien](../../relational-databases/databases/move-database-files.md)  
