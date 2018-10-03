---
title: Agent XPs (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 04599812bb411e634174832d564ae851316b1507
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048380"
---
# <a name="agent-xps-server-configuration-option"></a>Agent XPs (Serverkonfigurationsoption)
  Mithilfe der Option **Agent XPs** können Sie die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents auf diesem Server aktivieren. Wenn diese Option nicht aktiviert ist, ist der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nicht verfügbar.  
  
 Wenn Sie den [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Agent-Dienst mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tools starten, werden diese erweiterten gespeicherten Prozeduren automatisch aktiviert. Weitere Informationen finden Sie unter [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Wenn diese erweiterten gespeicherten Prozeduren nicht aktiviert sind, wird der Inhalt des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Knotens im Objekt-Explorer von Management Studio, unabhängig vom Status des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Diensts, nicht angezeigt.  
  
 Die folgenden Werte sind möglich:  
  
-   **0**gibt an, dass die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents nicht verfügbar sind (Standardeinstellung).  
  
-   **1**gibt an, dass die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verfügbar sind.  
  
 Die Einstellung tritt ohne Beenden und Neustarten des Servers sofort in Kraft.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents aktiviert.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisierte Administrationstasks &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md)   
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
