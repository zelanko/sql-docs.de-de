---
title: MSSQL_ENG024070 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2f5fc8fdc9b522ad79e67a7769ba2571b7a80af9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63023913"
---
# <a name="mssql_eng024070"></a>MSSQL_ENG024070
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|24070|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Dem Client fehlt ein erforderliches Privileg.|  
  
## <a name="explanation"></a>Erklärung  
 Es handelt sich um einen allgemeinen Fehler, der unabhängig von der Verwendung der Replikation ausgelöst werden kann. Auf einem Server in einer Replikationstopologie tritt der Fehler im Allgemeinen auf, weil das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienstkonto mithilfe des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Dienstkontroll-Managers anstelle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers geändert wurde. Wenn Sie versuchen, nach der Änderung des Dienstkontos einen Agentauftrag auszuführen, erzeugt dieser Auftrag möglicherweise einen Fehler, und es wird eine Fehlermeldung wie die folgende angezeigt:  
  
 "Ausgeführt als Benutzer: \<Useraccount>. Replikations Momentaufnahme-Subsystem \<der Replikation: Fehler des agentagentnamens>. Ausgeführt als Benutzer: \<Useraccount>. Dem Client fehlt ein erforderliches Privileg. Fehler bei Schritt. `[SQLSTATE 42000] (Error 14151)`. Fehler bei Schritt."  
  
 Dieses Problem tritt auf, weil der Windows-Dienstkontroll-Manager dem neuen Dienstkonto nicht die erforderlichen Berechtigungen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zuweisen kann.  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie zum Ändern von Dienstkonten und Kennwörtern immer den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager anstelle des Windows-Dienstkontroll-Managers, um dieses Problem in Zukunft zu vermeiden.  
  
 Ändern Sie das Dienstkonto mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers zurück in das ursprüngliche Konto, um das Problem zu beheben. Verwenden Sie anschließend den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, um das Dienstkonto in das neue Konto zu ändern. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager fügt das neue Konto dann der folgenden Sicherheitsgruppe hinzu:  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 Als Mitglied dieser Sicherheitsgruppe verfügt das neue Konto über die erforderlichen Berechtigungen, um den Auftrag des Replikations-Agents auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Ereignis Referenz &#40;Replikations&#41;](errors-and-events-reference-replication.md)   
 [Verwalten von Anmeldungen und Kenn Wörtern in der Replikation](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [SQL Server-Konfigurations-Manager](../sql-server-configuration-manager.md)  
  
  
