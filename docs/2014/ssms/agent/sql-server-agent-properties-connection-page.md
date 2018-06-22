---
title: SQL Server-Agent-Eigenschaften (Seite Verbindung)| Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 48f107d115960c879a8f2818b62215c6a1c316b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059056"
---
# <a name="sql-server-agent-properties-connection-page"></a>SQL Server-Agent-Eigenschaften (Seite Verbindung)
  Mithilfe dieser Seite können Sie die Einstellungen für die Verbindung zwischen dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
 **Aliasname für den lokalen Hostserver**  
 Gibt den Aliasnamen an, der beim Verbinden zur lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Wenn Sie die Standardoptionen der Verbindung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent nicht verwenden können, definieren Sie einen Alias für die Instanz, und geben Sie den Aliasnamen hier an.  
  
 **Windows-Authentifizierung verwenden**  
 Legt die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung als die Authentifizierungsmethode fest, die für die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwendet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent wird als das Konto verbunden, als das der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird.  
  
 **SQL Server-Authentifizierung verwenden**  
 Legt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung als die Authentifizierungsmethode fest, die für die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwendet wird.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung wird aus Gründen der Abwärtskompatibilität bereitgestellt. Aus Sicherheitsgründen sollte möglichst die Windows-Authentifizierung verwendet werden.  
  
 **Anmeldename**  
 Gibt den Anmeldenamen an, der für die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird.  
  
 **Kennwort**  
 Gibt das Kennwort an, das für die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird.  
  
  