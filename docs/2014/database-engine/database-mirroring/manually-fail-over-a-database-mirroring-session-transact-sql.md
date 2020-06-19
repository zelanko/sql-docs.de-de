---
title: Ausführen des manuellen Failovers einer Datenbank-Spiegelungssitzung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c04ea4908ccbc4cfe4f6bb3606347dd444ef416
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934141"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a>Ausführen des manuellen Failovers einer Datenbank-Spiegelungssitzung (Transact-SQL)
  Wenn die gespiegelte Datenbank synchronisiert wird, also den Status SYNCHRONIZED aufweist, kann der Datenbankbesitzer ein manuelles Failover zu dem gespiegelten Server initiieren. Das manuelle Failover kann nur vom Prinzipalserver aus initiiert werden.  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a>So führen Sie das manuelle Failover einer Datenbank-Spiegelungssitzung durch  
  
1.  Stellen Sie eine Verbindung mit dem Prinzipalserver her.  
  
2.  Ändern Sie den Datenbankkontext auf die **master** -Datenbank um:  
  
     `USE master;`  
  
3.  Führen Sie auf dem Prinzipalserver die folgende Anweisung aus:  
  
     [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET PARTNER FAILOVER, wobei *database_name* die gespiegelte Datenbank darstellt.  
  
     Hierdurch wird die sofortige Übertragung des Spiegelservers in die Prinzipalrolle initiiert.  
  
 Auf dem ehemaligen Prinzipal wird die Verbindung der Clients mit der Datenbank getrennt, und das Rollback der umgehend ausgeführten Transaktionen wird vorgenommen.  
  
> [!NOTE]  
>  Transaktionen, die mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator vorbereitet wurden, für die beim Auftreten eines Failovers jedoch noch kein Commit ausgeführt wurde, werden nach dem Failover der Datenbank als abgebrochen betrachtet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Alter Database-Daten Bank Spiegelung &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Manuelles Failover für eine Datenbank-Spiegelungs Sitzung &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
