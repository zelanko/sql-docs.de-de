---
title: Operator benachrichtigen (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2a90017caa4a5c556924756696b61f2686f57ba3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65727532"
---
# <a name="notify-operator-task"></a>Operator benachrichtigen (Task)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Der Task Operator benachrichtigen sendet Benachrichtigungsmeldungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentoperatoren. Bei einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentoperator handelt es sich um einen Alias für eine Person oder Gruppe, die elektronische Benachrichtigungen empfangen kann. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Operatoren finden Sie unter [Operatoren](../../ssms/agent/operators.md).  
  
 Mit dem Task „Operator benachrichtigen“ kann ein Paket mindestens einen Operator per E-Mail, Pager oder **net send**benachrichtigen. Jeder Operator kann mit verschiedenen Methoden benachrichtigt werden. Beispielsweise wird OperatorA per E-Mail und Pager benachrichtigt, OperatorB dagegen per Pager und **net send**. Die Operatoren, die Benachrichtigungen vom Task erhalten, müssen Mitglieder der **OperatorNotify** -Auflistung im Task Operator benachrichtigen sein.  
  
 Der Task "Operator benachrichtigen" ist der einzige Datenbankwartungstask, der keine Transact-SQL-Anweisung und keinen DBCC-Befehl kapselt.  
  
## <a name="configuration-of-the-notify-operator-task"></a>Konfiguration des Tasks "Operator benachrichtigen"  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen. Dieser Task ist im **-Designer in der** Toolbox **im Abschnitt** Wartungsplantasks [!INCLUDE[ssIS](../../includes/ssis-md.md)] enthalten.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Task „Operator benachrichtigen“ &#40;Wartungsplan&#41;](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
