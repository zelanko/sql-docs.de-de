---
title: SQL Server-Agent Dienst kann SQL Server Authentifizierung nicht verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e16882247a123b32ba07fbbae0d1f3573fd2d678
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092068"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>Die SQL Server-Authentifizierung kann vom SQL Server-Agent-Dienst nicht verwendet werden
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent unterstützt nur die Windows-Authentifizierung, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>Beschreibung  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann sich der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst nur mit der Windows-Authentifizierung bei der Datenbank anmelden. Dies bedeutet, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das-Agent-Dienst Konto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Benutzer sein muss.  
  
 Weitere Informationen finden Sie in den Themen "Sicherheit bei der automatischen Verwaltung" und "Implementieren der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Sicherheit" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Probleme beim Aktualisieren des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
