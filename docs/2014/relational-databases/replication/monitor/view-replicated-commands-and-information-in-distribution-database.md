---
title: Anzeigen replizierter Befehle und anderer Informationen in der Verteilungs Datenbank (Replikations Programmierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 86ced6fd281da2e47ddaa31cab7fa977767b98d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74164953"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a>Anzeigen replizierter Befehle und anderer Informationen in der Verteilungsdatenbank (Replikationsprogrammierung mit Transact-SQL)
  Bei Verwendung der Transaktionsreplikation werden Transaktionsbefehle in der Verteilungsdatenbank gespeichert, bis sie vom Verteilungs-Agent an alle Abonnenten weitergegeben oder bis die Änderungen von einem Verteilungs-Agent abgerufen werden. Diese ausstehenden Befehle in der Verteilungsdatenbank können programmgesteuert mit gespeicherten Replikationsprozeduren angezeigt werden. Weitere Informationen finden Sie unter [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql).  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>So zeigen Sie replizierte Befehle für alle Transaktionsveröffentlichungen in der Verteilungsdatenbank an  
  
1.  Führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)aus.  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>So zeigen Sie replizierte Befehle in der Verteilungsdatenbank für einen bestimmten Artikel oder für eine bestimmte Datenbank an, der bzw. die mithilfe der Transaktionsreplikation veröffentlicht wurde  
  
1.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)aus. ** \@Veröffentlichung** und ** \@Artikel**angeben. Beachten Sie den Wert von **article id** im Resultset.  
  
2.  Führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)aus. Optionale Geben Sie die Artikel-ID aus Schritt 2 für ** \@article_id**an. Optionale Geben Sie die ID der Veröffentlichungs Datenbank für ** \@publisher_database_id**an, die aus der **database_id** Spalte in der [sys. Database](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) -Katalog Sicht abgerufen werden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuertes Überwachen der Replikation](../monitoring-replication.md)  
  
  
