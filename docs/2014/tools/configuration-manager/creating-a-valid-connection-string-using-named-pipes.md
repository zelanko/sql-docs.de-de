---
title: Erstellen einer gültigen Verbindungs Zeichenfolge mithilfe von Named Pipes | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine gültige Verbindungs Zeichenfolge erstellen, wenn Sie mit dem Named Pipes-Protokoll eine Verbindung mit einer Instanz von SQL Server herstellen. Anzeigen von Beispielen gültiger Pipenamen.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 65fcebc3bbe12061e699106fb23eed15a5498414
ms.sourcegitcommit: c8e45e0fdab8ea2ae1c7e709346354576b18ca1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716707"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a>Erstellen einer gültigen Verbindungszeichenfolge mithilfe von Named Pipes
  Wenn die Standard Instanz von das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Named Pipes-Protokoll überwacht, wird Sie als Pipename verwendet, es sei denn, Sie wird vom Benutzer geändert `\\.\pipe\sql\query` . Der Punkt gibt an, dass der Computer der lokale Computer ist, `pipe` gibt an, dass die Verbindung eine Named Pipe ist, und `sql\query` ist der Name der Pipe. Zum Herstellen einer Verbindung mit der Standardpipe muss der Alias `\\<computer_name>\pipe\sql\query` als Pipename aufweisen. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Lauschen auf einer anderen Pipe konfiguriert worden ist, muss vom Pipenamen diese Pipe verwendet werden. Wenn beispielsweise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Pipe `\\.\pipe\unit\app` verwendet, muss der Alias als Pipenamen `\\<computer_name>\pipe\unit\app` verwenden.  
  
 Gehen Sie wie folgt vor, um einen gültigen Pipenamen zu erstellen:  
  
-   Geben Sie einen **Aliasnamen**an.  
  
-   Wählen Sie **Named Pipes** als **Protokoll**aus.  
  
-   Geben Sie den **Pipenamen**ein. Alternativ können Sie den **Pipenamen** leer lassen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager den entsprechenden Pipenamen nach der Angabe des **Protokolls** und **Servers** vervollständigen.  
  
-   Geben Sie einen **Server**an. Sie können für eine benannte Instanz einen Servernamen und Instanznamen angeben.  
  
 Zum Zeitpunkt der Verbindungs Herstellung werden von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Komponente die Werte für den Server, das Protokoll und den Pipenamen aus der Registrierung für den angegebenen Aliasnamen gelesen und ein Pipename im Format `np:\\<computer_name>\pipe\<pipename>` oder erstellt `np:\\<IPAddress>\pipe\<pipename>` . Für eine benannte Instanz lautet der standardpipename `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query` .  
  
> [!NOTE]  
>  Der Port 445 wird von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Firewall standardmäßig geschlossen. Da [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über den Port 445 kommuniziert, müssen Sie diesen Port erneut öffnen, falls [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Lauschen auf eingehende Clientverbindungen mithilfe von Named Pipes konfiguriert wurde. Informationen zum Konfigurieren einer Firewall finden Sie unter "Vorgehensweise: Konfigurieren einer Firewall für SQL Server-Zugriff" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation, oder prüfen Sie Ihre Firewalldokumentation.  
  
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
>  Informationen zum Angeben des Netzwerk Protokolls als **sqlcmd** -Parameter finden Sie unter "Vorgehensweise: Herstellen einer Verbindung mit dem Datenbank-Engine mithilfe sqlcmd.exe" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer gültigen Verbindungs Zeichenfolge mithilfe des Shared Memory-Protokolls](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Erstellen einer gültigen Verbindungs Zeichenfolge mithilfe von TCP-IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
