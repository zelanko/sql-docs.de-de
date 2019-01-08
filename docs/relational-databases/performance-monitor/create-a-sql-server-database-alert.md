---
title: Erstellen einer SQL Server-Datenbankwarnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: fd07a79e9ebfd562c0d9ca61ebaa14581d55af10
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53379501"
---
# <a name="create-a-sql-server-database-alert"></a>Erstellen einer SQL Server-Datenbankwarnung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Sie können mithilfe des Systemmonitors eine Warnung erstellen, die ausgelöst wird, sobald ein Schwellenwert für einen Leistungsindikator des Systemmonitors erreicht wird. Als Reaktion auf die Warnung startet der Systemmonitor eine Anwendung, z. B. eine für die Verarbeitung der Warnung geschriebene benutzerdefinierte Anwendung. Sie könnten beispielsweise eine Warnung erstellen, die ausgelöst wird, wenn die Anzahl der Deadlocks einen bestimmten Wert überschreitet.  
  
 Sie können Warnungen auch mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents erstellen. Weitere Informationen finden Sie unter [Warnungen](../../ssms/agent/alerts.md).  
  
 Weitere Informationen zum Verwenden des Systemmonitors zum Einrichten einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbankwarnung finden Sie unter [Einrichten einer SQL Server-Datenbankwarnung &#40;Windows&#41;](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  
