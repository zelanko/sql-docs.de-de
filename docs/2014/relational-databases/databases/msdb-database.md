---
title: msdb-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/10/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, msdb database
- alerts [SQL Server], msdb database
- jobs [SQL Server], msdb database
- msdb database [SQL Server]
ms.assetid: 5032cb2d-65a0-40dd-b569-4dcecdd58ceb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cee4c5d802447488930ffd04d698edcd2015e86b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62871709"
---
# <a name="msdb-database"></a>msdb-Datenbank
  Die **msdb** -Datenbank wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum Planen von Warnungen und Aufträgen sowie von anderen Features [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]wie [!INCLUDE[ssSB](../../includes/sssb-md.md)] und Datenbank-E-Mail verwendet.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird beispielsweise in der **msdb**-Datenbank automatisch ein vollständiger Onlinesicherungs- und Wiederherstellungsverlauf in Tabellen verwaltet. Diese Informationen umfassen den Namen der Person, die die Sicherung ausgeführt hat, den Zeitpunkt der Sicherung und die Angabe, auf welchen Medien bzw. in welchen Dateien die Sicherung gespeichert wurde. 
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwendet diese Informationen, um einen Plan für das Wiederherstellen einer Datenbank und das Anwenden vorhandener Transaktionsprotokollsicherungen vorzuschlagen. Sicherungsvorgänge für alle Datenbanken werden auch dann aufgezeichnet, wenn sie mit benutzerdefinierten Anwendungen oder Tools von Drittanbietern erstellt wurden. Wenn Sie beispielsweise eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Anwendung verwenden, die zum Ausführen von Sicherungsvorgängen SMO-Objekte (SQL Server Management Objects) aufruft, wird das Ereignis in den **msdb** -Systemtabellen, im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll sowie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll protokolliert. Um die in der **msdb**-Datenbank gespeicherten Informationen zu schützen, empfiehlt es sich, das **msdb** -Transaktionsprotokoll auf einem fehlertoleranten Datenträger zu speichern.  
  
 Standardmäßig verwendet **msdb** das einfache Wiederherstellungsmodell. Wenn Sie die Tabellen mit dem [Sicherungs- und Wiederherstellungsverlauf](../backup-restore/backup-history-and-header-information-sql-server.md) verwenden, empfiehlt es sich, das vollständige Wiederherstellungsmodell für **msdb**zu verwenden. Weitere Informationen finden Sie unter [Wiederherstellungsmodelle &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md). Beachten Sie Folgendes: Ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert oder aktualisiert oder wird **Setup.exe** zum Neuerstellen der Systemdatenbanken verwendet, wird das Wiederherstellungsmodell von msdb automatisch auf simple festgelegt.  
  
> [!IMPORTANT]  
>  Nach einem Vorgang, durch den **msdb**aktualisiert wird (beispielsweise nach dem Sichern oder Wiederherstellen von Datenbanken), empfiehlt es sich, eine Sicherung von **msdb**auszuführen. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="physical-properties-of-msdb"></a>Physische Eigenschaften der msdb-Datenbank  
 Die folgende Tabelle zeigt die Anfangskonfigurationswerte der **msdb** -Daten und -Protokolldateien. Die Größe dieser Dateien kann sich in den verschiedenen Editionen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]geringfügig unterscheiden.  
  
|Datei|Logischer Name (logical name)|Physischer Name (physical name)|Dateivergrößerung (file growth)|  
|----------|------------------|-------------------|-----------------|  
|Primäre Daten|MSDBData|MSDBData.mdf|Automatische Vergrößerung um 10 Prozent, bis der Speicherplatz auf dem Datenträger erschöpft ist.|  
|Log|MSDBLog|MSDBLog.ldf|Automatische Vergrößerung um 10 %, bis der Maximalwert von 2 TB erreicht wird.|  
  
 Informationen zum Verschieben der **msdb** -Datenbank oder -Protokolldateien finden Sie unter [Verschieben von Systemdatenbanken](move-system-databases.md).  
  
### <a name="database-options"></a>Datenbankoptionen  
 Die folgende Tabelle zeigt den Standardwert jeder Datenbankoption in der **msdb** -Datenbank und gibt an, ob die Option geändert werden kann. Zum Anzeigen der aktuellen Einstellungen dieser Optionen verwenden Sie die Katalogsicht [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Datenbankoption|Standardwert|Kann geändert werden.|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|EIN|Nein|  
|ANSI_NULL_DEFAULT|OFF|Ja|  
|ANSI_NULLS|OFF|Ja|  
|ANSI_PADDING|OFF|Ja|  
|ANSI_WARNINGS|OFF|Ja|  
|ARITHABORT|OFF|Ja|  
|AUTO_CLOSE|OFF|Ja|  
|AUTO_CREATE_STATISTICS|EIN|Ja|  
|AUTO_SHRINK|OFF|Ja|  
|AUTO_UPDATE_STATISTICS|EIN|Ja|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Ja|  
|CHANGE_TRACKING|OFF|Nein|  
|CONCAT_NULL_YIELDS_NULL|OFF|Ja|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Ja|  
|CURSOR_DEFAULT|GLOBAL|Ja|  
|Datenbankverfügbarkeitsoptionen|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Nein<br /><br /> Ja<br /><br /> Ja|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Ja|  
|DB_CHAINING|EIN|Ja|  
|ENCRYPTION|OFF|Nein|  
|NUMERIC_ROUNDABORT|OFF|Ja|  
|PAGE_VERIFY|CHECKSUM|Ja|  
|PARAMETERIZATION|SIMPLE|Ja|  
|QUOTED_IDENTIFIER|OFF|Ja|  
|READ_COMMITTED_SNAPSHOT|OFF|Nein|  
|RECOVERY|SIMPLE|Ja|  
|RECURSIVE_TRIGGERS|OFF|Ja|  
|Service Broker-Optionen|ENABLE_BROKER|Ja|  
|TRUSTWORTHY|EIN|Ja|  
  
 Eine Beschreibung dieser Datenbankoptionen finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="restrictions"></a>Beschränkungen  
 Die folgenden Operationen können an der **msdb** -Datenbank nicht ausgeführt werden:  
  
-   Ändern der Sortierung. Die Standardsortierung entspricht der Serversortierung.  
  
-   Löschen der Datenbank.  
  
-   Der **Gast** Benutzer wird aus der Datenbank gelöscht.  
  
-   Aktivieren von Change Data Capture  
  
-   Teilnehmen an der Datenbankspiegelung.  
  
-   Entfernen der primären Dateigruppe, der primären Datendatei oder der Protokolldatei.  
  
-   Umbenennen der Datenbank oder der primären Dateigruppe.  
  
-   Versetzen der Datenbank in den OFFLINE-Modus.  
  
-   Versetzen der primären Dateigruppe in den READ_ONLY-Modus.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Systemdatenbanken](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Verschieben von Datenbankdateien](move-database-files.md)  
  
 [Datenbank-E-Mail](../database-mail/database-mail.md)  
  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
