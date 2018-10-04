---
title: Anzeigen oder Konfigurieren von Verbindungsoptionen für Remoteserver (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f65188b6f322d3ee65d3182d135cec367142f4ec
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062900"
---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a>Anzeigen oder Konfigurieren von Verbindungsoptionen für Remoteserver (SQL Server)
  In diesem Thema wird beschrieben, wie Sie Verbindungsoptionen für Remoteserver auf Serverebene in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]anzeigen oder konfigurieren können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So zeigen Sie Verbindungsoptionen für Remoteserver an oder konfigurieren sie mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren von Verbindungsoptionen für Remoteserver](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Für das Ausführen von **sp_serveroption** sind ALTER ANY LINKED SERVER-Berechtigungen auf dem Server erforderlich.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a>So zeigen Sie Verbindungsoptionen für Remoteserver an oder konfigurieren sie  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **SQL Server-Eigenschaften > \<***Servername***>** auf **Verbindungen**.  
  
3.  Überprüfen Sie auf der Seite **Verbindungen** die Einstellungen für **Remoteserververbindungen** , und ändern Sie sie gegebenenfalls.  
  
4.  Wiederholen Sie Schritt 1 bis 3 auf dem zweiten Server des Remoteserverpaares.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-remote-server-connection-options"></a>So zeigen Sie Verbindungsoptionen für Remoteserver an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel werden von [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) Informationen über alle Remoteserver zurückgegeben.  
  
```tsql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a>So konfigurieren Sie Verbindungsoptionen für Remoteserver  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) zum Konfigurieren eines Remoteservers verwendet wird. In diesem Beispiel wird ein Remoteserver, der einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz ( `SEATTLE3`) entspricht, so konfiguriert, dass seine Sortierung mit der Sortierung der lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz kompatibel ist.  
  
```tsql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="FollowUp"></a> Nachverfolgung: Nach dem Konfigurieren von Verbindungsoptionen für Remoteserver  
 Der Remoteserver muss angehalten und neu gestartet werden, damit die Einstellung wirksam werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Remoteserver](remote-servers.md)   
 [Verbindungsserver &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [sp_linkedservers (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql)   
 [sp_helpserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql)   
 [sp_serveroption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
