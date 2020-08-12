---
title: SQL Server-Agent-Fehlerprotokoll
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: eb276434a263085ac839ff09c4e17e17b906c0ab
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729733"
---
# <a name="sql-server-agent-error-log"></a>SQL Server-Agent-Fehlerprotokoll

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent erstellt ein Fehlerprotokoll, in dem standardmäßig Warnungen und Fehler erfasst werden. Die folgenden Warnungen und Fehler werden im Protokoll angezeigt:  
  
-   Warnmeldungen, die Informationen zu möglichen Problemen geben, z. B. „Job \<*job_name*> was deleted while it was running“ (Auftrag „Auftragsname“ wurde beim Ausführen gelöscht).  
  
-   Fehlermeldungen, die in der Regel Eingriff eines Systemadministrators erfordern, z. B. "Mailsitzung kann nicht gestartet werden". Fehlermeldungen können mithilfe von **NET SEND**an bestimmte Benutzer oder Computer gesendet werden.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwaltet bis zu neun [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokolle. Jedes archivierte Fehlerprotokoll verfügt über eine Dateierweiterung, durch die das relative Alter des Protokolls angegeben wird. So gibt z. B. die Erweiterung ".1" das zuletzt archivierte Fehlerprotokoll an, während die Erweiterung ".9" das Fehlerprotokoll kennzeichnet, das zuerst archiviert wurde.  
  
Standardmäßig werden Meldungen zur Ablaufverfolgung nicht in das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokoll geschrieben, da das Protokoll dadurch zu schnell aufgefüllt werden könnte. Wenn das Fehlerprotokoll voll ist, sind Ihre Möglichkeiten zur Auswahl und Analyse schwierigerer Fehler eingeschränkt. Da durch das Protokoll die Verarbeitungsmenge für den Server erhöht wird, sollten Sie genau überlegen, welche Vorteile Ihnen das Aufzeichnen der Meldungen zur Ablaufverfolgung im Fehlerprotokoll bietet. Im Allgemeinen ist es am besten, alle Meldungen nur beim Debuggen eines bestimmten Problems aufzuzeichnen.  
  
Beim Beenden des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents können Sie den Speicherort des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokolls ändern. Leere Fehlerprotokolle können nicht geöffnet werden. Sie können das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Protokoll jederzeit durchlaufen, ohne den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent mit [dbo.sp_cycle_agent_errorlog](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-cycle-agent-errorlog-transact-sql?view=sql-server-2017) anhalten zu müssen.  
  
**So zeigen Sie das SQL Server-Agent-Fehlerprotokoll an**  
  
-   [Fehlerprotokoll des SQL Server-Agents anzeigen &#40;SQL Server Management Studio&#41;](../../ssms/agent/view-sql-server-agent-error-log-sql-server-management-studio.md)  
  
**So benennen Sie ein SQL Server-Agent-Fehlerprotokoll um**  
  
-   [Fehlerprotokoll des SQL Server-Agents umbenennen &#40;SQL Server Management Studio&#41;](../../ssms/agent/rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
**So senden Sie SQL Server-Agent-Fehlermeldungen**  
  
-   [Send SQL Server Agent Error Messages](../../ssms/agent/send-sql-server-agent-error-messages.md)  
  
**So schreiben Sie Meldungen zur Ablaufverfolgung in das SQL Server-Agent-Fehlerprotokoll**  
  
-   [Schreiben von Meldungen zur Ablaufverfolgung in das SQL Server-Agent-Fehlerprotokoll &#40;SQL Server Management Studio&#41;](../../ssms/agent/write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
