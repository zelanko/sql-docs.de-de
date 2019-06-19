---
title: Eigenschaften des SQL Server-Agents (Registerkarte Auftragssystem)|Microsoft-Dokumente
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a71dda192bebbe84876b2e4fbcb770f5967127c2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089615"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Eigenschaften des SQL Server-Agents (Registerkarte Auftragssystem)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Auf dieser Seite können Sie anzeigen und ändern, wie Aufträge vom [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst verwaltet werden.  
  
## <a name="options"></a>enthalten  
**Timeoutintervall beim Herunterfahren (in Sekunden)**  
Gibt an, wie viele Sekunden der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent vor dem Herunterfahren auf den Abschluss von Aufträgen abwartet. Wenn der Auftrag noch nach dem angegebenen Intervall ausgeführt wird, wird das Beenden des Auftrags vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent erzwungen.  
  
**Nichtadministrator-Proxykonto verwenden**  
Legt ein Nichtadministrator-Proxykonto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent fest. [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] und höhere Versionen unterstützen mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**User name**  
Geben Sie den Namen des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Kennwort**  
Geben Sie das Kennwort des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen unterstützen mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
**Domäne**  
Geben Sie die Domäne des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
  
