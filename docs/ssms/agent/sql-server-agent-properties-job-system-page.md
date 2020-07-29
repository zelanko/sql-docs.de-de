---
title: Eigenschaften des SQL Server-Agents (Registerkarte Auftragssystem)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a0e33eb0b4999c608f2083d3023f046a2ecc640a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755123"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Eigenschaften des SQL Server-Agents (Registerkarte Auftragssystem)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Auf dieser Seite können Sie anzeigen und anpassen, wie der [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst Aufträge verwaltet.  
  
## <a name="options"></a>Tastatur  
**Timeoutintervall beim Herunterfahren (in Sekunden)**  
Gibt an, wie viele Sekunden der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent vor dem Herunterfahren auf den Abschluss von Aufträgen abwartet. Wenn der Auftrag noch nach dem angegebenen Intervall ausgeführt wird, wird das Beenden des Auftrags vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent erzwungen.  
  
**Nichtadministrator-Proxykonto verwenden**  
Legt ein Nichtadministrator-Proxykonto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent fest. [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] und höhere Versionen unterstützen mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Benutzername**  
Geben Sie den Namen des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Kennwort**  
Geben Sie das Kennwort des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen unterstützen mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
**Domäne**  
Geben Sie die Domäne des Benutzers für das Nichtadministrator-Proxykonto ein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt mehrere Proxys. Diese Option betrifft daher nur die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
  
