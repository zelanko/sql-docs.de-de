---
title: Starten von SQL Server mit Minimalkonfiguration | Microsoft-Dokumentation
description: Hier lernen Sie die Startoption mit Minimalkonfiguration in SQL Server kennen. Außerdem erfahren Sie, wann und wie Sie die Option verwenden sowie inwiefern die Funktionalität durch diese Option beeinträchtigt wird.
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1ae9ee2f231367ebf577f0c5c70e5e64ce32d6cc
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670763"
---
# <a name="start-sql-server-with-minimal-configuration"></a>Starten Sie von SQL Server mit Minimalkonfiguration
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Wenn Konfigurationsprobleme auftreten, die das Starten des Servers verhindern, können Sie eine Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der Startoption für die Minimalkonfiguration starten. Dies ist die Startoption **-f**. Durch das Starten einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit Minimalkonfiguration wird der Server automatisch in den Einzelbenutzermodus versetzt.  
  
 Beachten Sie Folgendes, wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Modus der Minimalkonfiguration starten:  
  
-   Nur ein einziger Benutzer kann eine Verbindung herstellen, und der `CHECKPOINT`-Prozess wird nicht ausgeführt.  
  
-   Der Remotezugriff und das Read-Ahead werden deaktiviert.  
  
-   Für den Startvorgang vorgesehene gespeicherte Prozeduren werden nicht ausgeführt.  

-   `tempdb` wird auf die kleinstmögliche Größe konfiguriert.

-   Die Überwachung wird deaktiviert, aber die Überwachungs-DDL kann weiterhin ausgegeben werden. In der Praxis sollte **-m** in den meisten Fällen ausreichen, die eine Neukonfiguration der SQL Server-Überwachung erfordern. Weitere Informationen über die Sicherheit der Überwachungskonfiguration finden Sie unter [Überwachung in SQL Server](/previous-versions/sql/sql-server-2008/dd392015(v=sql.100)#security).
  
 Nach dem Starten des Servers mit Minimalkonfiguration sollten Sie den oder die entsprechenden Optionswert(e) des Servers ändern, den Server dann beenden und neu starten.  
  
> [!IMPORTANT]  
>  Stellen Sie mithilfe des **sqlcmd** -Hilfsprogramms und der dedizierten Administratorverbindung (Dedicated Administrator Connection; DAC) eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her. Wenn Sie eine typische Verbindung verwenden, sollten Sie den SQL Server-Agent-Dienst beenden, bevor Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Modus der Minimalkonfiguration herstellen. Andernfalls verwendet der SQL Server-Agent-Dienst die Verbindung und blockiert sie dadurch.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Diagnoseverbindung für Datenbankadministratoren](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)   
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Startoptionen für den Datenbank-Engine-Dienst](../../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
