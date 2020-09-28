---
description: Auflisten von Informationen zu Auftragskategorien
title: Auflisten von Informationen zu Auftragskategorien
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 87a72d720e751999e8de2a1f6e76df43c7348462
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480325"
---
# <a name="list-job-category-information"></a>Auflisten von Informationen zu Auftragskategorien
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie Auftragskategorieinformationen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects auflisten können.  
  
-   **Vorbereitungen:**  
  
    [Security](#Security)  
  
-   **So listen Sie Informationen zu Auftragskategorien auf, und zwar mit**  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Verwenden von Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>So listen Sie Informationen zu Auftragskategorien auf  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde_md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
Weitere Informationen finden Sie unter [sp_help_category (Transact-SQL)](https://msdn.microsoft.com/8cad1dcc-b43e-43bd-bea0-cb0055c84169).  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Verwendung von SQL Server Management Objects  
**So listen Sie Informationen zu Auftragskategorien auf**  
  
Verwenden Sie die **JobCategory** -Klasse, indem Sie eine von Ihnen ausgewählte Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell verwenden.  
  
