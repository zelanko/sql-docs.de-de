---
title: Configure a User to Create and Manage SQL Server Agent Jobs
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6c492a7875eed70cc58efa2dcae8ac180229e5ad
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75246499"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Configure a User to Create and Manage SQL Server Agent Jobs
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie einen Benutzer zum Erstellen oder Ausführen von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Aufträgen konfigurieren.  
  
-   **Vorbereitungen:**  [Sicherheit](#Security)  
  
-   **Konfigurieren eines Benutzers zum Erstellen und Verwalten von SQL Server-Agent-Aufträgen mithilfe von**  [SQL Server Management Studio](#SSMS)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
Wenn Sie einen Benutzer für das Erstellen oder Ausführen von Aufträgen des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents konfigurieren möchten, müssen Sie zunächst eine vorhandene SQL Server-Anmeldung oder eine msdb-Rolle für eine der folgenden festen Datenbankrollen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents in der msdb-Datenbank hinzufügen: SQLAgentUserRole, SQLAgentReaderRole oder SQLAgentOperatorRole.  
  
Standardmäßig können Mitglieder dieser Datenbankrollen ihre eigenen Auftragsschritte erstellen, die unter ihrem Konto ausgeführt werden. Falls Benutzer, die keine Administratoren sind, Aufträge ausführen möchten, mit denen andere Arten von Auftragsschritten ausgeführt werden (z. B. [!INCLUDE[ssIS](../../includes/ssis_md.md)] -Pakete), benötigen sie Zugriff auf ein Proxykonto. Alle Mitglieder der festen Serverrolle sysadmin haben die Berechtigung zum Erstellen, Ändern und Löschen von Proxykonten. Weitere Informationen zu den Berechtigungen, die jeder dieser festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen zugeordnet sind, finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
#### <a name="permissions"></a><a name="Permissions"></a>Berechtigungen  
Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Verwenden von SQL Server Management Studio  
**So fügen Sie einer festen Datenbankrolle des SQL Server-Agents einen SQL-Anmeldenamen oder eine msdb-Rolle hinzu**  
  
1.  Erweitern Sie im **Objekt-Explorer**einen Server.  
  
2.  Erweitern Sie **Sicherheit**und anschließend **Anmeldungen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Anmeldenamen, den Sie der festen Datenbankrolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents hinzufügen möchten, und klicken Sie auf **Eigenschaften**.  
  
4.  Wählen Sie auf der Seite **Benutzerzuordnung** des Dialogfelds **Anmeldungseigenschaften** die Zeile aus, die **msdb**enthält.  
  
5.  Aktivieren Sie unter **Mitgliedschaft in Datenbankrolle für: msdb**das Kontrollkästchen für die entsprechende feste Datenbankrolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents.  
  
**So konfigurieren Sie ein Proxykonto zum Erstellen und Verwalten von Auftragsschritten des SQL Server-Agents**  
  
1.  Erweitern Sie im **Objekt-Explorer**einen Server.  
  
2.  Erweitern Sie **SQL Server-Agent**.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Proxys** , und klicken Sie dann auf **Neuer Proxy**.  
  
4.  Geben Sie im Dialogfeld **Neues Proxykonto** auf der Seite **Allgemein** den Proxynamen, den Anmeldeinformationsnamen und eine Beschreibung für den neuen Proxy an. Beachten Sie, dass Sie Anmeldeinformationen erstellen müssen, bevor Sie ein Proxykonto des SQL Server-Agents erstellen. Weitere Informationen zum Erstellen von Anmeldeinformationen finden Sie unter [How to: Anmeldeinformationen erstellen](https://msdn.microsoft.com/c1e77e91-2a69-40d9-b8b3-97cffc710586) und [ANMELDEINFORMATIONEN ERSTELLEN (Transact-SQL)](https://msdn.microsoft.com/d5e9ae69-41d9-4e46-b13d-404b88a32d9d).  
  
5.  Aktivieren Sie die entsprechenden Subsysteme für diesen Proxy.  
  
6.  Auf der Seite **Prinzipale** können Sie Anmeldenamen oder Rollen hinzufügen oder entfernen, um den Zugriff auf das Proxykonto zu erteilen oder zu entziehen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md)  
  
