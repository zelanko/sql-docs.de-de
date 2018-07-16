---
title: Remoteadministratorverbindungen (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a0a79abea84914ca0c4ffef487e8f7e1bc0a7e96
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302720"
---
# <a name="remote-admin-connections-server-configuration-option"></a>Remoteadministratorverbindungen (Serverkonfigurationsoption)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt eine dedizierte Administratorverbindung (Dedicated Administrator Connection, DAC) zur Verfügung. Mit der DAC kann ein Administrator auf einen laufenden Server zugreifen, um Diagnosefunktionen oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen auszuführen oder um Probleme auf dem Server zu behandeln, selbst wenn der Server gesperrt ist oder nicht in einem normalen Status ausgeführt wird und nicht auf eine [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Verbindung antwortet. Standardmäßig ist die DAC nur von einem Client auf dem Server verfügbar. Verwenden Sie die Option remote admin connections von sp_configure, um zuzulassen, dass Clientanwendungen auf Remotecomputern die DAC verwenden.  
  
 Standardmäßig lauscht die DAC nur an der Loopback-IP-Adresse (127.0.0.1), Port 1434. Ist der TCP-Port 1434 nicht verfügbar, wird ein TCP-Port dynamisch zugewiesen, wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] startet. Wenn mehr als eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Computer installiert ist, müssen Sie das Fehlerprotokoll auf die TCP-Portnummer überprüfen.  
  
 In der folgenden Tabelle sind die möglichen Werte für die Option remote admin connections aufgeführt.  
  
|value|Description|  
|-----------|-----------------|  
|0|Nur lokale Verbindungen sind mit der DAC zulässig.|  
|1|Remoteverbindungen sind mit der DAC zulässig.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die DAC von einem Remotecomputer aus aktiviert.  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Diagnoseverbindung für Datenbankadministratoren](diagnostic-connection-for-database-administrators.md)  
  
  
