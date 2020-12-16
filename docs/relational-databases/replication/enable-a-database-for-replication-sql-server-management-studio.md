---
title: Aktivieren einer Datenbank für die Replikation (SSMS)
description: Hier erfahren Sie, wie Sie eine Datenbank für die Replikation mithilfe von SQL Server Management Studio (SSMS) oder Transact-SQL (T-SQL) aktivieren.
ms.custom: seo-lt-2019
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: a22a2bb5e57bd80fdc868bf461af758831a3c9ec
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460273"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>Aktivieren einer Datenbank für die Replikation (SQL Server Management Studio)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  
Eine Datenbank wird implizit für die Replikation aktiviert, wenn ein Mitglied der festen Serverrolle **sysadmin** mit dem Assistenten für neue Veröffentlichung eine Veröffentlichung erstellt. Ein Mitglied der festen Serverrolle **sysadmin** kann eine Datenbank auch explizit für die Replikation aktivieren, sodass ein Mitglied der festen Datenbankrolle **db_owner** eine oder mehrere Veröffentlichungen in der Datenbank erstellen kann. Verwenden Sie zum expliziten Aktivieren einer Datenbank die Seite **Veröffentlichungsdatenbanken** im Dialogfeld **Verlegereigenschaften - \<Publisher>** . Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
## <a name="using-sql-server-management-studio-ssms"></a>Verwenden von SQL Server Management Studio (SSMS)
  
1.  Aktivieren Sie auf der Seite **Veröffentlichungsdatenbanken** im Dialogfeld **Verlegereigenschaften - \<Publisher>** das Kontrollkästchen **Transaktionsreplikation** und/oder **Mergereplikation** für jede Datenbank, die Sie replizieren möchten. Aktivieren Sie **Transaktionsreplikation** , um die Datenbank für die Momentaufnahmereplikation zu aktivieren.  
  
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
