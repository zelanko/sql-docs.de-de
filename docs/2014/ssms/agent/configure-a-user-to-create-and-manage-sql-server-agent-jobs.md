---
title: Konfigurieren eines Benutzers zum Erstellen und Verwalten von SQL Server-Agent-Aufträgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a62f6c2e1ef86a6fcd5e532b2ef413d8142698e6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63253561"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Konfigurieren eines Benutzers zum Erstellen und Verwalten von SQL Server-Agent-Aufträgen
  In diesem Thema wird beschrieben, wie Sie einen Benutzer zum Erstellen oder Ausführen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträgen konfigurieren.  
  
-   **Vorbereitungen:**  [Sicherheit](#Security)  
  
-   **Konfigurieren eines Benutzers zum Erstellen und Verwalten von SQL Server-Agent-Aufträgen mithilfe von**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Wenn Sie einen Benutzer für das Erstellen oder Ausführen von Aufträgen des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents konfigurieren möchten, müssen Sie zunächst einen vorhandenen SQL Server-Anmeldenamen oder eine msdb-Rolle für eine der folgenden festen Datenbankrollen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents in der msdb-Datenbank hinzufügen: SQLAgentUserRole, SQLAgentReaderRole oder SQLAgentOperatorRole.  
  
 Standardmäßig können Mitglieder dieser Datenbankrollen ihre eigenen Auftragsschritte erstellen, die unter ihrem Konto ausgeführt werden. Falls Benutzer, die keine Administratoren sind, Aufträge ausführen möchten, mit denen andere Arten von Auftragsschritten ausgeführt werden (z. B. [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Pakete), benötigen sie Zugriff auf ein Proxykonto. Alle Mitglieder der festen Serverrolle sysadmin haben die Berechtigung zum Erstellen, Ändern und Löschen von Proxykonten. Weitere Informationen zu den Berechtigungen, die jeder dieser festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen zugeordnet sind, finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](sql-server-agent-fixed-database-roles.md).  
  
####  <a name="Permissions"></a> Berechtigungen  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwendung von SQL Server Management Studio  
 **So fügen Sie einer festen Datenbankrolle des SQL Server-Agents einen SQL-Anmeldenamen oder eine msdb-Rolle hinzu**  
  
1.  Erweitern Sie im **Objekt-Explorer**einen Server.  
  
2.  Erweitern Sie **Sicherheit**und anschließend **Anmeldungen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Anmeldenamen, den Sie der festen Datenbankrolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents hinzufügen möchten, und klicken Sie auf **Eigenschaften**.  
  
4.  Auf der **Benutzerzuordnung** auf der Seite die **Anmeldungseigenschaften** Dialogfeld Feld, wählen Sie die Zeile mit `msdb`.  
  
5.  Aktivieren Sie unter **Mitgliedschaft in Datenbankrolle für: msdb**das Kontrollkästchen für die entsprechende feste Datenbankrolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents.  
  
 **So konfigurieren Sie ein Proxykonto zum Erstellen und Verwalten von Auftragsschritten des SQL Server-Agents**  
  
1.  Erweitern Sie im **Objekt-Explorer**einen Server.  
  
2.  Erweitern Sie **SQL Server-Agent**.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Proxys** , und klicken Sie dann auf **Neuer Proxy**.  
  
4.  Geben Sie im Dialogfeld **Neues Proxykonto** auf der Seite **Allgemein** den Proxynamen, den Anmeldeinformationsnamen und eine Beschreibung für den neuen Proxy an. Beachten Sie, dass Sie Anmeldeinformationen erstellen müssen, bevor Sie ein Proxykonto des SQL Server-Agents erstellen. Weitere Informationen zum Erstellen von Anmeldeinformationen finden Sie unter [Erstellen von Anmeldeinformationen](../../relational-databases/security/authentication-access/create-a-credential.md) und [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).  
  
5.  Aktivieren Sie die entsprechenden Subsysteme für diesen Proxy.  
  
6.  Auf der Seite **Prinzipale** können Sie Anmeldenamen oder Rollen hinzufügen oder entfernen, um den Zugriff auf das Proxykonto zu erteilen oder zu entziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md)  
  
  
