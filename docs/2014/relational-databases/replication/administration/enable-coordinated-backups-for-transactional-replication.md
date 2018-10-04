---
title: Aktivieren koordinierter Sicherungen für die Transaktionsreplikation (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 27c4a2daa8574d9ad012f079309e5a1658db5568
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101830"
---
# <a name="enable-coordinated-backups-for-transactional-replication-replication-transact-sql-programming"></a>Aktivieren koordinierter Sicherungen für die Transaktionsreplikation (Replikationsprogrammierung mit Transact-SQL)
  Wenn Sie eine Datenbank für die Transaktionsreplikation aktivieren, können Sie angeben, dass alle Transaktionen gesichert werden müssen, bevor sie an die Verteilungsdatenbank übermittelt werden. Zudem können Sie auf der Verteilungsdatenbank die koordinierte Sicherung aktivieren, sodass das Transaktionsprotokoll der Veröffentlichungsdatenbank erst dann abgeschnitten wird, nachdem die an den Verteiler weitergegebenen Transaktionen gesichert wurden. Weitere Informationen finden Sie unter [Strategien zum Sichern und Wiederherstellen einer Momentaufnahme- und Transaktionsreplikation](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a>So aktivieren Sie koordinierte Sicherungen für eine mit der Transaktionsreplikation veröffentlichte Datenbank  
  
1.  Verwenden Sie auf dem Verleger die [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql)-Funktion, um die **IsSyncWithBackup**-Eigenschaft der Veröffentlichungsdatenbank zurückzugeben. Wenn die Funktion **1**zurückgibt, sind bereits koordinierte Sicherungen für die veröffentlichte Datenbank aktiviert.  
  
2.  Wenn die Funktion in Schritt 1 **0** zurückgibt, führen Sie [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie einen Wert **sync with backup** für **@optname**und **true** für **@value**.  
  
    > [!NOTE]  
    >  Wenn Sie die Option **sync with backup** in **false**ändern, wird der Abschneidepunkt der Veröffentlichungsdatenbank nach Ausführen des Protokolllese-Agents aktualisiert oder, wenn der Protokolllese-Agent fortlaufend ausgeführt wird, nach einem bestimmten Zeitintervall. Das Maximalintervall wird vom **–MessageInterval** -Agentparameter gesteuert (standardmäßig 30 Sekunden).  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a>So aktivieren Sie koordinierte Sicherungen für eine Verteilungsdatenbank  
  
1.  Verwenden Sie auf dem Verteiler die [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql)-Funktion, um die **IsSyncWithBackup**-Eigenschaft der Verteilungsdatenbank zurückzugeben. Wenn die Funktion **1**zurückgibt, sind bereits koordinierte Sicherungen für die Verteilungsdatenbank aktiviert.  
  
2.  Wenn die Funktion in Schritt 1 **0** zurückgibt, führen Sie [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) auf dem Verteiler für die Verteilungsdatenbank aus. Geben Sie einen Wert **sync with backup** für **@optname** und **true** für **@value**.  
  
### <a name="to-disable-coordinated-backups"></a>So deaktivieren Sie koordinierte Sicherungen  
  
1.  Führen Sie [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Verteiler für die Verteilungsdatenbank aus. Geben Sie einen Wert **sync with backup** für **@optname** und **false** für **@value**.  
  
  
