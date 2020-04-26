---
title: Festlegen des Dienst Start Kontos für SQL Server-Agent (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30c50d1f6efc44c17eac76e0e03432c2461da296
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033659"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)
  Das Dienststartkonto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents definiert das Windows-Konto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt wird, sowie die zugehörigen Netzwerkberechtigungen. In diesem Thema wird beschrieben, wie Sie das Dienstkonto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]festlegen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   [So legen Sie das Dienststartkonto für den SQL Server-Agent mit SQL Server Management Studio fest](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Seit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]muss das Dienststartkonto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent nicht mehr ein Mitglied der Administratorengruppe von [!INCLUDE[msCoName](../../includes/msconame-md.md)] sein. Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienststartkonto muss jedoch ein Mitglied der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Serverrolle „sysadmin“ sein. Das Konto muss Mitglied der „msdb“-Datenbankrolle „TargetServersRole“ auf dem Masterserver sein, um die Multiserver-Auftragsverarbeitung verwenden zu können.  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten wird nur im Objekt-Explorer angezeigt, wenn Sie die Berechtigung besitzen, ihn zu verwenden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Der-Agent muss für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Verwendung der Anmelde Informationen eines Kontos konfiguriert werden, das Mitglied der `sysadmin` Fixed-Server Rolle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das-Agent-Dienst Konto erforderlich sind, finden [Sie unter Auswählen eines Kontos für den SQL Server-Agent Dienst](select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienst Konten und-Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>So legen Sie das Dienststartkonto für den SQL Server-Agent fest  
  
1.  Klicken Sie in **Registrierte Server**auf das Pluszeichen, um **Datenbank-Engine**zu erweitern.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Lokale Servergruppen** zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Serverinstanz, auf der Sie das Dienststartkonto festlegen möchten, und wählen Sie dann **SQL Server-Konfigurations-Manager** aus.  
  
4.  Klicken Sie im Dialogfeld **Benutzerkontensteuerung** auf **Ja**.  
  
5.  Wählen Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager im Konsolenbereich **SQL Server-Dienste**aus.  
  
6.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **SQL Server-Agent**_(Servername)_, wobei *Servername* der Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Instanz ist, für die Sie das Dienststartkonto ändern möchten. Wählen Sie anschließend **Eigenschaften**aus.  
  
7.  Wählen Sie im Dialogfeld **Eigenschaften** von **SQL Server-Agent**_(server_name)_ auf der Registerkarte **Anmelden** eine der folgenden Optionen unter **Anmelden als**aus:  
  
    -   **Integriertes Konto**: Wählen Sie diese Option aus, wenn die Aufträge nur Ressourcen vom lokalen Server benötigen. Informationen zum Auswählen eines integrierten Kontotyps finden Sie unter [Auswählen eines Kontos für den SQL Server-Agent-Dienst](https://msdn.microsoft.com/library/ms191543.aspx).  
  
        > [!IMPORTANT]  
        >   Das lokale Dienstkonto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in **** wird nicht für den [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Agentdienst unterstützt.  
  
    -   **Dieses Konto**: Wählen Sie diese Option aus, wenn die Aufträge Ressourcen aus dem gesamten Netzwerk benötigen, einschließlich Anwendungsressourcen, wenn Sie Ereignisse an andere Windows-Anwendungsprotokolle weiterleiten möchten oder wenn Sie Operatoren per E-Mail oder Pager benachrichtigen möchten.  
  
         Bei Auswahl dieser Option:  
  
        1.  Geben Sie das Konto, das verwendet wird, um den SQL Server-Agent auszuführen, in das Feld **Kontoname** ein. Klicken Sie alternativ auf **Durchsuchen** , um das Dialogfeld **Benutzer oder Gruppe auswählen** zu öffnen, und wählen Sie das zu verwendende Konto aus.  
  
        2.  Geben Sie im Feld **Kennwort** das Kennwort für das Konto ein. Geben Sie im Feld **Kennwort bestätigen** das Kennwort erneut ein.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager auf die Schaltfläche **Schließen** .  
  
  
