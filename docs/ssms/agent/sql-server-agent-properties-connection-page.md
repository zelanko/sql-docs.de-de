---
title: SQL Server-Agent-Eigenschaften (Seite Verbindung)| Microsoft-Dokumente
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e243186d8c5a5747e73eb2098cae5c5c041134ae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845738"
---
# <a name="sql-server-agent-properties-connection-page"></a>SQL Server-Agent-Eigenschaften (Seite Verbindung)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die Einstellungen für die Verbindung zwischen dem [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
**Aliasname für den lokalen Hostserver**  
Gibt den Aliasnamen an, der beim Verbinden zur lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Wenn Sie die Standardoptionen der Verbindung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent nicht verwenden können, definieren Sie einen Alias für die Instanz, und geben Sie den Aliasnamen hier an.  
  
**Windows-Authentifizierung verwenden**  
Legt die [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows-Authentifizierung als die Authentifizierungsmethode fest, die für die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwendet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent wird als das Konto verbunden, als das der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird.  
  
**SQL Server-Authentifizierung verwenden**  
Legt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung als die Authentifizierungsmethode fest, die für die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwendet wird.  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung wird aus Gründen der Abwärtskompatibilität bereitgestellt. Aus Sicherheitsgründen sollte möglichst die Windows-Authentifizierung verwendet werden.  
  
**Anmeldename**  
Gibt den Anmeldenamen an, der für die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird.  
  
**Kennwort**  
Gibt das Kennwort an, das für die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird.  
  
