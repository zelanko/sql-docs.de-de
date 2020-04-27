---
title: Anzeigen von Informationen zu einer Warnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c5567abc0893bd183c2468f82278a014e2005113
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211297"
---
# <a name="view-information-about-an-alert"></a>View Information About an Alert
  In diesem Thema wird beschrieben, wie Sie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationen zu- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Agent- [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Warnungen [!INCLUDE[tsql](../../includes/tsql-md.md)]in mithilfe von oder anzeigen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So zeigen Sie Informationen zu einer Warnung an mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** Information über eine Warnung anzeigen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-alert"></a>So zeigen Sie Informationen zu einer Warnung an  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie Informationen über eine Warnung anzeigen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um den Ordner **Warnungen** zu erweitern.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Warnung mit den von Ihnen gewünschten Informationen, die Sie anzeigen möchten, und wählen Sie **Eigenschaften**aus.  
  
     Weitere Informationen zu den im Dialogfeld _Eigenschaften von Warnung_**Warnungsname** enthaltenen verfügbaren Optionen finden Sie unter:  
  
    -   [Warnungs Eigenschaften-neue Warnung &#40;Seite "Allgemein"&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [Warnungs Eigenschaften-Seite "neue Warnung &#40;Antwort"&#41;](alert-properties-new-alert-response-page.md)  
  
    -   [Warnungs Eigenschaften: Seite "neue Warnung &#40;Optionen"&#41;](alert-properties-new-alert-options-page.md)  
  
    -   [Warnungseigenschaften &#40;Seite „Verlauf“&#41;](alert-properties-history-page.md)  
  
5.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-information-about-an-alert"></a>So zeigen Sie Informationen zu einer Warnung an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_help_alert &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).  
  
  
