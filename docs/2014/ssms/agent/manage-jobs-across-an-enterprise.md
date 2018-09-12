---
title: Verwalten von Aufträgen über ein gesamtes Unternehmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: adb40ead9f932e2b9de46623ab3c90f94090e28a
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43809896"
---
# <a name="manage-jobs-across-an-enterprise"></a>Verwalten von Aufträgen über ein gesamtes Unternehmen
  Wenn Sie Änderungen an den Definitionen von Multiserveraufträgen außerhalb von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] vornehmen, müssen Sie die Änderungen der Downloadliste bereitstellen, damit die Zielserver erneut einen Download des aktualisierten Auftrags durchführen können. Um sicherzustellen, dass die Zielserver über aktuelle Auftragsdefinitionen verfügen, führen Sie nach dem Aktualisieren des Multiserverauftrags eine INSERT-Anweisung aus:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 Um Zielserver darüber zu benachrichtigen, dass ein Multiserverauftrag geändert wurde, müssen Sie den vorherigen Befehl aufrufen, nachdem Sie eine der folgenden Prozeduren verwendet haben:  
  
-   [sp_add_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_update_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)  
  
-   [sp_delete_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)  
  
-   [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [sp_detach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql)  
  
    > [!NOTE]  
    >  Es ist nicht notwendig, **sp_post_msx_operation** aufzurufen, nachdem Sie **sp_update_job** oder **sp_delete_job**aufgerufen haben, da diese gespeicherten Prozeduren automatisch die notwendigen Änderungen der Downloadliste bereitstellen.  
  
 Mithilfe der folgenden Tasks werden häufig Aufträge über ein gesamtes Unternehmen hinweg verwaltet:  
  
 **So überprüfen Sie den Status eines Zielservers**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)  
  
-   [SQL Server Management Objects (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **So wechseln Sie die Zielserver für einen Auftrag**  
  
-   [SQL Server Management Studio](modify-the-target-servers-for-a-job.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
-   [SQL Server Management Objects (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **So ändern Sie den Speicherort eines Zielservers**  
  
-   [SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
-   [SQL Server Management Objects (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **So synchronisieren Sie die Uhren der Zielserver**  
  
-   [SQL Server Management Studio](synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)  
  
 **So erzwingen Sie, dass ein Zielserver den Masterserver abruft**  
  
-   [SQL Server Management Studio](force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Ereignissen](manage-events.md)  
  
  
