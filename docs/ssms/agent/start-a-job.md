---
description: Starten eines Auftrags
title: Starten eines Auftrags
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e1bfdf49a974cafc80846684ffb37288f3e3bc27
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88370824"
---
# <a name="start-a-job"></a>Starten eines Auftrags
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects einen [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Auftrag in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ausführen.  
  
Ein Auftrag ist eine festgelegte Reihe von Aktionen, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträge können auf einem lokalen oder mehreren Remoteservern ausgeführt werden.  
  
-   **Vorbereitungen:**  
  
    [Security](#Security)  
  
-   **So starten Sie einen Auftrag an mit**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-start-a-job"></a>So starten Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent** , und erweitern Sie dann **Aufträge**. Führen Sie, je nachdem, wie der Auftrag gestartet werden soll, eine der folgenden Aktionen aus:  
  
    -   Wenn Sie auf einem einzelnen Server oder einem Zielserver arbeiten oder einen lokalen Serverauftrag auf einem Masterserver ausführen, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie starten möchten, und klicken Sie dann auf **Auftrag starten**.  
  
    -   Wenn Sie mehrere Aufträge starten möchten, klicken Sie mit der rechten Maustaste auf **Auftragsaktivitätsmonitor**, und klicken Sie dann auf **Auftragsaktivitäten anzeigen**. Im Auftragsaktivitätsmonitor können Sie mehrere Aufträge auswählen. Klicken Sie dazu mit der rechten Maustaste auf die Auswahl, und klicken Sie auf **Aufträge starten**.  
  
    -   Wenn Sie auf einem Masterserver arbeiten und alle Zielserver den Auftrag gleichzeitig ausführen sollen, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie starten möchten, klicken Sie auf **Auftrag starten**und dann auf **Auf allen Zielservern starten**.  
  
    -   Wenn Sie auf einem Masterserver arbeiten und Zielserver für den Auftrag angeben möchten, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie starten möchten, klicken Sie auf **Auftrag starten**und dann auf **Auf angegebenen Zielservern starten**. Aktivieren Sie im Dialogfeld **Downloadanweisungen bereitstellen** das Kontrollkästchen **Diese Zielserver** , und wählen Sie dann alle Zielserver aus, auf denen dieser Auftrag ausgeführt werden soll.  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Verwenden von Transact-SQL  
  
#### <a name="to-start-a-job"></a>So starten Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde_md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
Weitere Informationen finden Sie unter [sp_start_job (Transact-SQL)](https://msdn.microsoft.com/8a91df6a-eb84-4512-9a17-4a6e32a9538a).  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Verwendung von SQL Server Management Objects  
**So starten Sie einen Auftrag**  
  
Rufen Sie die **Start** -Methode der **Job** -Klasse in einer Programmiersprache Ihrer Wahl auf, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
