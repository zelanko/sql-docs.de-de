---
title: Auftrag des SQL Server-Agents ausführen (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 403abdc5735cdc3336435c1ed3f404a9e4058b6a
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58281334"
---
# <a name="execute-sql-server-agent-job-task"></a>Auftrag des SQL Server-Agents ausführen (Task)
  Mit dem Task Auftrag des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents ausführen werden Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents ausgeführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ist ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Dienst, der in einer Instanz von SQL Server definierte Aufträge ausführt. Sie können Aufträge erstellen, die Transact-SQL-Anweisungen, ActiveX-Skripts, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] - und Replikationswartungstasks sowie Pakete ausführen. Sie können auch einen Auftrag zum Überwachen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zum Auslösen von Warnungen konfigurieren. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentaufträge werden in der Regel zum Automatisieren von Tasks verwendet, die Sie wiederholt ausführen. Weitere Informationen finden Sie unter [Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md).  
  
 Mithilfe des Tasks Auftrag des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents ausführen kann ein Paket administrative Tasks im Zusammenhang mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten ausführen. Beispielsweise kann mit einem Auftrag des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents eine gespeicherte Systemprozedur, wie z.B. **sp_enum_dtspackages** , ausgeführt werden, um eine Liste der Pakete in einem Ordner abzurufen.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Der -Agent muss ausgeführt werden, damit lokale oder Multiserververwaltungsaufgaben automatisch ausgeführt werden können.  
  
 Dieser Task kapselt die Systemprozedur **sp_start_job** und übergibt den Namen des Auftrags des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents als Argument an die Prozedur. Weitere Informationen finden Sie unter [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a>Konfigurieren des Tasks Auftrag des SQL Server-Agents ausführen  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen. Dieser Task ist im **-Designer in der** Toolbox **im Abschnitt** Wartungsplantasks [!INCLUDE[ssIS](../../includes/ssis-md.md)] enthalten.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Task „Auftrag des SQL Server-Agents ausführen“ &#40;Wartungsplan&#41;](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
