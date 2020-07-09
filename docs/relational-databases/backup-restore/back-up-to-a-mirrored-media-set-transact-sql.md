---
title: Sichern auf einem gespiegelten Mediensatz (Transact-SQL) | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie mit der Transact-SQL-Anweisung BACKUP beim Sichern einer SQL Server-Datenbank einen gespiegelten Mediensatz angeben.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dcaa9ed0516767a590af02bebf521215411a3c4d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722493"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>Sichern auf einem gespiegelten Mediensatz (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Artikel wird beschrieben, wie Sie mit der [BACKUP](../../t-sql/statements/backup-transact-sql.md)-Anweisung ([!INCLUDE[tsql](../../includes/tsql-md.md)]) einen gespiegelten Mediensatz beim Sichern einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank angeben. Geben Sie in der BACKUP-Anweisung den ersten Spiegel in der TO-Klausel an. Geben Sie anschließend jeden Spiegel in der MIRROR TO-Klausel des Spiegels an. In den TO- und MIRROR TO-Klauseln müssen die gleiche Anzahl und der gleiche Typ von Sicherungsmedien angegeben werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der in der vorherigen Abbildung dargestellte gespiegelte Mediensatz erstellt und die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank auf beiden Spiegeln gesichert.  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a>Related Tasks  
 **So stellen Sie Daten von einer gespiegelten Sicherung wieder her**  
  
-   [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Gespiegelte Sicherungsmediensätze &#40;SQL Server&#41;](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md)  
  
  
