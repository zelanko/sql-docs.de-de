---
title: Senden von SQL Server-Agent-Fehlermeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- messages [SQL Server], SQL Server Agent
- sending messages
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 2597d0d7-951a-48cf-989f-abb67b9fdb36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c1aa0faafc6fb1cca693fe58665c7344db84c9f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62666787"
---
# <a name="send-sql-server-agent-error-messages"></a>Send SQL Server Agent Error Messages
  In diesem Thema wird beschrieben, wie der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent so konfiguriert wird, dass Fehlermeldungen mithilfe von NET [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Send in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mithilfe von gesendet werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   [So senden Sie SQL Server-Agent Fehlermeldungen mithilfe von SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten wird nur im Objekt-Explorer angezeigt, wenn Sie die Berechtigung besitzen, ihn zu verwenden.  
  
-   Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger-Dienst muss ausgeführt werden, damit NET SEND-Ereignisse empfangen werden können.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das-Agent-Dienst Konto erforderlich sind, finden [Sie unter Auswählen eines Kontos für den SQL Server-Agent Dienst](select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienst Konten und-Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-send-sql-server-agent-error-messages"></a>So senden Sie SQL Server-Agent-Fehlermeldungen  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen neben dem Server, der das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokoll enthält, von dem Sie Fehlermeldungen über NET SEND senden möchten.  
  
2.  Klicken Sie mit der rechten Maustaste **SQL Server-Agent** und wählen Sie **Eigenschaften**.  
  
3.  Geben Sie im Dialogfeld **SQL Server-Agent Eigenschaften-**_server_name_ unter **Fehlerprotokoll** auf der Seite **Allgemein** den Benutzernamen oder den Computernamen, an den Sie die Fehlermeldungen senden möchten, in das Feld **NET SEND-Empfänger** ein.  
  
4.  Klicken Sie auf **OK**.  
  
  
