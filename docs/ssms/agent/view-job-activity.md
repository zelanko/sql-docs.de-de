---
description: Auftragsaktivitäten anzeigen
title: Auftragsaktivitäten anzeigen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 04c42de9a98d507367cb2c2256a7c1f241baf1fc
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92030615"
---
# <a name="view-job-activity"></a>Auftragsaktivitäten anzeigen
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie den Laufzeitstatus von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträgen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]anzeigen können.  
  
Wenn der [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst startet, wird eine neue Sitzung erstellt, und die **sysjobactivity**-Tabelle in der **msdb**-Datenbank wird mit allen vorhandenen definierten Aufträgen aufgefüllt. In dieser Tabelle werden die aktuelle Auftragsaktivität und der aktuelle Auftragsstatus aufgezeichnet. Mithilfe des Auftragsaktivitätsmonitors im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent können Sie den aktuellen Status von Aufträgen anzeigen. Falls der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst unerwartet beendet wird, ersehen Sie aus der **sysjobactivity** -Tabelle, welche Aufträge ausgeführt wurden, als der Dienst beendet wurde.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-job-activity"></a>So zeigen Sie die Auftragsaktivität an  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung zu einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Auftragsaktivitätsmonitor** , und klicken Sie dann auf **Auftragsaktivitäten anzeigen**.  
  
4.  Im **Auftragsaktivitätsmonitor**können Sie Details zu jedem Auftrag anzeigen, der für diesen Server definiert ist.  
  
5.  Klicken Sie mit der rechten Maustaste auf einen Auftrag. Nun können Sie den Auftrag starten, beenden, aktivieren oder deaktivieren, löschen, dessen Status im Auftragsaktivitätsmonitor aktualisieren oder dessen Verlauf oder Eigenschaften anzeigen.  Um mehrere Aufträge zu starten, beenden, aktivieren, deaktivieren oder aktualisieren, wählen Sie mehrere Zeilen im Auftragsaktivitätsmonitor aus, und klicken Sie mit der rechten Maustaste auf die Auswahl.  
  
6.  Klicken Sie auf **Aktualisieren**, um den Auftragsaktivitätsmonitor zu aktualisieren. Um weniger Zeilen anzuzeigen, klicken Sie auf **Filter** , und geben Sie Filterparameter ein.  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Verwenden von Transact-SQL  
  
#### <a name="to-view-job-activity"></a>So zeigen Sie die Auftragsaktivität an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde_md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
Weitere Informationen finden Sie unter [sp_help_jobactivity (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql.md).  
