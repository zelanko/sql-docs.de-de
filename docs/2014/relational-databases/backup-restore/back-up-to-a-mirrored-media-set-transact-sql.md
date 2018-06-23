---
title: Sichern auf einem gespiegelten Mediensatz (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ee57f4caeba9747e3d4d9b1ac8577d7bf0ca486
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160234"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>Sichern auf einem gespiegelten Mediensatz (Transact-SQL)
  In diesem Thema wird beschrieben, wie die [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) -Anweisung zum Angeben eines gespiegelten Mediensatzes beim Sichern einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank verwendet wird. Geben Sie in der BACKUP-Anweisung den ersten Spiegel in der TO-Klausel an. Geben Sie anschließend jeden Spiegel in der MIRROR TO-Klausel des Spiegels an. In den TO- und MIRROR TO-Klauseln müssen die gleiche Anzahl und der gleiche Typ von Sicherungsmedien angegeben werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der in der vorherigen Abbildung dargestellte gespiegelte Mediensatz erstellt und die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank auf beiden Spiegeln gesichert.  
  
```  
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
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Gespiegelte Sicherungsmediensätze &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)  
  
  
