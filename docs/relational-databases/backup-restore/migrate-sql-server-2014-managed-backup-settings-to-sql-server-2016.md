---
title: Migrieren von verwalteten Sicherungseinstellungen
description: In diesem Thema werden Migrationsüberlegungen für SQL Server Managed Backup to Microsoft Azure erläutert, wenn ein Upgrade von SQL Server 2014 auf SQL Server 2016 ausgeführt wird.
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: ae937ebb-24ff-4a33-be3c-8f85328dfc75
author: cawrites
ms.author: chadam
ms.openlocfilehash: 03a496f72b42b8367d546712e1e7d3c7f7c35fe9
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "96130365"
---
# <a name="migrate-managed-backup-settings"></a>Migrieren von verwalteten Sicherungseinstellungen
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema werden Migrationsaspekte [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] bei der Aktualisierung von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] auf [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]erläutert.  
  
 Die Verfahren und das zugrunde liegende Verhalten von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] wurden in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]geändert. In den folgenden Abschnitten werden die funktionale Änderungen und deren Bedeutung beschrieben.  
  
## <a name="overview"></a>Übersicht  
 Die folgende Tabelle beschreibt einige der wichtigsten funktionalen Unterschiede für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] zwischen [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
|Bereich|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|----------|---------------------------|---------------------------|  
|**Namespace:**|smart_admin|managed_backup|  
|**Gespeicherte Systemprozeduren:**|sp_set_db_backup<br /><br /> sp_set_instance_backup|[managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)<br /><br /> [sp_backup_config_advanced](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)<br /><br /> [sp_backup_config_schedule](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)|  
|**Sicherheit**:|SQL-Anmeldeinformationen mit einem Microsoft Azure-Speicherkonto und Ihrem Zugriffsschlüssel.|SQL-Anmeldeinformationen mit einem Microsoft Azure Shared Access Signature (SAS)-Token.|  
|**Zugrunde liegende Speicher:**|Microsoft Azure-Speicher mithilfe des Seiten-Blobs.|Microsoft Azure-Speicher mithilfe des Block-Blobs.|  
  
## <a name="benefits"></a>Vorteile  
 Die neuen Funktionen in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]bieten zahlreiche Vorteile.  
  
-   Die Speicherkosten für Block-Blobs sind geringer.  
  
-   Mit Striping können Sie erheblich größere Sicherungskopien (12 TB im Vergleich zu 1 TB bei Seiten-Blobs) speichern.  
  
-   Striping verbessert auch die Wiederherstellungszeit für große Datenbanken  
  
-   Informationen zu weiteren Verbesserungen an [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)][!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]finden Sie unter [SQL Server Managed Backup to Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="considerations"></a>Überlegungen  
 Nach dem Upgrade von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]sind die folgenden Aspekte bezüglich [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] zu beachten:  
  
-   Alle zuvor für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] konfigurierten Datenbanken verwenden weiterhin die **smart_admin-** Systemprozeduren und das zugrunde liegende Verhalten in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
-   Die **smart_admin** -Prozeduren werden für neue Konfigurationen von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]nicht unterstützt. Sie müssen die neuen **managed_backup** -Prozeduren und -Funktionen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltete SQL Server-Sicherung in Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
