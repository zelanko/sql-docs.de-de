---
title: Abonnieren oder Abbestellen einer Richtlinienkategorie für eine Datenbank
description: In diesem Artikel wird erläutert, wie Sie eine Richtlinienkategorie für eine Datenbank für die richtlinienbasierte Verwaltung mithilfe von SQL Server Management Studio und Transact-SQL (T-SQL) abonnieren oder abbestellen.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.dmf.groupsubscription.f1
ms.assetid: d2c31769-7098-428e-ad9c-ef56541b7c52
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c8b658fc2589ad0c39173ac206036b8274acc858
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774134"
---
# <a name="subscribe-or-unsubscribe-a-database--to-a-policy-category"></a>Abonnieren einer Richtlinienkategorie für eine Datenbank bzw. Kündigen des Abonnements
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] eine Richtlinienkategorie für eine Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] abonniert bzw. das Abonnement gekündigt wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Abonnieren einer Richtlinienkategorie für eine Datenbank bzw. Kündigen des Abonnements mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner".  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-subscribe-or-unsubscribe-a-database-to-a-policy-category"></a>So abonnieren Sie eine Richtlinienkategorie für eine Datenbank bzw. kündigen das Abonnement  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, der die Datenbank enthält, in der Sie Kategorieabonnements verwalten möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Datenbanken** zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, in der Sie Kategorieabonnements verwalten möchten, zeigen Sie auf **Richtlinien**, und wählen Sie **Kategorien**aus.  
  
     Die folgenden Optionen sind im Dialogfeld **Kategorien** verfügbar:  
  
     Spalte erweitern  
     Klicken Sie, um eine Richtlinienkategorie zu erweitern. Dadurch werden alle in der Kategorie enthaltenen Richtlinien aufgelistet.  
  
     **Name**  
     Der Name der Richtlinienkategorie.  
  
     **Abonniert**  
     Gibt an, ob das Ziel die Richtlinienkategorie abonniert hat. Wenn dieses Kontrollkästchen deaktiviert ist, wird die Richtlinienkategorie für **Datenbankabonnements beauftragen**festgelegt. Dies bedeutet, dass die Richtlinienkategorie für alle Datenbanken auf dem Server gilt.  
  
     **Richtlinie**  
     Wenn Richtliniengruppen erweitert werden, werden die Richtlinien in der Richtlinienkategorie angezeigt.  
  
     **Aktiviert**  
     Gibt an, ob die Richtlinien aktiviert oder deaktiviert sind.  
  
     **Ausführungsmodus**  
     Zeigt den Ausführungsmodus der Richtlinie an.  
  
     **History**  
     Klicken Sie auf den Link Verlauf anzeigen, um den Protokolldatei-Viewer zu öffnen und den Richtlinienverlauf anzuzeigen.  
  
4.  Um eine Kategorie der richtlinienbasierten Verwaltung zu abonnieren, aktivieren Sie das Kontrollkästchen der Kategorie unter der Spalte **Abonniert** . Um das Abonnement einer Kategorie zu kündigen, deaktivieren Sie das Kontrollkästchen.  
  
5.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-subscribe-a-database-to-a-policy-category"></a>So abonnieren Sie eine Richtlinienkategorie für eine Datenbank  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    -- Adds a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql.md).  
  
#### <a name="to-unsubscribe-a-database-to-a-policy-category"></a>So kündigen Sie das Abonnement einer Richtlinienkategorie für eine Datenbank  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    -- Deletes a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md).  
  
  
