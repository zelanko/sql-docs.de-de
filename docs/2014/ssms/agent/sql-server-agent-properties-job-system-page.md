---
title: Eigenschaften des SQL Server-Agents (Registerkarte Auftragssystem)|Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: c9b7f5064270e8e648b5b24b24745aa5a7c11120
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058677"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Eigenschaften des SQL Server-Agents (Registerkarte Auftragssystem)
  Mithilfe dieser Seite können Sie anzeigen und ändern, wie Aufträge vom- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienst verwaltet werden.  
  
## <a name="options"></a>Optionen  
 **Timeoutintervall beim Herunterfahren (in Sekunden)**  
 Gibt an, wie viele Sekunden der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent vor dem Herunterfahren auf den Abschluss von Aufträgen abwartet. Wenn der Auftrag noch nach dem angegebenen Intervall ausgeführt wird, wird das Beenden des Auftrags vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent erzwungen.  
  
 **Nichtadministrator-Proxykonto verwenden**  
 Legt ein Nichtadministrator-Proxykonto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent fest. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]und höhere Versionen unterstützen mehrere Proxys. Daher ist diese Option nur bei der Verwaltung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von verfügbar. Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .  
  
 **Benutzername**  
 Geben Sie den Namen des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 **Kennwort**  
 Geben Sie das Kennwort des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen unterstützen mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 **Domäne**  
 Geben Sie die Domäne des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Aufträgen](implement-jobs.md)  
  
  
