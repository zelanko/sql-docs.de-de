---
title: Service Broker mit AlwaysOn-Verfügbarkeitsgruppen (SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 881c20e5-1c99-44eb-b393-09fc5ea0f122
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fdf98d461039c5c6fb4f25c8cdf543422e5a0a2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62788530"
---
# <a name="service-broker-with-alwayson-availability-groups-sql-server"></a>Service Broker mit AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  Dieses Thema enthält Informationen, wie Sie Service Broker in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] zur Verwendung mit [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]konfigurieren.  
  
 **In diesem Thema:**  
  
-   [Anforderungen, damit ein Dienst in einer Verfügbarkeitsgruppe Remotenachrichten empfangen kann](#ReceiveRemoteMessages)  
  
-   [Anforderungen zum Senden von Nachrichten an einen Remotedienst in einer Verfügbarkeitsgruppe](#SendRemoteMessages)  
  
##  <a name="ReceiveRemoteMessages"></a> Anforderungen, damit ein Dienst in einer Verfügbarkeitsgruppe Remotenachrichten empfangen kann  
  
1.  **Stellen Sie sicher, dass die Verfügbarkeitsgruppe über einen Listener verfügt.**  
  
     Weitere Informationen finden Sie unter [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)aktiviert sind, eine Always On-Verfügbarkeitsgruppe zu erstellen.  
  
2.  **Stellen Sie sicher, dass der Service Broker-Endpunkt vorhanden ist und ordnungsgemäß konfiguriert wird.**  
  
     Konfigurieren Sie für jede [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz, von der ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe gehostet wird, den Service Broker-Endpunkt wie folgt:  
  
    -   Legen Sie LISTENER_IP auf 'ALL' fest. Durch diese Einstellung werden Verbindungen für eine beliebige gültige IP-Adresse aktiviert, die an den Verfügbarkeitsgruppenlistener gebunden ist.  
  
    -   Legen Sie den Service Broker-PORT auf allen Hostserverinstanzen auf die gleiche Portnummer fest.  
  
        > [!TIP]  
        >  Um die Portnummer des Service Broker-Endpunkts für eine bestimmte Serverinstanz anzuzeigen, fragen Sie die **port** -Spalte der [sys.tcp_endpoint](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) s-Katalogsicht ab, in der **type_desc** = 'SERVICE_BROKER' ist.  
  
     Im folgenden Beispiel wird ein von Windows authentifizierter Service Broker-Endpunkt erstellt, der den Service Broker-Standardport (4022) verwendet und auf alle gültigen IP-Adressen lauscht.  
  
    ```  
    CREATE ENDPOINT [SSBEndpoint]  
        STATE = STARTED  
        AS TCP  (LISTENER_PORT = 4022, LISTENER_IP = ALL )  
        FOR SERVICE_BROKER (AUTHENTICATION = WINDOWS)  
    ```  
  
     Weitere Informationen finden Sie unter [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)konfigurieren.  
  
3.  **Erteilen Sie die CONNECT-Berechtigung für den Endpunkt.**  
  
     Erteilen Sie PUBLIC oder einem Anmeldenamen die CONNECT-Berechtigung für den Service Broker-Endpunkt.  
  
     Im folgenden Beispiel wird PUBLIC die Verbindungsberechtigung für einen Service Broker-Endpunkt mit dem Namen `broker_endpoint` erteilt.  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[broker_endpoint] TO [PUBLIC]  
    ```  
  
     Weitere Informationen finden Sie unter [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)konfigurieren.  
  
4.  **Stellen Sie sicher, dass in „msdb“ entweder eine AutoCreatedLocal-Route oder eine Route zum angegebenen Dienst enthalten ist.**  
  
    > [!NOTE]  
    >  Standardmäßig enthält jede Benutzerdatenbank einschließlich **msdb**die Route **AutoCreatedLocal**. Diese Route stimmt mit beliebigen Dienstnamen und Brokerinstanzen überein und gibt an, dass die Nachricht innerhalb der aktuellen Instanz übermittelt werden muss. **AutoCreatedLocal** hat eine niedrigere Priorität als Routen, in denen explizit ein bestimmter Dienst angegeben ist, der mit einer Remoteinstanz kommuniziert.  
  
     Weitere Informationen zum Erstellen von Routen finden Sie unter [Service Broker-Routingbeispiele](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) (in der [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] -Version der Onlinedokumentation) und [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)konfigurieren.  
  
##  <a name="SendRemoteMessages"></a> Anforderungen zum Senden von Nachrichten an einen Remotedienst in einer Verfügbarkeitsgruppe  
  
1.  **Erstellen Sie eine Route zum Zieldienst.**  
  
     Konfigurieren Sie die Route wie folgt:  
  
    -   Legen Sie ADDRESS auf die IP-Adresse des Listeners der Verfügbarkeitsgruppe fest, von der die Dienstdatenbank gehostet wird.  
  
    -   Legen Sie PORT auf den Port fest, den Sie im Service Broker-Endpunkt jeder SQL Server-Remoteinstanz angegeben haben.  
  
     Im folgenden Beispiel wird eine Route mit dem Namen `RouteToTargetService` für den `ISBNLookupRequestService` -Dienst erstellt. Die Route hat den Verfügbarkeitsgruppenlistener `MyAgListener`zum Ziel, der den Port 4022 verwendet.  
  
    ```  
    CREATE ROUTE [RouteToTargetService] WITH   
    SERVICE_NAME = 'ISBNLookupRequestService',   
    ADDRESS = 'TCP://MyAgListener:4022';  
  
    ```  
  
     Weitere Informationen finden Sie unter [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)konfigurieren.  
  
2.  **Stellen Sie sicher, dass in „msdb“ entweder eine AutoCreatedLocal-Route oder eine Route zum angegebenen Dienst enthalten ist.** (Weitere Informationen finden Sie unter [Anforderungen, damit ein Dienst in einer Verfügbarkeitsgruppe Remotenachrichten empfangen kann](#ReceiveRemoteMessages)weiter oben in diesem Thema.)  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
-   [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)  
  
-   [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Erstellung und Konfiguration von Verfügbarkeitsgruppen &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Einrichten von Anmeldekonten für die Datenbankspiegelung oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [SQL Server Service Broker](../../configure-windows/sql-server-service-broker.md)  
  
  
