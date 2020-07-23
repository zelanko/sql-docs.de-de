---
title: Absichern der Replikation über das Internet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Internet
- Internet [SQL Server replication], security
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 93ac741d35a81b9eabc305b7402e32a65426ecf8
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86915028"
---
# <a name="securing-replication-over-the-internet"></a>Securing Replication Over the Internet
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Die Replikation über das Internet bietet die größtmögliche Flexibilität, insbesondere für mobile Abonnenten. In diesem Fall muss jedoch die Internetreplikation entsprechend konfiguriert werden, um so die Sicherheit sicherstellen zu können. Für die sichere Freigabe von Daten über das Internet werden die folgenden beiden Verfahren von[!INCLUDE[msCoName](../../../includes/msconame-md.md)] empfohlen:  
  
-   Ein virtuelles privates Netzwerk (VPN)  
  
-   Die Websynchronisierungsoption für die Mergereplikation  
  
## <a name="virtual-private-network"></a>Virtuelles privates Netzwerk  
 Virtuelle private Netzwerke bieten ein unkompliziertes und sicheres, in Schichten aufgebautes Verfahren zum Replizieren von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Daten über das Internet. Die VPN-Verbindung über das Internet funktioniert logisch gesehen als WAN-Verbindung (Wide Area Network) zwischen den Standorten.  
  
 Dies wird erreicht, indem der Benutzer eine Tunnelverbindung über das Internet oder ein anderes öffentliches Netzwerk herstellen kann (mithilfe eines Protokolls, z. B. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PPTP (Point-to-Point Tunneling Protocol), das mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT 4.0 oder [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000 verfügbar ist, oder L2TP (Layer Two Tunneling Protocol), das als Bestandteil des Betriebssystems Windows 2000 verfügbar ist). Das Verfahren bietet die gleiche Sicherheit und die gleichen Funktionen, wie sie in einem privaten Netzwerk verfügbar sind.  
  
 Weitere Informationen zum Einrichten eines VPN finden Sie in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Dokumentation.  
  
## <a name="web-synchronization-through-iis"></a>Websynchronisierung über IIS  
 Mit der Websynchronisierung für die Mergereplikation ist es möglich, Daten mit dem HTTPS-Protokoll zu replizieren; so können auch Daten durch eine Firewall repliziert werden. Weitere Informationen finden Sie unter [Konfigurieren der Websynchronisierung](../../../relational-databases/replication/configure-web-synchronization.md) und [Sicherheitsarchitektur für die Websynchronisierung](../../../relational-databases/replication/security/security-architecture-for-web-synchronization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Anzeigen und Ändern von Replikationssicherheitseinstellungen](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
