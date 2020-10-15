---
description: SQL Server-Agent-Eigenschaften (Seite Verbindung)
title: SQL Server-Agent-Eigenschaften (Seite Verbindung)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 22ce45812a5f42c69be9154c7746fff2c8bdae27
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038173"
---
# <a name="sql-server-agent-properties-connection-page"></a>SQL Server-Agent-Eigenschaften (Seite Verbindung)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die Einstellungen für die Verbindung zwischen dem [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzeigen und ändern.  
  
## <a name="options"></a>Optionen  
**Aliasname für den lokalen Hostserver**  
Gibt den Aliasnamen an, der beim Verbinden zur lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Wenn Sie die Standardoptionen der Verbindung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent nicht verwenden können, definieren Sie einen Alias für die Instanz, und geben Sie den Aliasnamen hier an.  
  
**Windows-Authentifizierung verwenden**  
Legt die [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows-Authentifizierung als die Authentifizierungsmethode fest, die für die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwendet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent wird als das Konto verbunden, als das der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird.  
  
**SQL Server-Authentifizierung verwenden**  
Legt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung als die Authentifizierungsmethode fest, die für die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwendet wird.  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung wird aus Gründen der Abwärtskompatibilität bereitgestellt. Aus Sicherheitsgründen sollte möglichst die Windows-Authentifizierung verwendet werden.  
  
**Anmeldung**  
Gibt den Anmeldenamen an, der für die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird.  
  
**Kennwort**  
Gibt das Kennwort an, das für die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird.  
