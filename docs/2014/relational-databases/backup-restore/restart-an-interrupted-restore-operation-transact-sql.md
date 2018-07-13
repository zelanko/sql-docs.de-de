---
title: Erneutes Starten eines unterbrochenen Wiederherstellungsvorgangs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 872e3b59ccb8d3ae01957cf67ac1d7c368916613
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178117"
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a>Erneutes Starten eines unterbrochenen Wiederherstellungsvorgangs (Transact-SQL)
  In diesem Thema erfahren Sie, wie Sie einen unterbrochenen Wiederherstellungsvorgang erneut starten.  
  
### <a name="to-restart-an-interrupted-restore-operation"></a>So starten Sie einen unterbrochenen Wiederherstellungsvorgang neu  
  
1.  Führen Sie die unterbrochene RESTORE-Anweisung erneut aus, und geben Sie dabei Folgendes an:  
  
    -   Dieselben Klauseln, die auch in der ursprünglichen RESTORE-Anweisung verwendet wurden.  
  
    -   Die RESTART-Klausel.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird ein unterbrochener Wiederherstellungsvorgang erneut gestartet.  
  
```tsql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Vollständige Datenbankwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](complete-database-restores-full-recovery-model.md)   
 [Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](complete-database-restores-simple-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
