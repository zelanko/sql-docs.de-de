---
title: Aktivieren einer Datenbank für die Replikation (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ac332e77226d5de33a4ef7fc77a0c34f6b234a3b
ms.sourcegitcommit: b2a29f9659f627116d0a92c03529aafc60e1b85a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59516486"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>Aktivieren einer Datenbank für die Replikation (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
Eine Datenbank wird implizit für die Replikation aktiviert, wenn ein Mitglied der festen Serverrolle **sysadmin** mit dem Assistenten für neue Veröffentlichung eine Veröffentlichung erstellt. Ein Mitglied der festen Serverrolle **sysadmin** kann eine Datenbank auch explizit für die Replikation aktivieren, sodass ein Mitglied der festen Datenbankrolle **db_owner** eine oder mehrere Veröffentlichungen in der Datenbank erstellen kann. Verwenden Sie zum expliziten Aktivieren einer Datenbank im Dialogfeld **Verlegereigenschaften – \<Verleger>** die Seite **Veröffentlichungsdatenbanken**. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
## <a name="using-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
  
1.  Aktivieren Sie im Dialogfeld **Verlegereigenschaften - \<Verleger>** auf der Seite **Veröffentlichungsdatenbanken** das Kontrollkästchen **Transaktionsreplikation** und/oder **Mergereplikation** für jede Datenbank, die Sie replizieren möchten. Aktivieren Sie **Transaktionsreplikation** , um die Datenbank für die Momentaufnahmereplikation zu aktivieren.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
## <a name="using-transact-sql-t-sql"></a>Transact-SQL (T-SQL)
Mit folgendem Transact-SQL-Code können Sie eine Datenbank für die Replikation aktivieren: 

```sql
USE master
EXEC sp_replicationdboption @dbname = 'AdventureWorks2017',
@optname = 'publish',
@value = 'true'
GO
```

Legen Sie @value = 'false' fest, um die Veröffentlichung zu deaktivieren. 
