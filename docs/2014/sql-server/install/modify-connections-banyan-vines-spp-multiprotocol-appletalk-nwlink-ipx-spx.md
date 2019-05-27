---
title: Ändern von Verbindungen, mit denen Netzwerkprotokolle für Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk oder NWLink IPX SPX | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: cdbcaa39e3d9630bd4ea50919f31cdbb15a36d14
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093900"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a>Ändern von Verbindungen, die die Netzwerkprotokolle Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk oder NWLink IPX/SPX verwenden
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
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
