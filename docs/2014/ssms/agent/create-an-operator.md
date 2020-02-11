---
title: Erstellen eines Operators | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d3a5414e845d8e625c852d628bf0d965432bc72a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63136420"
---
# <a name="create-an-operator"></a>Create an Operator
  In diesem Thema wird beschrieben, wie Sie einen Benutzer so konfigurieren [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dass er [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Benachrichtigungen über [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] - [!INCLUDE[tsql](../../includes/tsql-md.md)]Agent-Aufträge in mithilfe von oder empfängt.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So erstellen Sie einen Operator mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die Pager-und **net send** -Optionen werden in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einer zukünftigen Version von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aus dem-Agent entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktionen zurzeit verwenden.  
  
-   Beachten Sie, dass E-Mail- und Pagerbenachrichtigungen an Operatoren nur versendet werden können, wenn der SQL Server-Agent für die Verwendung von Datenbank-E-Mail konfiguriert ist. Weitere Informationen finden Sie unter [Zuweisen von Warnungen zu einem Operator](assign-alerts-to-an-operator.md).  
  
-   
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Aufträge problemlos mithilfe einer grafischen Oberfläche verwaltet werden. Dies ist die empfohlene Vorgehensweise für die Erstellung und Verwaltung der Auftragsinfrastruktur.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können Operatoren erstellen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-an-operator"></a>So erstellen Sie einen Operator  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, auf dem Sie den SQL Server-Agent-Operator erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Operatoren** , und wählen Sie dann **Neuer Operator**aus.  
  
     Die folgenden Optionen befinden sich im Dialogfeld **Neuer Operator** auf der Seite **Allgemein** :  
  
     **Name**  
     Ändern Sie den Namen des Operators.  
  
     **Aktiviert**  
     Aktiviert den Operator. Bei fehlender Aktivierung werden keine Benachrichtigungen an den Operator gesendet.  
  
     **Name der E-Mail**  
     Gibt die E-Mail-Adresse des Operators an.  
  
     **NET SEND-Adresse**  
     Gibt die für **NET SEND**zu verwendende Adresse an.  
  
     **Pager-e-Mail**  
     Gibt die E-Mail-Adresse für den Pager des Operators an.  
  
     **Pager nach Zeitplan**  
     Legt fest, zu welchen Zeiten der Pager aktiv ist.  
  
     **Montag-Sonntag**  
     Wählen Sie die Tage aus, an denen der Pager aktiv ist.  
  
     **Workday BEGIN**  
     Wählen Sie die Tageszeit aus, nach deren Eintreten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent Meldungen an den Pager sendet.  
  
     **Arbeitstag-Ende**  
     Wählen Sie die Tageszeit aus, nach deren Eintreten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent keine weiteren Meldungen an den Pager sendet.  
  
     Die folgenden Optionen befinden sich im Dialogfeld **Neuer Operator** auf der Seite **Benachrichtigungen** :  
  
     **Warnungen**  
     Zeigt die Warnungen in der Instanz an.  
  
     **Aufträge**  
     Zeigt die Aufträge in der Instanz an.  
  
     **Warnungs Liste**  
     Listet die Warnungen in der Instanz auf.  
  
     **Auftragsliste**  
     Listet die Aufträge in der Instanz auf.  
  
     **E**  
     Benachrichtigt den Operator per E-Mail.  
  
     **Pager**  
     Benachrichtigt den Operator, indem eine E-Mail-Nachricht an die Pageradresse gesendet wird.  
  
     **NET SEND**  
     Benachrichtigt diesen Operator per **net send**.  
  
4.  Klicken Sie auf **OK**, wenn Sie das Erstellen des neuen Operators abgeschlossen haben.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-an-operator"></a>So erstellen Sie einen Operator  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- sets up the operator information for user 'danwi.' The operator is enabled.   
    -- SQL Server Agent sends notifications by pager from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_add_operator &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql).  
  
  
