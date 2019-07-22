---
title: Ausführen des manuellen Failovers einer Datenbank-Spiegelungssitzung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
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
ms.openlocfilehash: ddfaec9f9192af98f8b3580554f8c89d757af566
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041743"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a>Ausführen des manuellen Failovers einer Datenbank-Spiegelungssitzung (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn die gespiegelte Datenbank synchronisiert wird, also den Status SYNCHRONIZED aufweist, kann der Datenbankbesitzer ein manuelles Failover zu dem gespiegelten Server initiieren. Das manuelle Failover kann nur vom Prinzipalserver aus initiiert werden.  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a>So führen Sie das manuelle Failover einer Datenbank-Spiegelungssitzung durch  
  
1.  Stellen Sie eine Verbindung mit dem Prinzipalserver her.  
  
2.  Ändern Sie den Datenbankkontext auf die **master** -Datenbank um:  
  
     **USE master;**  
  
3.  Führen Sie auf dem Prinzipalserver die folgende Anweisung aus:  
  
     [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md) *Name der Datenbank* SET PARTNER FAILOVER, wobei *Name der Datenbank* die gespiegelte Datenbank darstellt.  
  
     Hierdurch wird die sofortige Übertragung des Spiegelservers in die Prinzipalrolle initiiert.  
  
 Auf dem ehemaligen Prinzipal wird die Verbindung der Clients mit der Datenbank getrennt, und das Rollback der umgehend ausgeführten Transaktionen wird vorgenommen.  
  
> [!NOTE]  
>  Transaktionen, die mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator vorbereitet wurden, für die beim Auftreten eines Failovers jedoch noch kein Commit ausgeführt wurde, werden nach dem Failover der Datenbank als abgebrochen betrachtet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE-Datenbankspiegelung &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [Manuelles Failover für eine Datenbank-Spiegelungssitzung (SQL Server Management Studio)](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
