---
title: Starten von SQL Server mit Minimalkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b1bdbf5d0c4de58e1d447e27f12261ef0ed054c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="start-sql-server-with-minimal-configuration"></a>Starten Sie von SQL Server mit Minimalkonfiguration
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Wenn Konfigurationsprobleme auftreten, die das Starten des Servers verhindern, können Sie eine Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der Startoption für die Minimalkonfiguration starten. Dies ist die Startoption **-f**. Durch das Starten einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit Minimalkonfiguration wird der Server automatisch in den Einzelbenutzermodus versetzt.  
  
 Beachten Sie Folgendes, wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Modus der Minimalkonfiguration starten:  
  
-   Nur ein einziger Benutzer kann eine Verbindung herstellen, und der `CHECKPOINT`-Prozess wird nicht ausgeführt.  
  
-   Der Remotezugriff und das Read-Ahead werden deaktiviert.  
  
-   Für den Startvorgang vorgesehene gespeicherte Prozeduren werden nicht ausgeführt.  

-   `tempdb` wird auf die kleinstmögliche Größe konfiguriert.
  
 Nach dem Starten des Servers mit Minimalkonfiguration sollten Sie den oder die entsprechenden Optionswert(e) des Servers ändern, den Server dann beenden und neu starten.  
  
> [!IMPORTANT]  
>  Stellen Sie mithilfe des **sqlcmd** -Hilfsprogramms und der dedizierten Administratorverbindung (Dedicated Administrator Connection; DAC) eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her. Wenn Sie eine typische Verbindung verwenden, sollten Sie den SQL Server-Agent-Dienst beenden, bevor Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Modus der Minimalkonfiguration herstellen. Andernfalls verwendet der SQL Server-Agent-Dienst die Verbindung und blockiert sie dadurch.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)   
 [Diagnoseverbindung für Datenbankadministratoren](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)   
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 
  [Startoptionen für den Datenbank-Engine-Dienst](../../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
  
