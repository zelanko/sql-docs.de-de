---
title: Netzwerk Zugriff auf einen Datenbankspiegelungs-Endpunkt
description: Erfahren Sie, wie Sie den Windows authenticatcher-Netzwerk Zugriff auf einen Datenbankspiegelungs-Endpunkt für SQL Server erlauben.
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e40a1eead54fe9d00eaf099410260023229796d0
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228569"
---
# <a name="allow-network-access-to-a-database-mirroring-endpoint-using-windows-authentication-sql-server"></a>Zulassen des Netzwerkzugriffs auf einen Datenbank-Spiegelungsendpunkt mithilfe der Windows-Authentifizierung (SQL Server)
  Die Verwendung der Windows-Authentifizierung für die Verbindung der Datenbank, wodurch Endpunkte auf zwei Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gespiegelt werden, erfordert unter den folgenden Bedingungen eine manuelle Konfiguration der Anmeldekonten:  
  
-   Wenn die Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als Dienste unter unterschiedlichen Domänenkonten ausgeführt werden (in der gleichen oder einer vertrauenswürdigen Domäne), müssen die Anmeldeinformationen jedes Kontos in **master** auf jeder der Remoteserverinstanzen erstellt werden. Dieser Anmeldung müssen CONNECT-Berechtigungen für den Endpunkt gewährt werden.  
  
-   Wenn die Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als Netzwerkdienstkonto ausgeführt werden, muss die Anmeldung zu jedem Hostcomputer-Konto (*DomainName***\\***ComputerName$*) in **master** auf jeder Remoteserverinstanz erstellt werden. Dieser Anmeldung müssen CONNECT-Berechtigungen für den Endpunkt gewährt werden. Das liegt daran, dass eine Serverinstanz, die unter dem Netzwerkdienstkonto ausgeführt wird, mit dem Domänenkonto des Hostcomputers authentifiziert wird.  
  
> [!NOTE]  
>  Stellen Sie sicher, dass für jede dieser Serverinstanzen ein Endpunkt vorliegt. Weitere Informationen finden Sie unter [Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung &#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).  
  
### <a name="to-configure-logins-for-windows-authentication"></a>So konfigurieren Sie Anmeldenamen für die Windows-Authentifizierung  
  
1.  Erstellen Sie auf den anderen Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]eine Anmeldung für das Benutzerkonto jeder Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Verwenden Sie eine [ CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql)-Anweisung mit der FROM WINDOWS-Klausel.  
  
     Weitere Informationen finden Sie unter [Erstellen eines Anmeldenamens](../relational-databases/security/authentication-access/create-a-login.md).  
  
2.  Erteilen Sie für die Anmeldung die Berechtigung für eine Verbindung zum Endpunkt unter Verwendung der [GRANT](/sql/t-sql/statements/grant-transact-sql) -Anweisung, damit der angemeldete Benutzer auf den Endpunkt zugreifen kann. Wenn es sich beim Benutzer um den Administrator handelt, ist keine Berechtigung für eine Verbindung zum Endpunkt erforderlich.  
  
     Weitere Informationen finden Sie unter [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden [!INCLUDE[tsql](../includes/tsql-md.md)] -Beispiel wird ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldename für ein Benutzerkonto namens `Otheruser` erstellt, das der Domäne `Adomain`angehört. Anschließend erteilt das Beispiel diesem Benutzer die Berechtigungen zum Verbindungsaufbau mit einem bereits vorhandenen Datenbank-Spiegelungsendpunkt mit dem Namen `Mirroring_Endpoint`.  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Daten Bank Spiegelung &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md)   
 [Transport Sicherheit für Daten Bank Spiegelung und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md)   
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
