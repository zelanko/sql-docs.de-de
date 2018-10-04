---
title: Schreiben Sie Meldungen zur Ablaufverfolgung in der SQL Server-Agent-Fehlerprotokoll (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- writing trace messages
- traces [SQL Server], SQL Server Agent logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 90e3731e-6fae-43db-833e-9accecdd1c03
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a58590fe431fa898c617f9d1fd552aa131678b89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217270"
---
# <a name="write-execution-trace-messages-to-the-sql-server-agent-error-log-sql-server-management-studio"></a>Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)
  In diesem Thema wird die Vorgehensweise zum Konfigurieren des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents zum Einschließen von Meldungen zur Ablaufverfolgung in das Fehlerprotokoll in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]beschrieben.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   [So schreiben Sie Meldungen zur Ablaufverfolgung, die SQL Server-Agent-Fehlerprotokoll mithilfe von SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten wird nur im Objekt-Explorer angezeigt, wenn Sie die Berechtigung besitzen, ihn zu verwenden.  
  
-   Schließen Sie Meldungen zur Ablaufverfolgung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokolle ein, wenn Sie ein bestimmtes Problem des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents untersuchen, denn die Option kann dazu führen, dass das Fehlerprotokoll sehr umfangreich wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen, die für die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienstkonto finden Sie unter [Auswählen eines Kontos für den SQL Server-Agent-Dienst](select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienstkonten und Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a>   
#### <a name="to-write-execution-trace-messages-to-the-sql-server-agent-error-log"></a>So schreiben Sie Meldungen zur Ablaufverfolgung in das SQL Server-Agent-Fehlerprotokoll  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen neben dem Server, der das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokoll enthält, in das Sie Meldungen zur Ablaufverfolgung schreiben möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent** , und wählen Sie **Eigenschaften**aus.  
  
3.  Aktivieren Sie im Dialogfeld **SQL Server-Agent-Eigenschaften >***Servername* unter **Fehlerprotokoll** auf der Seite **Allgemein** das Kontrollkästchen **Meldungen zur Ablaufverfolgung einschließen**.  
  
4.  Klicken Sie auf **OK**.  
  
  
