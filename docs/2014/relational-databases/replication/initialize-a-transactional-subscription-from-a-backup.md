---
title: Initialisieren eines Transaktions Abonnements von einer Sicherung (Replikations Programmierung mit Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 1563d58f2d54f77680781e22a162112ade1658e4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057105"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a>Initialisieren eines Transaktionsabonnements von einer Sicherung (Replikationsprogrammierung mit Transact-SQL)
  Obwohl ein Abonnement für eine Transaktionsveröffentlichung in der Regel mit einer Momentaufnahme initialisiert wird, kann ein Abonnement auch mit gespeicherten Replikationsprozeduren von einer Sicherung initialisiert werden. Weitere Informationen finden Sie unter [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)initialisiert wird.  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a>So initialisieren Sie einen Transaktionsabonnenten von einer Sicherung  
  
1.  Stellen Sie bei einer bestehenden Veröffentlichung sicher, dass die Veröffentlichung die Fähigkeit unterstützt, von einer Sicherung initialisieren zu können. Führen Sie dazu [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Notieren Sie den Wert von **allow_initialize_from_backup** im Resultset.  
  
    -   Wenn der Wert **1**ist, unterstützt die Veröffentlichung diese Funktionalität.  
  
    -   Ist der Wert **0**, führen Sie [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **allow_initialize_from_backup** für die- ** \@ Eigenschaft** und den Wert `true` für ** \@ value**an.  
  
2.  Führen Sie für eine neue Veröffentlichung [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert `true` für **allow_initialize_from_backup**an. Weitere Informationen finden Sie unter [Erstellen einer Veröffentlichung](publish/create-a-publication.md).  
  
    > [!WARNING]  
    >  Um fehlende Abonnentendaten zu vermeiden, wenn Sie **sp_addpublication** mit `@allow_initialize_from_backup = N'true'`verwenden, sollten Sie immer `@immediate_sync = N'true'`verwenden.  
  
3.  Erstellen Sie mit der [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)-Anweisung eine Sicherung der Veröffentlichungsdatenbank.  
  
4.  Stellen Sie die Sicherung auf dem Abonnenten mit der [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)-Anweisung wieder her.  
  
5.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank die gespeicherte Prozedur [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) aus. Geben Sie die folgenden Parameter an:  
  
    -   ** \@ sync_type** -der Wert **initialisieren with Backup**.  
  
    -   ** \@ backupdevicetype** : der Typ des Sicherungs Mediums: **logisch** (Standard **), Daten**Träger oder **Band**.  
  
    -   ** \@ backupdevicename** : das logische oder physische Sicherungsmedium, das für die Wiederherstellung verwendet werden soll.  
  
         Für ein logisches Gerät geben Sie den Namen des Sicherungsmediums an, der beim Erstellen des Geräts mit **sp_addumpdevice** festgelegt wurde.  
  
         Geben Sie für ein physisches Gerät einen vollständigen Pfad und einen Dateinamen an, z. B. `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` oder `TAPE = '\\.\TAPE0'`.  
  
    -   Optionale ** \@ Password** : ein Kennwort, das angegeben wurde, als der Sicherungs Satz erstellt wurde.  
  
    -   Optionale ** \@ Media Password** : ein Kennwort, das angegeben wurde, als der Medien Satz formatiert wurde.  
  
    -   Optionale " ** \@ fleidhint** ": Bezeichner für den Sicherungs Satz, der wieder hergestellt werden soll. **1** gibt z. B. den ersten Sicherungssatz auf dem Sicherungsmedium an und **2** den zweiten Sicherungssatz.  
  
    -   (Optional für Bandgeräte) ** \@ entladen** : Geben Sie den Wert **1** (Standardwert) an, wenn das Band nach Abschluss der Wiederherstellung vom Laufwerk entladen werden soll, und **0** , wenn es nicht entladen werden soll.  
  
6.  (Optional) Führen Sie für ein Pullabonnement [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) und [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) im Abonnenten für die Abonnementdatenbank aus. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md).  
  
7.  (Optional) Starten Sie den Verteilungs-Agent. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) oder [Synchronize a Push Subscription](synchronize-a-push-subscription.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../databases/copy-databases-with-backup-and-restore.md)   
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
