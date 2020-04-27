---
title: SQL Server-Agent-Eigenschaften (Seite Verbindung)| Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0c387513b8896018ead7d35e15a32e9e314ac0d3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245729"
---
# <a name="sql-server-agent-properties-connection-page"></a>SQL Server-Agent-Eigenschaften (Seite Verbindung)
  Verwenden Sie diese Seite, um die Einstellungen für die Verbindung zwischen dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]und anzuzeigen und zu ändern.  
  
## <a name="options"></a>Optionen  
 **Aliasname für den lokalen Hostserver**  
 Gibt den Aliasnamen an, der beim Verbinden zur lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Wenn Sie die Standardoptionen der Verbindung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent nicht verwenden können, definieren Sie einen Alias für die Instanz, und geben Sie den Aliasnamen hier an.  
  
 **Windows-Authentifizierung verwenden**  
 Legt die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung als die Authentifizierungsmethode fest, die für die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwendet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent wird als das Konto verbunden, als das der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird.  
  
 **SQL Server Authentifizierung verwenden**  
 Legt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung als die Authentifizierungsmethode fest, die für die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwendet wird.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung wird aus Gründen der Abwärtskompatibilität bereitgestellt. Aus Sicherheitsgründen sollte möglichst die Windows-Authentifizierung verwendet werden.  
  
 **Anmeldung**  
 Gibt den Anmeldenamen an, der für die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird.  
  
 **Kennwort**  
 Gibt das Kennwort an, das für die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird.  
  
  
