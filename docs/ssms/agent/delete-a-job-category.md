---
description: Löschen einer Auftragskategorie
title: Löschen einer Auftragskategorie
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 346cdbc84fb6d4af293f96b7044b0afae07dabe7
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036582"
---
# <a name="delete-a-job-category"></a>Löschen einer Auftragskategorie
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie eine [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Auftragskategorie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects löschen können.  
  
Auftragskategorien helfen Ihnen dabei, Ihre Aufträge zum einfachen Filtern und Gruppieren zu organisieren. Sie können z. B. alle Aufträge für die Datenbanksicherung in der Datenbankwartungskategorie organisieren.  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Einschränkungen  
Wenn Sie eine benutzerdefinierte Auftragskategorie löschen, werden sie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgefordert, die Aufträge neu zuzuweisen, die in einer anderen Auftragskategorie zugewiesen wurden. Sie können nur benutzerdefinierte Auftragskategorien löschen.  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-job-category"></a>So löschen Sie eine Auftragskategorie  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie eine Auftragskategorie löschen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Aufträge** , und wählen Sie **Auftragskategorien verwalten**aus.  
  
4.  Klicken Sie im **Auftragskategorien verwalten** _server\_name_ auf die zu löschende Auftragskategorie.  
  
5.  Klicken Sie auf **Löschen**.  
  
6.  Klicken Sie im Dialogfeld **Auftragskategorien** auf **Ja**.  
  
7.  Schließen Sie das Dialogfeld **Auftragskategorien verwalten**_server\_name_.  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-job-category"></a>So löschen Sie eine Auftragskategorie  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde_md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
Weitere Informationen finden Sie unter [sp_delete_category (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md).  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Verwendung von SQL Server Management Objects  
**So löschen Sie eine Auftragskategorie**  
  
Rufen Sie die **JobCategory** -Klasse auf, indem Sie eine von Ihnen ausgewählte Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell verwenden.  
