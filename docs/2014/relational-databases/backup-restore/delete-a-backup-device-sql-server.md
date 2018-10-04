---
title: Löschen eines Sicherungsmediums (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], deleting devices
- backup devices [SQL Server], deleting
- deleting backup devices
- removing backup devices
- backing up databases [SQL Server], backup devices
ms.assetid: 7be62480-ed6a-4262-a071-1feba73b1c02
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: de81f6e7f5f375e2b71414385e4c27e2ceb8082f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187560"
---
# <a name="delete-a-backup-device-sql-server"></a>Löschen eines Sicherungsmediums (SQL Server)
  In diesem Thema wird beschrieben, wie Sie ein Sicherungsmedium in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So löschen Sie ein Sicherungsmedium mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **diskadmin** .  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-backup-device"></a>So löschen Sie ein Sicherungsmedium  
  
1.  Klicken Sie im Objekt-Explorer nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Serverobjekte**und anschließend **Sicherungsmedien**.  
  
3.  Klicken Sie mit der rechten Maustaste auf das gewünschte Medium, und klicken Sie dann auf **Löschen**.  
  
4.  Überprüfen Sie im Dialogfeld **Objekt löschen** , ob in der Spalte **Objektname** der richtige Medienname angezeigt wird.  
  
5.  Klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-backup-device"></a>So löschen Sie ein Sicherungsmedium  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, und fügen Sie es in das Abfragefenster ein. In diesem Beispiel wird gezeigt, wie [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) verwendet werden muss, um ein Sicherungsmedium zu löschen. Führen Sie das erste Beispiel aus, um das `mybackupdisk` -Sicherungsmedium und den physischen Namen `c:\backup\backup1.bak`zu erstellen. Führen Sie `sp_dropdevice` So löschen Sie die `mybackupdisk` Sicherungsmedium. Der physische Namen wird vom `delfile` -Parameter gelöscht.  
  
```tsql  
--Define a backup device and physical name.   
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mybackupdisk', 'c:\backup\backup1.bak' ;  
GO  
--Delete the backup device and the physical name.  
USE AdventureWorks2012 ;  
GO  
EXEC sp_dropdevice ' mybackupdisk ', 'delfile' ;  
GO  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)   
 [sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
  
