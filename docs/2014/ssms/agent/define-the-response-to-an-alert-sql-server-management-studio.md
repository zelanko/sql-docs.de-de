---
title: Definieren der Antwort auf eine Warnung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6aad30767fa52a745d6d817074b1ede4740d989e
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43811996"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a>Definieren der Antwort auf eine Warnung (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie Sie definieren können, wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]reagiert.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So definieren Sie die Antwort auf eine Warnung mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die Pager- und **net send** -Optionen werden in zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht mehr im [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktionen zurzeit verwenden.  
  
-   Beachten Sie, dass E-Mail- und Pagerbenachrichtigungen an Operatoren nur versendet werden können, wenn der SQL Server-Agent für die Verwendung von Datenbank-E-Mail konfiguriert ist. Weitere Informationen finden Sie unter [Zuweisen von Warnungen zu einem Operator](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Aufträge problemlos mithilfe einer grafischen Oberfläche verwaltet werden. Dies ist die empfohlene Vorgehensweise für die Erstellung und Verwaltung der Auftragsinfrastruktur.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können die Antwort auf eine Warnung definieren.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-define-the-response-to-an-alert"></a>So definieren Sie die Antwort auf eine Warnung  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, der die Warnung enthält, für die Sie eine Warnung definieren möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um den Ordner **Warnungen** zu erweitern.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Warnung, für die Sie eine Antwort definieren möchten, und wählen Sie **Eigenschaften**aus.  
  
5.  Klicken Sie im Dialogfeld *Warnungsname***Warnungseigenschaften** unter **Seite auswählen** auf die Option **Antwort**.  
  
6.  Aktivieren Sie das Kontrollkästchen **Auftrag ausführen** , und wählen Sie aus der Liste unter dem Kontrollkästchen **Auftrag ausführen** einen Auftrag aus, der ausgeführt werden soll, wenn die Warnung angezeigt wird. Sie können einen neuen Auftrag erstellen, indem Sie auf **Neuer Auftrag**klicken. Um weitere Informationen zu dem Auftrag anzuzeigen, klicken Sie auf **Auftrag anzeigen**. Weitere Informationen zu den verfügbaren Optionen in den Dialogfeldern **Neuer Auftrag** und **Auftragseigenschaften***Auftragsname* finden Sie unter [Erstellen eines Auftrags](create-a-job.md) und [Anzeigen eines Auftrags](view-a-job.md).  
  
7.  Aktivieren Sie das Kontrollkästchen **Operatoren benachrichtigen** , sofern Sie Operatoren benachrichtigen möchten, wenn eine Warnung aktiviert ist. Wählen Sie in der Liste **Operator**mindestens eine der folgenden Methoden für die Benachrichtigung eines Operators bzw. von Operatoren aus: **E-Mail**, **Pager**oder **NET SEND**. Sie können einen neuen Operator erstellen, indem Sie auf **Neuer Operator**klicken. Um weitere Informationen über einen Operator anzuzeigen, klicken Sie auf **Operator anzeigen**. Weitere Informationen zu den verfügbaren Optionen im Dialogfeld **Neuer Operator** und im **Dialogfeld zum Anzeigen von Operatoreigenschaften** unter [Create an Operator](create-an-operator.md) und [View Information About an Operator](view-information-about-an-operator.md).  
  
8.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-define-the-response-to-an-alert"></a>So definieren Sie die Antwort auf eine Warnung  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that François Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'François Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [Sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).  
  
  
