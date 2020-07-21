---
title: MSSQLSERVER_-2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1ccfdf4f2409fa4a91e5b287b45c25918e41d1aa
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552995"
---
# <a name="mssqlserver_-2"></a>MSSQLSERVER_-2
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|-2|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Timeout ist abgelaufen.  Das Timeout ist vor dem Beenden des Vorgangs eingetreten, oder der Server reagiert nicht. (Microsoft SQL Server, Fehler: -2)|   
  
## <a name="explanation"></a>Erklärung  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client kann keine Verbindung mit dem Server herstellen. Dieser Fehler ist möglicherweise darauf zurückzuführen, dass die Verbindung von der Firewall auf dem Server abgelehnt wurde. 
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass Sie die Firewall auf der Serverinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] so konfiguriert haben, dass sie Verbindungen annimmt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der Windows-Firewall für den SQL Server Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)   
 [Konfigurieren einer Windows-Firewall für den Datenbank-Engine Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Netzwerkprotokolle und Netzwerk Bibliotheken](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Client-Netzwerkkonfiguration](../../database-engine/configure-windows/client-network-configuration.md)   
 [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
