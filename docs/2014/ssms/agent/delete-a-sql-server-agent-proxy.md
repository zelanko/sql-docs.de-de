---
title: Löschen eines SQL Server-Agent-Proxys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9222253c884fdf3cfa52d283f250580a02a9f7ee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62523756"
---
# <a name="delete-a-sql-server-agent-proxy"></a>Delete a SQL Server Agent Proxy
  In diesem Thema wird beschrieben, wie Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxykonto in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So löschen Sie einen SQL Server-Agent-Proxykonto mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie das Proxykonto eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents löschen, sollten Sie sicherstellen, dass der Proxy keine Verweise auf aktive Auftragsschritte enthält. Klicken Sie mit der rechten Maustaste auf den Proxy, um nach Auftragsschritten zu suchen, die auf den Proxy verweisen. Wählen Sie **Eigenschaften**aus, und wählen Sie dann im Dialogfeld _Proxyname_**-Proxykonto** die Seite **Verweise** aus. Beim Löschen eines Proxys können Sie im Dialogfeld **Objekt löschen** die Auftragsschritte, die diesen Proxy verwenden, neu zuweisen.  
  
-   Von[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxys werden Anmeldeinformationen zum Speichern von Informationen zu Windows-Benutzerkonten verwendet. Der in der Anmeldeinformation angegebene Benutzer muss über eine Berechtigung des Typs "Anmelden als Stapelverarbeitungsauftrag" auf dem Computer verfügen, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent wird der Subsystemzugriff für einen Proxy überprüft und der Zugriff auf den Proxy jedes Mal dann gewährt, wenn der Auftragsschritt ausgeführt wird. Wenn der Proxyzugriff auf das Subsystem nicht mehr länger möglich ist, erzeugt der Auftragsschritt einen Fehler. Ansonsten wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die Identität des Benutzers angenommen, der im Proxy angegeben ist und von dem der Auftragsschritt ausgeführt wird.  
  
-   Wenn die Anmeldung für den Benutzer Zugriffsrecht auf den Proxy hat, oder der Benutzer zu einer Rolle mit Zugriffsrechten auf den Proxy gehört, kann der Benutzer den Proxy in einem Auftragsschritt verwenden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können Proxykonten erstellen, ändern oder löschen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>So löschen Sie ein SQL Server-Agent-Proxykonto  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, der das Proxykonto enthält, das Sie löschen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um den Ordner **Proxys** zu erweitern.  
  
4.  Klicken Sie im Objekt-Explorer auf das Pluszeichen, um das Subsystem zu erweitern, das zu löschende Proxykonto enthält (z. B. **ActiveX-Skript**).  
  
5.  Klicken Sie mit der rechten Maustaste auf das Proxykonto, das Sie löschen möchten, und klicken Sie dann auf **Löschen**.  
  
6.  Bestätigen Sie im Dialogfeld **Objekt löschen** , dass das richtige Proxykonto ausgewählt ist. Aktivieren Sie das Kontrollkästchen **Neu zuweisen an** , um die Auftragsschritte, die auf dieses Proxykonto verweisen, einem anderen Proxykonto zuzuweisen.  
  
7.  Klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>So löschen Sie ein SQL Server-Agent-Proxykonto  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_delete_proxy &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql).  
  
  
