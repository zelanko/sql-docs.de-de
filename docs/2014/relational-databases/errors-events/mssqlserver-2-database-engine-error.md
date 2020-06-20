---
title: MSSQLSERVER_2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8fdf89a03e13c40e1b72d621c120db82356db1a7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034776"
---
# <a name="mssqlserver_2"></a>MSSQLSERVER_2
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Fehler beim Herstellen einer Verbindung mit dem Server.  Beim Herstellen einer Verbindung mit SQL Server kann dieser Fehler durch den Umstand verursacht werden, dass die Standardeinstellungen von SQL Server keine Remoteverbindungen zulassen. (Anbieter: Named Pipes-Anbieter, Fehler: 40 – Es konnte keine Verbindung mit SQL Server hergestellt werden) (.Net SqlClient-Datenanbieter)|  
  
## <a name="explanation"></a>Erklärung  
 Keine Antwort von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf die Clientanforderung, da der Server wahrscheinlich nicht gestartet wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass der Server gestartet wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten der Datenbank-Engine Dienste](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Netzwerkprotokolle und Netzwerk Bibliotheken](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Client-Netzwerkkonfiguration](../../database-engine/configure-windows/client-network-configuration.md)   
 [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
