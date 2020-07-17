---
title: Anzeigen einer Datenbank-Momentaufnahme (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe von SQL Server Management Studio oder Transact-SQL eine SQL Server-Datenbankmomentaufnahme anzeigen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7ba50746752b0c3531d1ae3a0b1b9d4820dea82
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727536"
---
# <a name="view-a-database-snapshot-sql-server"></a>Anzeigen einer Datenbank-Momentaufnahme (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird erläutert, wie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank-Momentaufnahme mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angezeigt wird.  
  
> [!NOTE]  
>  Wenn Sie Datenbank-Momentaufnahmen erstellen, wiederherstellen oder löschen möchten, müssen Sie [!INCLUDE[tsql](../../includes/tsql-md.md)]verwenden.  
  
 **In diesem Thema**  
  
-   **Anzeigen einer Datenbank-Momentaufnahme mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So zeigen Sie eine Datenbankmomentaufnahme an**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her, und erweitern Sie die Instanz.  
  
2.  Erweitern Sie **Datenbanken**.  
  
3.  Erweitern Sie **Datenbank-Momentaufnahmen**, und wählen Sie die gewünschte Momentaufnahme aus.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So zeigen Sie eine Datenbankmomentaufnahme an**  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Zum Anzeigen der Datenbank-Momentaufnahmen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz fragen Sie die Spalte **source_database_id** der [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) -Katalogsicht nach Nicht-NULL-Werten ab.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer Datenbankmomentaufnahme &#40;Transact-SQL&#41;](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [Wiederherstellen einer Datenbank zu einer Datenbank-Momentaufnahme](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
-   [Löschen einer Datenbankmomentaufnahme &#40;Transact-SQL&#41;](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Momentaufnahmen &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
