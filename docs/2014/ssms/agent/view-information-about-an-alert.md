---
title: Anzeigen von Informationen zu einer Warnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
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
ms.openlocfilehash: e7bb9ec006ee49a7b446fd2700df81debea1012d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48167590"
---
# <a name="view-information-about-an-alert"></a>View Information About an Alert
  In diesem Thema wird beschrieben, wie Sie Infodermationen in Bezug auf [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]anzeigen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So zeigen Sie Informationen zu einer Warnung an mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** Information über eine Warnung anzeigen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-alert"></a>So zeigen Sie Informationen zu einer Warnung an  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie Informationen über eine Warnung anzeigen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um den Ordner **Warnungen** zu erweitern.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Warnung mit den von Ihnen gewünschten Informationen, die Sie anzeigen möchten, und wählen Sie **Eigenschaften**aus.  
  
     Weitere Informationen zu den im Dialogfeld *Warnungsname***Warnungseigenschaften** enthaltenen verfügbaren Optionen finden Sie unter:  
  
    -   [Warnung-Eigenschaften – neue Warnung &#40;Seite "Allgemein"&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [Warnung-Eigenschaften – neue Warnung &#40;Seite "Antwort"&#41;](alert-properties-new-alert-response-page.md)  
  
    -   [Eigenschaften von Warnung: Neue Warnung &#40;Seite "Optionen"&#41;](alert-properties-new-alert-options-page.md)  
  
    -   [Warnungseigenschaften &#40;Seite „Verlauf“&#41;](alert-properties-history-page.md)  
  
5.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-information-about-an-alert"></a>So zeigen Sie Informationen zu einer Warnung an  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
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
  
 Weitere Informationen finden Sie unter [Sp_help_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).  
  
  
