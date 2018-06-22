---
title: Model-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/02/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- template databases [SQL Server]
- model database [SQL Server], about model databases
- model database [SQL Server]
ms.assetid: 4e4f739b-fd27-4dce-8be6-3d808040d8d7
caps.latest.revision: 47
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3f8fd67f968701440b06274bbd40600be94c00b5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059151"
---
# <a name="model-database"></a>model-Datenbank
  Die **model** -Datenbank wird als Vorlage für alle Datenbanken verwendet, die auf einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz erstellt werden. Da **tempdb** bei jedem Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt wird, muss die **model** -Datenbank zu jedem Zeitpunkt auf einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System vorhanden sein. Der gesamte Inhalt der **model** -Datenbank, einschließlich Datenbankoptionen, wird in die neue Datenbank kopiert. Einige Einstellungen der **model** -Datenbank werden auch zum Erstellen einer neuen **tempdb** -Datenbank während des Startvorgangs verwendet; deshalb muss die **model** -Datenbank immer in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System vorhanden sein.  
  
 Neu erstellte Benutzerdatenbanken verwenden dasselbe [Wiederherstellungsmodell](../backup-restore/recovery-models-sql-server.md) wie die model-Datenbank. Der Standard ist vom Benutzer konfigurierbar. Informationen zum aktuellen Wiederherstellungsmodell der model-Datenbank finden Sie unter [Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
> [!IMPORTANT]  
>  Wenn Sie die **model**-Datenbank mit benutzerspezifischen Vorlageninformationen ändern, empfiehlt es sich, dass Sie **model** sichern. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="model-usage"></a>Verwenden der model-Datenbank  
 Wenn eine CREATE DATABASE-Anweisung ausgegeben wird, wird der erste Teil der Datenbank erstellt, indem der Inhalt der **model** -Datenbank kopiert wird. Der Rest der neuen Datenbank wird dann mit leeren Seiten gefüllt.  
  
 Wenn Sie Änderungen an der **model** -Datenbank vornehmen, werden diese Änderungen an alle anschließend erstellten Datenbanken vererbt. Sie könnten z. B. Berechtigungen oder Datenbankoptionen festlegen oder Objekte wie Tabellen, Funktionen oder gespeicherte Prozeduren hinzufügen. Die Dateieigenschaften der **model** -Datenbank stellen eine Ausnahme dar und werden bis auf die Anfangsgröße der Datendatei ignoriert.  
  
## <a name="physical-properties-of-model"></a>Physische Eigenschaften der model-Datenbank  
 Die folgende Tabelle zeigt die Anfangskonfigurationswerte der **model** -Daten und -Protokolldateien. Die Größen dieser Dateien können für verschiedene Editionen von geringfügig [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|File|Logischer Name (logical name)|Physischer Name (physical name)|Dateivergrößerung (file growth)|  
|----------|------------------|-------------------|-----------------|  
|Primäre Daten|modeldev|model.mdf|Automatische Vergrößerung um 10 Prozent, bis der Speicherplatz auf dem Datenträger erschöpft ist.|  
|Log|modellog|modellog.ldf|Automatische Vergrößerung um 10 %, bis der Maximalwert von 2 TB erreicht wird.|  
  
 Informationen zum Verschieben der **model** -Datenbank oder -Protokolldateien finden Sie unter [Verschieben von Systemdatenbanken](system-databases.md).  
  
### <a name="database-options"></a>Datenbankoptionen  
 Die folgende Tabelle zeigt den Standardwert jeder Datenbankoption in der **model** -Datenbank und gibt an, ob die Option geändert werden kann. Zum Anzeigen der aktuellen Einstellungen dieser Optionen verwenden Sie die Katalogsicht [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Datenbankoption|Standardwert|Kann geändert werden.|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|ja|  
|ANSI_NULL_DEFAULT|OFF|ja|  
|ANSI_NULLS|OFF|ja|  
|ANSI_PADDING|OFF|ja|  
|ANSI_WARNINGS|OFF|ja|  
|ARITHABORT|OFF|ja|  
|AUTO_CLOSE|OFF|ja|  
|AUTO_CREATE_STATISTICS|ON|ja|  
|AUTO_SHRINK|OFF|ja|  
|AUTO_UPDATE_STATISTICS|ON|ja|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|ja|  
|CHANGE_TRACKING|OFF|nein|  
|CONCAT_NULL_YIELDS_NULL|OFF|ja|  
|CURSOR_CLOSE_ON_COMMIT|OFF|ja|  
|CURSOR_DEFAULT|GLOBAL|ja|  
|Datenbankverfügbarkeitsoptionen|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|nein<br /><br /> ja<br /><br /> ja|  
|DATE_CORRELATION_OPTIMIZATION|OFF|ja|  
|DB_CHAINING|OFF|nein|  
|ENCRYPTION|OFF|nein|  
|NUMERIC_ROUNDABORT|OFF|ja|  
|PAGE_VERIFY|CHECKSUM|ja|  
|PARAMETERIZATION|SIMPLE|ja|  
|QUOTED_IDENTIFIER|OFF|ja|  
|READ_COMMITTED_SNAPSHOT|OFF|ja|  
|RECOVERY|Richtet sich nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Edition<sup>1</sup>|ja|  
|RECURSIVE_TRIGGERS|OFF|ja|  
|Service Broker-Optionen|DISABLE_BROKER|nein|  
|TRUSTWORTHY|OFF|nein|  
  
 <sup>1</sup> zum Überprüfen des aktuellen Wiederherstellungsmodells der Datenbank finden Sie unter [anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41; ](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) oder [sys.databases &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).  
  
 Eine Beschreibung dieser Datenbankoptionen finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="restrictions"></a>Restrictions  
 Die folgenden Operationen können an der **model** -Datenbank nicht ausgeführt werden:  
  
-   Hinzufügen von Dateien oder Dateigruppen.  
  
-   Ändern der Sortierung. Die Standardsortierung entspricht der Serversortierung.  
  
-   Ändern des Datenbankbesitzers Der Besitzer von**model** ist **sa**.  
  
-   Löschen der Datenbank.  
  
-   Löschen des **guest** -Benutzers aus der Datenbank.  
  
-   Aktivieren von Change Data Capture  
  
-   Teilnehmen an der Datenbankspiegelung.  
  
-   Entfernen der primären Dateigruppe, der primären Datendatei oder der Protokolldatei.  
  
-   Umbenennen der Datenbank oder der primären Dateigruppe.  
  
-   Versetzen der Datenbank in den OFFLINE-Modus.  
  
-   Versetzen der primären Dateigruppe in den READ_ONLY-Modus.  
  
-   Erstellen von Prozeduren, Sichten oder Triggern mit der Option WITH ENCRYPTION. Der Verschlüsselungsschlüssel ist an die Datenbank gebunden, in der das Objekt erstellt wird. In der **model** -Datenbank erstellte verschlüsselte Objekte können nur in **model**verwendet werden.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Systemdatenbanken](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Verschieben von Datenbankdateien](move-database-files.md)  
  
  
