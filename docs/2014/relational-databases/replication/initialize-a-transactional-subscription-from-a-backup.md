---
title: Initialisieren eines Transaktionsabonnements von einer Sicherung (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7e7fb32de254729c4173fab260e5797db5f2cc2f
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793306"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a>Initialisieren eines Transaktionsabonnements von einer Sicherung (Replikationsprogrammierung mit Transact-SQL)
  Obwohl ein Abonnement für eine Transaktionsveröffentlichung in der Regel mit einer Momentaufnahme initialisiert wird, kann ein Abonnement auch mit gespeicherten Replikationsprozeduren von einer Sicherung initialisiert werden. Weitere Informationen finden Sie unter [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)initialisiert wird.  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a>So initialisieren Sie einen Transaktionsabonnenten von einer Sicherung  
  
1.  Stellen Sie bei einer bestehenden Veröffentlichung sicher, dass die Veröffentlichung die Fähigkeit unterstützt, von einer Sicherung initialisieren zu können. Führen Sie dazu [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Notieren Sie den Wert von **allow_initialize_from_backup** im Resultset.  
  
    -   Wenn der Wert **1**ist, unterstützt die Veröffentlichung diese Funktionalität.  
  
    -   Ist der Wert **0**, führen Sie [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **Allow_initialize_from_backup** für  **\@Eigenschaft** und den Wert `true` für  **\@Wert**.  
  
2.  Führen Sie für eine neue Veröffentlichung [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert `true` für **Allow_initialize_from_backup**. Weitere Informationen finden Sie unter [Create a Publication](publish/create-a-publication.md).  
  
    > [!WARNING]  
    >  Um fehlende Abonnentendaten zu vermeiden, wenn Sie **sp_addpublication** mit `@allow_initialize_from_backup = N'true'`verwenden, sollten Sie immer `@immediate_sync = N'true'`verwenden.  
  
3.  Erstellen Sie mit der [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)-Anweisung eine Sicherung der Veröffentlichungsdatenbank.  
  
4.  Stellen Sie die Sicherung auf dem Abonnenten mit der [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)-Anweisung wieder her.  
  
5.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank die gespeicherte Prozedur [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) aus. Geben Sie die folgenden Parameter an:  
  
    -   **\@Sync_type** -Wert **initialisieren mit der Sicherung**.  
  
    -   **\@Backupdevicetype** – der Typ des Sicherungsmediums: **logische** (Standard), **Datenträger**, oder **Band**.  
  
    -   **\@Backupdevicename** -das logische oder physische Sicherungsmedium, für die Wiederherstellung verwendet.  
  
         Für ein logisches Gerät geben Sie den Namen des Sicherungsmediums an, der beim Erstellen des Geräts mit **sp_addumpdevice** festgelegt wurde.  
  
         Geben Sie für ein physisches Gerät einen vollständigen Pfad und einen Dateinamen an, z. B. `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` oder `TAPE = '\\.\TAPE0'`.  
  
    -   (Optional)  **\@Kennwort** -ein Kennwort, das bereitgestellt wurde, als der Sicherungssatz erstellt wurde.  
  
    -   (Optional)  **\@Mediapassword** -ein Kennwort, das bereitgestellt wurde, als der Mediensatz formatiert wurde.  
  
    -   (Optional)  **\@Fileidhint** -Bezeichner für den Sicherungssatz wiederhergestellt werden. **1** gibt z. B. den ersten Sicherungssatz auf dem Sicherungsmedium an und **2** den zweiten Sicherungssatz.  
  
    -   (Optional für Bandmedien)  **\@nicht entladen** -Geben Sie den Wert **1** (Standard), wenn das Band aus dem Laufwerk werden soll, nachdem die Wiederherstellung abgeschlossen ist und **0** Wenn es nicht entladen werden soll .  
  
6.  (Optional) Führen Sie für ein Pullabonnement [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) und [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) im Abonnenten für die Abonnementdatenbank aus. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md).  
  
7.  (Optional) Starten Sie den Verteilungs-Agent. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) oder [Synchronize a Push Subscription](synchronize-a-push-subscription.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../databases/copy-databases-with-backup-and-restore.md)   
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
