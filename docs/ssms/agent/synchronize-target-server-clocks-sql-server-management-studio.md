---
description: Synchronisieren der Uhren des Zielservers
title: Synchronisieren der Uhren des Zielservers
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 496a5e901ec802cbd7a7ffbb810a14ee31734dcc
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037756"
---
# <a name="synchronize-target-server-clocks"></a>Synchronisieren der Uhren des Zielservers

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie Zielserveruhren in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit der Masterserveruhr mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]synchronisieren können. Das Synchronisieren dieser Systemuhren unterstützt Auftragszeitpläne.  

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
  
#### <a name="permissions"></a><a name="Permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-synchronize-target-server-clocks"></a>So synchronisieren Sie die Uhren der Zielserver  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie die Zielserveruhren mit der Masterserveruhr synchronisieren möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserververwaltung**, und klicken Sie auf **Zielserver verwalten**.  
  
3.  Klicken Sie im Dialogfeld **Zielserver verwalten** auf **Anweisungen bereitstellen**.  
  
4.  Wählen Sie in der Liste **Anweisungstyp** die Option **Uhren synchronisieren**aus.  
  
5.  Führen Sie unter **Empfänger**eine der folgenden Aktionen aus:  
  
    -   Klicken Sie auf **Alle Zielserver** , um die Uhren aller Zielserver mit der Uhr des Masterservers zu synchronisieren.  
  
    -   Klicken Sie auf **Diese Zielserver** , um bestimmte Serveruhren zu synchronisieren, und wählen Sie dann alle Zielserver aus, deren Uhren mit der Uhr des Masterservers synchronisiert werden sollen.  
  
6.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a>Verwenden von Transact-SQL  
  
#### <a name="to-synchronize-target-server-clocks"></a>So synchronisieren Sie die Uhren der Zielserver  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde_md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
Weitere Informationen finden Sie unter [sp_resync_targetserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md).  
