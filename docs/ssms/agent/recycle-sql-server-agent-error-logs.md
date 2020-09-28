---
description: Fehlerprotokolle des SQL Server-Agents wiederverwenden
title: Fehlerprotokolle des SQL Server-Agents wiederverwenden
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: df1158dbd8a258a729d8e7a7684106d774e6e345
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492093"
---
# <a name="recycle-sql-server-agent-error-logs"></a>Fehlerprotokolle des SQL Server-Agents wiederverwenden
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Verwenden Sie diese Seite, um die Fehlerprotokolle des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents wiederzuverwenden. Beim Wiederverwenden des Protokolls werden das aktuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokoll geschlossen und ein neues Fehlerprotokoll ohne Neustart des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstes gestartet. Beachten Sie, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die letzten neun Fehlerprotokolle speichert. Wenn bereits neun Fehlerprotokolle vorhanden sind, führt das Wiederverwenden des Fehlerprotokolls dazu, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent das älteste Fehlerprotokoll entfernt.  
  
## <a name="see-also"></a>Weitere Informationen  
[SQL Server-Agent-Fehlerprotokoll](../../ssms/agent/sql-server-agent-error-log.md)  
  
