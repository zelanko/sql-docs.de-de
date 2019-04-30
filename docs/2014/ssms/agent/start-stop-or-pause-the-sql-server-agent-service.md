---
title: Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f21d13149ffa90a2383e8f090b205b50efa54641
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63246139"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Start, Stop, or Pause the SQL Server Agent Service
  In diesem Thema wird beschrieben, wie Sie den SQL Server-Agent-Dienst in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten, beenden oder neu starten.  
  
 Sie können den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst so konfigurieren, dass er automatisch zusammen mit dem Betriebssystem gestartet wird, oder ihn manuell starten, wenn Sie Aufträge ausführen müssen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst kann beendet oder angehalten werden, um Aufträge, Operatorbenachrichtigungen und Warnungen auszusetzen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   [Starten, Beenden oder Neustarten des SQL Server-Agent-Diensts mit SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss als Dienst ausgeführt werden, um administrative Tasks zu automatisieren. Weitere Informationen finden Sie unter [Configure SQL Server Agent](configure-sql-server-agent.md).  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten wird nur im Objekt-Explorer angezeigt, wenn Sie die Berechtigung besitzen, ihn zu verwenden.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen, die für die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienstkonto finden Sie unter [Auswählen eines Kontos für den SQL Server-Agent-Dienst](select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienstkonten und Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>So können Sie den SQL Server-Agent-Dienst starten, beenden oder neu starten  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, auf dem Sie den SQL Server-Agent-Dienst verwalten möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und wählen Sie dann **Starten**, **Beenden**oder **Neu starten**aus.  
  
3.  Klicken Sie im Dialogfeld **Benutzerkontensteuerung** auf **Ja**.  
  
4.  Klicken Sie bei der Frage, ob die Aktion ausgeführt werden soll, auf **Ja**.  
  
 Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, SQL Server-Agent oder des SQL Server-Browsers](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
-   [Autostart SQL Server Agent &#40;SQL Server Management Studio&#41;](autostart-sql-server-agent-sql-server-management-studio.md)  
  
  
