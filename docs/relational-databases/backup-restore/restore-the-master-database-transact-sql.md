---
title: Wiederherstellen der Hauptdatenbank (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], restoring
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6ce115a0df8ca77b37a78234247174ca9f2dd006
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68041471"
---
# <a name="restore-the-master-database-transact-sql"></a>Wiederherstellen der master-Datenbank (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  In diesem Thema erfahren Sie, wie Sie die **master** -Datenbank von einer vollständigen Datenbanksicherung wiederherstellen.  
  
### <a name="to-restore-the-master-database"></a>So stellen Sie die master-Datenbank wieder her  
  
1.  Starten Sie die Serverinstanz im Einzelbenutzermodus.  
  
     Informationen zum Angeben des Startparameters für Einzelbenutzer ( **-m**) finden Sie unter [Konfigurieren von Serverstartoptionen &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).  
  
2.  Verwenden Sie zum Wiederherstellen einer vollständigen Sicherung der **master**-Datenbank die folgende [RESTORE DATABASE](../../t-sql/statements/restore-statements-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung:  
  
     `RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`  
  
     Die REPLACE-Option weist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an, die angegebene Datenbank wiederherzustellen, selbst wenn eine Datenbank mit dem gleichen Namen bereits vorhanden ist. Die vorhandene Datenbank wird ggf. gelöscht. Für den Einzelbenutzermodus empfiehlt sich die Eingabe der RESTORE DATABASE-Anweisung im [Hilfsprogramm sqlcmd](../../tools/sqlcmd-utility.md). Weitere Informationen finden Sie unter [Verwenden des Hilfsprogramms sqlcmd](../../relational-databases/scripting/sqlcmd-use-the-utility.md).  
  
    > [!IMPORTANT]  
    >  Nach der Wiederherstellung von **master** wird die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] heruntergefahren, und der **sqlcmd** -Prozess wird beendet. Vor dem Neustarten der Serverinstanz muss der Einzelbenutzer-Startparameter entfernt werden. Weitere Informationen finden Sie unter [Konfigurieren von Serverstartoptionen &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).  
  
3.  Starten Sie die Serverinstanz neu, und setzen Sie andere Wiederherstellungsschritte, z. B. das Wiederherstellen von anderen Datenbanken, das Anfügen von Datenbanken und das Korrigieren von Benutzerkonflikten, fort.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `master` -Datenbank auf der Standardserverinstanz wiederhergestellt. In diesem Beispiel wird vorausgesetzt, dass die Serverinstanz bereits im Einzelbenutzermodus ausgeführt wird. Im Beispiel wird `sqlcmd` gestartet, und es wird eine `RESTORE DATABASE` -Anweisung ausgeführt, mit der eine vollständige Datenbanksicherung der `master` -Datenbank vom Datenträgermedium wiederhergestellt wird: `Z:\SQLServerBackups\master.bak`.  
  
> [!NOTE]  
>  Bei einer benannten Instanz muss mit dem **sqlcmd**-Befehl die Option **-S** _\<Computername>_ \\ *\<Instanzname>* angegeben werden.  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [Vollständige Datenbankwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Problembehandlung bei verwaisten Benutzern &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [Neuerstellen von Systemdatenbanken](../../relational-databases/databases/rebuild-system-databases.md)   
 [Startoptionen für den Datenbank-Engine-Dienst](../../database-engine/configure-windows/database-engine-service-startup-options.md)   
 [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md)   
 [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Starten von SQL Server im Einzelbenutzermodus](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
