---
description: Give Others Ownership of a Job
title: Give Others Ownership of a Job
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 9a1dc39795646c704d8168858475095cd549cb0e
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461361"
---
# <a name="give-others-ownership-of-a-job"></a>Give Others Ownership of a Job
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Artikel wird beschrieben, wie Sie den Besitz von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Aufträgen einem anderen Benutzer zuweisen.  
  
-   **Vorbereitungen:**  [Beschränkungen](#Restrictions), [Sicherheit](#Security)  
  
-   **So ändern Sie den Besitz eines Auftrags mit:**  
  
    [SQL Server Management Studio](#SSMSProc2)  
  
    [Transact-SQL](#TsqlProc2)  
  
    [SQL Server Management Objects](#SMOProc2)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Einschränkungen  
Um einen Auftrag erstellen zu können, muss ein Benutzer Mitglied einer der festen Datenbankrollen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents oder Mitglied der festen Serverrolle **sysadmin** sein. Ein Auftrag kann nur von seinem Besitzer bzw. Mitgliedern der **sysadmin** -Rolle bearbeitet werden. Weitere Informationen zu den festen Datenbankrollen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Den Besitzer eines Auftrags können Sie nur ändern, wenn Sie als Systemadministrator angemeldet sind.  
  
Wenn Sie einen Auftrag einem anderen Anmeldenamen zuweisen, ist nicht sichergestellt, dass die Berechtigungen des neuen Besitzers zum erfolgreichen Ausführen des Auftrags ausreichen.  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
Aus Sicherheitsgründen kann nur der Auftragsbesitzer bzw. ein Mitglied der **sysadmin** -Rolle die Definition des Auftrags ändern. Nur Mitglieder der festen Serverrolle **sysadmin** können anderen Benutzern den Auftragsbesitz zuweisen. Zudem können sie unabhängig vom Auftragsbesitzer alle Aufträge ausführen.  
  
> [!NOTE]  
> Wenn Sie den Auftragsbesitz einem Benutzer zuweisen, der kein Mitglied der festen Serverrolle **sysadmin** ist, und wenn in dem Auftrag Schritte ausgeführt werden, für die Proxykonten erforderlich sind (beispielsweise die [!INCLUDE[ssIS](../../includes/ssis_md.md)] -Paketausführung), müssen Sie sicherstellen, dass der Benutzer auf dieses Proxykonto zugreifen kann. Andernfalls schlägt der Auftrag fehl.  
  
#### <a name="permissions"></a><a name="Permissions"></a>Berechtigungen  
Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProc2"></a>Verwenden von SQL Server Management Studio  
**So ändern Sie den Besitz eines Auftrags**  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie zunächst den **SQL Server-Agent**, anschließend **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, und wählen Sie dann **Eigenschaften** aus.  
  
3.  Wählen Sie aus der Liste **Besitzer** einen Anmeldenamen aus. Den Besitzer eines Auftrags können Sie nur ändern, wenn Sie als Systemadministrator angemeldet sind.  
  
    Wenn Sie einen Auftrag einem anderen Anmeldenamen zuweisen, ist nicht sichergestellt, dass die Berechtigungen des neuen Besitzers zum erfolgreichen Ausführen des Auftrags ausreichen.  
  
## <a name="using-transact-sql"></a><a name="TsqlProc2"></a>Verwenden von Transact-SQL  
**So ändern Sie den Besitz eines Auftrags**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von Database Engine (Datenbankmodul) her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
3.  Geben Sie im Abfragefenster die folgenden Anweisungen ein, bei denen die gespeicherte Systemprozedur [sp_manage_jobs_by_login (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql.md) verwendet wird. Im folgenden Beispiel erfolgt eine Neuzuweisung aller Aufträge von `danw` an `françoisa`.  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'françoisa' ;  
    GO  
    ```  
  
## <a name="using-sql-server-management-objects"></a><a name="SMOProc2"></a>Verwendung von SQL Server Management Objects  
**So ändern Sie den Besitz eines Auftrags**  
  
1.  Rufen Sie die **Job** -Klasse auf, indem Sie eine von Ihnen ausgewählte Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell verwenden. Beispielcode hierzu finden Sie unter [Planen von automatischen, administrativen Tasks im SQL Server-Agent](../../relational-databases/server-management-objects-smo/tasks/scheduling-automatic-administrative-tasks-in-sql-server-agent.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
[Erstellen von Aufträgen](../../ssms/agent/create-jobs.md)  
