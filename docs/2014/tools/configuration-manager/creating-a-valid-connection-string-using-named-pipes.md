---
title: Erstellen einer gültigen Verbindungszeichenfolge mithilfe von Named Pipes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: b5cd4cc03a1b4254e26750b45704d67af62cef04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317440"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a>Erstellen einer gültigen Verbindungszeichenfolge mithilfe von Named Pipes
  Wenn vom Benutzer geändert. wenn die Standardinstanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird lauscht der named Pipes-Protokoll, `\\.\pipe\sql\query` als Pipenamen. Der Punkt gibt an, dass der Computer der lokale Computer ist, `pipe` gibt an, dass die Verbindung eine Named Pipe ist, und `sql\query` ist der Name der Pipe. Zum Herstellen einer Verbindung mit der Standardpipe muss der Alias `\\<computer_name>\pipe\sql\query` als Pipename aufweisen. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Lauschen auf einer anderen Pipe konfiguriert worden ist, muss vom Pipenamen diese Pipe verwendet werden. Wenn beispielsweise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Pipe `\\.\pipe\unit\app` verwendet, muss der Alias als Pipenamen `\\<computer_name>\pipe\unit\app` verwenden.  
  
 Gehen Sie wie folgt vor, um einen gültigen Pipenamen zu erstellen:  
  
-   Geben Sie einen **Aliasnamen**an.  
  
-   Wählen Sie **von Pipes** als die **Protokoll**.  
  
-   Geben Sie die **Pipename**. Alternativ lassen Sie **Pipenamen** leer und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konfigurations-Manager wird den entsprechenden Pipenamen abgeschlossen, nachdem Sie angegeben haben die **Protokoll** und **Server**  
  
-   Geben Sie einen **Server**. Sie können für eine benannte Instanz einen Servernamen und Instanznamen angeben.  
  
 Zum Zeitpunkt der Verbindung die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Komponente liest der Server, das Protokoll und Pipenamen aus der Registrierung für den angegebenen Aliasnamen, und erstellt ein Pipename im Format `np:\\<computer_name>\pipe\<pipename>` oder `np:\\<IPAddress>\pipe\<pipename>`. Für eine benannte Instanz lautet der standardpipename ist `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`.  
  
> [!NOTE]  
>  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Firewall beendet standardmäßig über Port 445. Da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kommuniziert über Port 445, müssen Sie den Port öffnen, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Überprüfen eingehender Clientverbindungen mithilfe von named Pipes konfiguriert ist. Informationen zum Konfigurieren einer Firewall finden Sie unter "Vorgehensweise: Konfigurieren einer Firewall für SQL Server-Zugriff" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation, oder prüfen Sie Ihre Firewalldokumentation.  
  
## <a name="connecting-to-the-local-server"></a>Herstellen einer Verbindung mit dem lokalen Server  
 Beim Herstellen einer Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], das auf dem gleichen Computer wie der Client ausgeführt wird, können Sie `(local)` als Servernamen verwenden. Aus Gründen der Mehrdeutigkeit wird das Verwenden von `(local)` nicht empfohlen, kann aber nützlich sein, wenn vom Client bekannt ist, dass er auf dem vorgesehenen Computer ausgeführt wird. Beim Erstellen einer Anwendung für mobile Benutzer mit getrennter Verbindung (beispielsweise für Verkaufspersonal, wobei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Laptops ausgeführt und zum Speichern von Projektdaten verwendet wird) würde beispielsweise die Verbindung eines Clients zu (local) immer zu dem auf dem Laptop ausgeführten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt. Anstelle von `localhost` kann das Wort `(local)` oder ein Punkt (.) verwendet werden.  
  
## <a name="verifying-your-connection-protocol"></a>Überprüfen des Verbindungsprotokolls  
 Von der folgenden Abfrage wird das Protokoll zurückgegeben, das für die aktuelle Verbindung verwendet wird.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Beispiele  
 Verbindung mit Servernamen zur Standardpipe:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Verbindung mit IP-Adresse zur Standardpipe:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 Verbindung mit Servernamen zu einer Nichtstandardpipe:  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Verbindung mit Servernamen zu einer benannten Instanz:  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Verbindung zum lokalen Computer mithilfe von `localhost`:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 Verbindung zum lokalen Computer mithilfe eines Punkts:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  Angeben des Netzwerkprotokolls als eine **Sqlcmd** Parameter finden Sie unter "Vorgehensweise: Verbinden mit der Datenbank-Engine mithilfe von sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokoll](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
