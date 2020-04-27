---
title: Deaktivieren oder erneutes Aktivieren einer Warnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], reactivating
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- alerts [SQL Server], disabling
- reactivating alerts
- removing alerts
ms.assetid: 4cb37dc6-1134-405d-8590-58b44dcf63b2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 638ce62d8dd12764681c2b65a271d9ae13bb5d83
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68189339"
---
# <a name="disable-or-reactivate-an-alert"></a>Disable or Reactivate an Alert
  In diesem Thema wird beschrieben, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wie Sie eine-Agent-Warnung [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in mithilfe [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] von [!INCLUDE[tsql](../../includes/tsql-md.md)]oder deaktivieren oder erneut aktivieren.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So deaktivieren oder aktivieren eine Warnung erneut mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** Information in einer Warnung bearbeiten. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-disable-or-reactivate-an-alert"></a>So deaktivieren oder reaktivieren Sie eine Warnung  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, der die Warnung enthält, die Sie deaktivieren oder erneut aktivieren möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um den Ordner **Warnungen** zu erweitern.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Warnung, die Sie aktivieren möchten, und wählen Sie **Aktivieren** aus. Klicken Sie demgegenüber mit der rechten Maustaste auf die Warnung, die Sie deaktivieren möchten, und wählen Sie **Deaktivieren**aus.  
  
5.  Die Dialogfelder **Warnungen deaktivieren** oder **Warnungen aktivieren** werden angezeigt. Außerdem wird der Status des Vorgangs angezeigt. Wenn Sie fertig sind, klicken Sie auf **Schließen**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-disable-or-reactivate-an-alert"></a>So deaktivieren oder reaktivieren Sie eine Warnung  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_update_alert &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).  
  
  
