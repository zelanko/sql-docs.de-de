---
title: Zulassen, dass Nichtadministratoren den Replikationsmonitor verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4a7699c555086d627e4c3a52ea70acf931ea1af
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068648"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>Zulassen, dass Nichtadministratoren den Replikationsmonitor verwenden
  In diesem Thema wird beschrieben, wie Nicht-Administratoren ermöglicht wird, den Replikationsmonitor in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]zu verwenden. Der Replikationsmonitor kann von Benutzern verwendet werden, die Mitglieder der folgenden Rollen sind:  
  
-   Feste Serverrolle **sysadmin** .  
  
     Diese Benutzer können die Replikation überwachen und haben den vollen Zugriff in Bezug auf Änderungen der Replikationseigenschaften, wie beispielsweise Zeitpläne für Agents, Agentprofile usw.  
  
-   Die `replmonitor` Daten Bank Rolle in der Verteilungs Datenbank.  
  
     Diese Benutzer können die Replikation überwachen, aber keine Replikationseigenschaften ändern.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So ermöglichen Sie Nichtadministratoren die Verwendung des Replikationsmonitors mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Um nicht Administratoren die Verwendung des Replikations Monitors zu gestatten, muss ein Mitglied der festen Server Rolle **sysadmin** den Benutzer der Verteilungs Datenbank hinzufügen und diesen Benutzer der `replmonitor` Rolle zuweisen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>So lassen Sie zu, dass Nichtadministratoren den Replikationsmonitor verwenden  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie **Datenbanken**und **Systemdatenbanken**, und erweitern Sie die Verteilungsdatenbank (standardmäßig als **distribution** bezeichnet).  
  
3.  Erweitern Sie **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Benutzer**, und klicken Sie dann auf **Neuer Benutzer**.  
  
4.  Geben Sie einen Benutzernamen und ein Kennwort für den Benutzer ein.  
  
5.  Wählen Sie ein Standardschema aus `replmonitor` .  
  
6.  Aktivieren Sie das `replmonitor` Kontrollkästchen im Raster **Daten bankrollen Mitgliedschaft** .  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>So fügen Sie der festen Datenbankrolle "replmonitor" einen Benutzer hinzu  
  
1.  Führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql)aus. Wenn der Benutzer nicht im `UserName` Resultset aufgeführt ist, muss dem Benutzer mithilfe der Anweisung [Create User &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) Zugriff auf die Verteilungs Datenbank erteilt werden.  
  
2.  Führen Sie auf dem Verteiler für die Verteilungs Datenbank [sp_helprolemember &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)aus, und geben Sie dabei `replmonitor` den Wert für den-Parameter an **@rolename** . Wenn der Benutzer in `MemberName` dem Resultset aufgeführt ist, gehört der Benutzer bereits zu dieser Rolle.  
  
3.  Wenn der Benutzer nicht zur `replmonitor` Rolle gehört, führen Sie [sp_addrolemember &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) auf dem Verteiler für die Verteilungs Datenbank aus. Geben Sie den Wert `replmonitor` für **@rolename** und den Namen des Daten Bank Benutzers oder den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Anmelde Namen an, der für hinzugefügt wird **@membername** .  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>So entfernen Sie einen Benutzer aus der festen Datenbankrolle "replmonitor"  
  
1.  Um zu überprüfen, ob der Benutzer der `replmonitor` Rolle angehört, führen Sie [sp_helprolemember &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) auf dem Verteiler für die Verteilungs Datenbank aus, und geben Sie den Wert für an `replmonitor` **@rolename** . Wenn der Benutzer unter `MemberName` im Resultset nicht aufgeführt wird, gehört der Benutzer aktuell nicht zu der Rolle.  
  
2.  Wenn der Benutzer der `replmonitor` Rolle angehört, führen Sie [sp_droprolemember &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) auf dem Verteiler für die Verteilungs Datenbank aus. Geben Sie den Wert `replmonitor` für **@rolename** und den Namen des Daten Bank Benutzers oder den Windows-Anmelde Namen an, der für entfernt wird **@membername** .  
  
  
