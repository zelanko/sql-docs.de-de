---
title: SQL Server-Agent-Dienst können keine SQL Server-Authentifizierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0d9badd521bf9bdccd5c141e28956f5b19f6275d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119720"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>Die SQL Server-Authentifizierung kann vom SQL Server-Agent-Dienst nicht verwendet werden
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent unterstützt nur die Windows-Authentifizierung, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann sich der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst nur mit der Windows-Authentifizierung bei der Datenbank anmelden. Dies bedeutet, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstkonto muss ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benutzer.  
  
 Weitere Informationen finden Sie in den Themen "Sicherheit bei der automatischen Verwaltung" und "Implementieren der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Sicherheit" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Probleme beim Upgrade des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
