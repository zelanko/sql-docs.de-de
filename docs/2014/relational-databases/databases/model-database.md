---
title: Model-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/02/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- template databases [SQL Server]
- model database [SQL Server], about model databases
- model database [SQL Server]
ms.assetid: 4e4f739b-fd27-4dce-8be6-3d808040d8d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c2886fffebdf06ea16ebe8b6992387be3c22e0bf
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812182"
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
 Die folgende Tabelle zeigt die Anfangskonfigurationswerte der **model** -Daten und -Protokolldateien. Die Größen dieser Dateien können in den unterschiedlichen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geringfügig variieren.  
  
|Datei|Logischer Name (logical name)|Physischer Name (physical name)|Dateivergrößerung (file growth)|  
|----------|------------------|-------------------|-----------------|  
|Primäre Daten|modeldev|model.mdf|Automatische Vergrößerung um 10 Prozent, bis der Speicherplatz auf dem Datenträger erschöpft ist.|  
|Log|modellog|modellog.ldf|Automatische Vergrößerung um 10 %, bis der Maximalwert von 2 TB erreicht wird.|  
  
 Informationen zum Verschieben der **model** -Datenbank oder -Protokolldateien finden Sie unter [Verschieben von Systemdatenbanken](system-databases.md).  
  
### <a name="database-options"></a>Datenbankoptionen  
 Die folgende Tabelle zeigt den Standardwert jeder Datenbankoption in der **model** -Datenbank und gibt an, ob die Option geändert werden kann. Zum Anzeigen der aktuellen Einstellungen dieser Optionen verwenden Sie die Katalogsicht [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Datenbankoption|Standardwert|Kann geändert werden.|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Ja|  
|ANSI_NULL_DEFAULT|OFF|Ja|  
|ANSI_NULLS|OFF|Ja|  
|ANSI_PADDING|OFF|Ja|  
|ANSI_WARNINGS|OFF|Ja|  
|ARITHABORT|OFF|Ja|  
|AUTO_CLOSE|OFF|Ja|  
|AUTO_CREATE_STATISTICS|ON|Ja|  
|AUTO_SHRINK|OFF|Ja|  
|AUTO_UPDATE_STATISTICS|ON|Ja|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Ja|  
|CHANGE_TRACKING|OFF|Nein|  
|CONCAT_NULL_YIELDS_NULL|OFF|Ja|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Ja|  
|CURSOR_DEFAULT|GLOBAL|Ja|  
|Datenbankverfügbarkeitsoptionen|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Nein<br /><br /> Ja<br /><br /> Ja|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Ja|  
|DB_CHAINING|OFF|Nein|  
|ENCRYPTION|OFF|Nein|  
|NUMERIC_ROUNDABORT|OFF|Ja|  
|PAGE_VERIFY|CHECKSUM|Ja|  
|PARAMETERIZATION|SIMPLE|Ja|  
|QUOTED_IDENTIFIER|OFF|Ja|  
|READ_COMMITTED_SNAPSHOT|OFF|Ja|  
|RECOVERY|Hängt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Edition<sup>1</sup>|Ja|  
|RECURSIVE_TRIGGERS|OFF|Ja|  
|Service Broker-Optionen|DISABLE_BROKER|Nein|  
|TRUSTWORTHY|OFF|Nein|  
  
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
  
  
