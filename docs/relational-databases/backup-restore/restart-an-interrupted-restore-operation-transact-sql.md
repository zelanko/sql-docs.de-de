---
title: Neustarten einer unterbrochenen Wiederherstellung (Transact-SQL)
description: In diesem Artikel erfahren Sie, wie Sie einen unterbrochenen Wiederherstellungsvorgang in SQL Server mithilfe von Transact-SQL neu starten.
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
author: cawrites
ms.author: chadam
ms.openlocfilehash: f2c70762e4e68081fc63930b1140ba904a5ca565
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "96129143"
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a>Erneutes Starten eines unterbrochenen Wiederherstellungsvorgangs (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema erfahren Sie, wie Sie einen unterbrochenen Wiederherstellungsvorgang erneut starten.  
  
### <a name="to-restart-an-interrupted-restore-operation"></a>So starten Sie einen unterbrochenen Wiederherstellungsvorgang neu  
  
1.  Führen Sie die unterbrochene RESTORE-Anweisung erneut aus, und geben Sie dabei Folgendes an:  
  
    -   Dieselben Klauseln, die auch in der ursprünglichen RESTORE-Anweisung verwendet wurden.  
  
    -   Die RESTART-Klausel.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird ein unterbrochener Wiederherstellungsvorgang erneut gestartet.  
  
```sql  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Vollständige Datenbankwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
