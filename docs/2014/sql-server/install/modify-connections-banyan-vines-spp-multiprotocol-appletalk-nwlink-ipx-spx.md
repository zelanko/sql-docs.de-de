---
title: Ändern von Verbindungen, mit denen Netzwerkprotokolle für Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk oder NWLink IPX SPX | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5b2b8e2d6ead66108b76d03bbfc020d9345afcd7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296010"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a>Ändern von Verbindungen, die Netzwerkprotokolle für Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk oder NWLink IPX SPX verwenden
  Der Upgrade Advisor hat Client-Server-Verbindungsprotokolle erkannt, die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nicht unterstützt werden. Clientanwendungen, die als Netzwerkprotokoll Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol (RPC), AppleTalk oder NWLink IPX/SPX verwenden, müssen eine Verbindung über ein unterstütztes Protokoll herstellen.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] werden die Netzwerkprotokolle Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk und NWLink IPX/SPX nicht unterstützt. Clients, die zuvor Verbindungen mit diesen Protokollen hergestellt haben, müssen ein anderes Protokoll auswählen.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie die Clientanwendungen entsprechend, um ein unterstütztes Protokoll zu verwenden, wenn Sie eine Verbindung mit dem Server herstellen. Wenn ein Alias eingerichtet ist, der eines der nicht unterstützten Protokolle verwendet, muss der Alias so geändert werden, dass er eines der unterstützten Protokolle verwendet.  
  
 Wenn Ihre Anwendung Verbindungszeichenfolge speziell verwendet oder lädt, die eines der folgenden Protokolle, von einem der angeben Netzwerke = DBMSRPCN für RPC, NETWORK = DBMSADSN für Appletalk oder NETWORK = DBMSVINN, für Banyan VINES-Eigenschaft, oder indem Sie ein explizites Präfix wie "Spx: *Server\Instanz*"für SPX," bv:*Server*"für Banyan VINES," Adsp:*Server*"für AppleTalk oder" Rpc:*Server*"für Multiprotokoll, müssen dann Sie die Anwendung eines der unterstützten Protokolle verwendet ändern.  
  
 Weitere Informationen finden Sie unter "Auswählen eines Netzwerkprotokolls" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
