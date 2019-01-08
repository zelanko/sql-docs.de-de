---
title: Fehlerprotokolle des SQL Server-Agents wiederverwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c0654dcc83e757751ac055192775c0ee958f26e9
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52789782"
---
# <a name="recycle-sql-server-agent-error-logs"></a>Fehlerprotokolle des SQL Server-Agents wiederverwenden
  Mithilfe dieser Seite können Sie die Fehlerprotokolle des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents wiederverwenden. Beim Wiederverwenden des Protokolls werden das aktuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokoll geschlossen und ein neues Fehlerprotokoll ohne Neustart des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstes gestartet. Beachten Sie, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die letzten neun Fehlerprotokolle speichert. Wenn bereits neun Fehlerprotokolle vorhanden sind, führt das Wiederverwenden des Fehlerprotokolls dazu, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent das älteste Fehlerprotokoll entfernt.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-Fehlerprotokoll](sql-server-agent-error-log.md)  
  
  
