---
title: Ändern Sie die Verbindungen, die die Netzwerkprotokolle Banyan Vines sequenziert Packet Protocol (SPP), Multiprotocol, AppleTalk oder NWLink IPX SPX verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], modifying connections
- SPP [SQL Server]
- NWLink IPX/SPX [SQL Server]
- connections [SQL Server]
- AppleTalk [SQL Server]
- Sequenced Packet Protocol [SQL Server]
- Multiprotocol Net-Library [SQL Server]
- Banyan VINES Sequenced Package Protocol [SQL Server]
- IPX/SPX [SQL Server]
- protocols [SQL Server], modifying connections
- RPC [SQL Server]
ms.assetid: 5c5ae453-cc5b-4898-95c7-ad34157b1f60
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 750b9c0b76ab6c3b43908ecb8454f31ac1a25b1a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054707"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a>Ändern von Verbindungen, die die Netzwerkprotokolle Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk oder NWLink IPX/SPX verwenden
  Der Upgrade Advisor hat Client-Server-Verbindungsprotokolle erkannt, die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nicht unterstützt werden. Clientanwendungen, die als Netzwerkprotokoll Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol (RPC), AppleTalk oder NWLink IPX/SPX verwenden, müssen eine Verbindung über ein unterstütztes Protokoll herstellen.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] werden die Netzwerkprotokolle Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk und NWLink IPX/SPX nicht unterstützt. Clients, die zuvor Verbindungen mit diesen Protokollen hergestellt haben, müssen ein anderes Protokoll auswählen.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie die Clientanwendungen entsprechend, um ein unterstütztes Protokoll zu verwenden, wenn Sie eine Verbindung mit dem Server herstellen. Wenn ein Alias eingerichtet ist, der eines der nicht unterstützten Protokolle verwendet, muss der Alias so geändert werden, dass er eines der unterstützten Protokolle verwendet.  
  
 Wenn Ihre Anwendungs Verbindungs Zeichenfolge eines dieser Protokolle ausdrücklich verwendet oder lädt, indem Sie entweder Network = dbmsrpcn für RPC, Network = Dbmsadsn für AppleTalk oder Network = Dbmsvinn für Banyan Vines-Eigenschaft angeben, wenn Sie ein explizites Präfix wie z. b. "SPX:*/Instanznamen*" für SPX, "BV:*Server*" für Banyan-Reben, "ADSP:*Server*" für AppleTalk oder "RPC:*Server*" für MultiProtocol verwenden, müssen Sie die Anwendung so ändern, dass eines der unterstützten Protokolle verwendet wird.  
  
 Weitere Informationen finden Sie unter "Auswählen eines Netzwerkprotokolls" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
