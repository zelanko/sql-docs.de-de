---
title: MSSQL_ENG024070 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 31421597871bfef0c02a15ce83bf486ea9cc6646
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048420"
---
# <a name="mssqleng024070"></a>MSSQL_ENG024070
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|24070|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Dem Client fehlt ein erforderliches Privileg.|  
  
## <a name="explanation"></a>Erklärung  
 Es handelt sich um einen allgemeinen Fehler, der unabhängig von der Verwendung der Replikation ausgelöst werden kann. Auf einem Server in einer Replikationstopologie tritt der Fehler im Allgemeinen auf, weil das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienstkonto mithilfe des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Dienstkontroll-Managers anstelle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers geändert wurde. Wenn Sie versuchen, nach der Änderung des Dienstkontos einen Agentauftrag auszuführen, erzeugt dieser Auftrag möglicherweise einen Fehler, und es wird eine Fehlermeldung wie die folgende angezeigt:  
  
 "Ausgeführt als Benutzer: \<UserAccount >. Replikationsmomentaufnahme-Subsystem des Replikation-Replikation: Agent \<AgentName > Fehler. Ausgeführt als Benutzer: \<UserAccount >. Dem Client fehlt ein erforderliches Privileg. Fehler bei Schritt. `[SQLSTATE 42000] (Error 14151)`. installiert haben. Fehler bei Schritt."  
  
 Dieses Problem tritt auf, weil der Windows-Dienstkontroll-Manager dem neuen Dienstkonto nicht die erforderlichen Berechtigungen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zuweisen kann.  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie zum Ändern von Dienstkonten und Kennwörtern immer den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager anstelle des Windows-Dienstkontroll-Managers, um dieses Problem in Zukunft zu vermeiden.  
  
 Ändern Sie das Dienstkonto mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers zurück in das ursprüngliche Konto, um das Problem zu beheben. Verwenden Sie anschließend den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, um das Dienstkonto in das neue Konto zu ändern. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager fügt das neue Konto dann der folgenden Sicherheitsgruppe hinzu:  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 Als Mitglied dieser Sicherheitsgruppe verfügt das neue Konto über die erforderlichen Berechtigungen, um den Auftrag des Replikations-Agents auszuführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)   
 [Verwalten von Anmeldeinformationen und Kennwörtern bei der Replikation](security/manage-logins-and-passwords-in-replication.md)   
 [SQL Server-Konfigurations-Manager](../sql-server-configuration-manager.md)  
  
  
