---
title: Auswählen eines Netzwerkprotokolls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
- Named Pipes [SQL Server]
- TCP [SQL Server]
- network protocols [SQL Server], choosing
- protocols [SQL Server], choosing
- NWLink IPX/SPX [SQL Server]
- client configuration [SQL Server], protocols
- VIA
- Multiprotocol Net-Library [SQL Server]
- IPX/SPX [SQL Server]
- Banyan VINES
- protocols [SQL Server], client configuration
ms.assetid: 6565fb7d-b076-4447-be90-e10d0dec359a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 9c167994c7145bce348b6959a57533e398e1d6bb
ms.sourcegitcommit: ca9b5cb6bccfdba4cdbe1697adf5c673b4713d6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "56407550"
---
# <a name="choosing-a-network-protocol"></a>Auswählen eines Netzwerkprotokolls
  Um eine Verbindung mit [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] herzustellen, müssen Sie ein aktiviertes Netzwerkprotokoll haben. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann Anforderungen für mehrere Protokolle gleichzeitig bedienen. Clients stellen eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über ein einzelnes Protokoll her. Wenn dem Clientprogramm nicht bekannt ist, auf welches Protokoll von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gelauscht wird, konfigurieren Sie den Client so, dass er nacheinander das Verwenden mehrerer Protokolle versucht. Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, um Netzwerkprotokolle zu aktivieren, zu deaktivieren oder zu konfigurieren.  
  
## <a name="shared-memory"></a>Shared Memory  
 Shared Memory ist das am einfachsten zu verwendende Protokoll. Es weist keine konfigurierbaren Einstellungen auf. Da Clients, die das Shared Memory-Protokoll verwenden, nur eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen können, die auf demselben Computer ausgeführt wird, ist dieses Protokoll bei den meisten Datenbankaktivitäten nicht hilfreich. Verwenden Sie das Shared Memory-Protokoll zur Problembehandlung, wenn Sie vermuten, dass die anderen Protokolle nicht ordnungsgemäß konfiguriert sind.  
  
> [!NOTE]  
>  Clients mit MDAC 2.8 oder früher können das Shared Memory-Protokoll nicht verwenden. Beim Versuch, das Protokoll aufzurufen, wird automatisch auf das Named Pipes-Protokoll umgeschaltet.  
  
## <a name="tcpip"></a>TCP/IP  
 TCP/IP ist ein Protokoll, das im Internet häufig verwendet wird. Es kommuniziert über untereinander verbundene Computernetzwerke mit unterschiedlichen Hardwarearchitekturen und verschiedenen Betriebssystemen. TCP/IP schließt Standards zum Weiterleiten von Netzwerkverkehr ein und bietet erweiterte Sicherheitsfunktionen. Es ist das heute in der Geschäftswelt am häufigsten verwendete Protokoll. Das Konfigurieren des Computers für die Verwendung von TCP/IP kann ein komplexer Vorgang sein, allerdings sind die meisten Netzwerkcomputer bereits ordnungsgemäß konfiguriert. Weitere Informationen zum Konfigurieren der TCP/IP-Einstellungen, die nicht im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager verfügbar sind, finden Sie in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Dokumentation.  
  
## <a name="named-pipes"></a>Named Pipes  
 Named Pipes ist ein Protokoll, das für lokale Netzwerke entwickelt wurde. Ein Teil des Arbeitsspeichers wird von einem Vorgang zum Weiterleiten von Informationen an einen anderen Vorgang verwendet, sodass die Ausgabe des einen Vorgangs der Eingabe des anderen entspricht. Der zweite Prozess kann ein lokaler (auf demselben Computer wie der erste) oder ein Remoteprozess (auf einem Computer im Netzwerk) sein.  
  
## <a name="named-pipes-vs-tcpip-sockets"></a>Named Pipes im Vergleich zu TCP/IP-Sockets  
 In einer schnellen LAN-Umgebung (Local Area Network) sind TCP/IP-Sockets (Transmission Control Protocol/Internet Protocol) und Named Pipes-Clients hinsichtlich der Leistung vergleichbar. Der Leistungsunterschied zwischen TCP/IP-Sockets und Named Pipes-Clients wird jedoch in langsameren Netzwerken, wie z. B. WANs oder Einwählverbindungen, deutlich. Ursache hierfür sind die Unterschiede in der prozessübergreifenden Kommunikation (Interprocess Communication, IPC) zwischen Peers.  
  
 Für Named Pipes ist die Netzwerkkommunikation normalerweise überwiegend interaktiv. Ein Peer sendet keine Daten, bevor ein anderer Peer sie mithilfe eines Lesebefehls anfordert. Zu einem Netzwerklesevorgang gehört normalerweise vor Beginn des Lesens der Daten das kurze Einsehen zahlreicher Named Pipes-Nachrichten. Dies kann in einem langsamen Netzwerk sehr teuer sein und übermäßigen Netzwerkverkehr verursachen, was sich wiederum auf andere Netzwerkclients auswirkt.  
  
 Darüber hinaus sollte geklärt werden, ob die Kommunikation über lokale Pipes oder Netzwerkpipes stattfindet. Wenn die Serveranwendung lokal auf dem Computer mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird, bietet sich das Verwenden des lokalen Named Pipes-Protokolls an. Lokale Named Pipes-Protokolle werden im Kernelmodus ausgeführt und sind sehr schnell.  
  
 Für TCP/IP-Sockets sind Datenübertragungen geradliniger und mit weniger Verwaltungsaufwand verbunden. Datenübertragungen können auch von Mechanismen zur TCP/IP-Socketleistungserweiterung, wie beispielsweise Windowing, verzögerten Bestätigungen usw. profitieren. Dies kann in einem langsamen Netzwerk sehr hilfreich sein. Abhängig vom Anwendungstyp können diese Leistungsunterschiede sehr deutlich sein.  
  
 TCP/IP-Sockets unterstützen zudem eine Backlogwarteschlange. Dadurch kann im Vergleich zu Named Pipes, die aufgrund von ausgelasteten Pipes zu Fehlern beim Verbindungsversuch mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]führen können, ein begrenzter Glättungseffekt erreicht werden.  
  
 Im Allgemeinen wird TCP/IP in einem langsamen LAN, WAN oder DFÜ-Netzwerk bevorzugt. Wenn die Netzwerkgeschwindigkeit keine Rolle spielt, stellen Named Pipes hingegen häufig die bessere Wahl dar, da sie mehr Funktionalität, größere Benutzerfreundlichkeit und mehr Konfigurationsoptionen bieten.  
  
## <a name="enabling-the-protocol"></a>Aktivieren des Protokolls  
 Das Protokoll muss sowohl auf dem Client als auch dem Server aktiviert sein. Der Server kann gleichzeitig auf alle aktivierten Protokolle auf Anforderungen lauschen. Clientcomputer können ein Protokoll auswählen oder das Verwenden der Protokolle in der Reihenfolge versuchen, in der sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager angegeben sind.  
  
 Ein kurzes Tutorial zum Konfigurieren von Protokollen und zum Herstellen einer Verbindung mit [!INCLUDE[ssDE](../../includes/ssde-md.md)] finden Sie unter [Tutorial: Erste Schritte mit der Datenbank-Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).  
  
  
