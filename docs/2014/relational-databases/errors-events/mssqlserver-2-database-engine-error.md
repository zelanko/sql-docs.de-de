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
manager: craigg
ms.openlocfilehash: 8d1e10db6b9bb123bf82c0790cbc8be10388dddc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915217"
---
# <a name="mssqlserver2"></a>MSSQLSERVER_2
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Fehler beim Herstellen einer Verbindung mit dem Server.  Beim Herstellen einer Verbindung mit SQL Server kann dieser Fehler durch den Umstand verursacht werden, dass die Standardeinstellungen von SQL Server keine Remoteverbindungen zulassen. (Anbieter: Named Pipes-Anbieter, Fehler: 40 - Es konnte keine Verbindung zu SQL Server hergestellt werden) (.Net SqlClient-Datenanbieter)|  
  
## <a name="explanation"></a>Erklärung  
 Keine Antwort von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf die Clientanforderung, da der Server wahrscheinlich nicht gestartet wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass der Server gestartet wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten der Datenbank-Engine-Dienste](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [Konfigurieren von Clientprotokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Netzwerkprotokolle und Netzwerkbibliotheken](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Client-Netzwerkkonfiguration](../../database-engine/configure-windows/client-network-configuration.md)   
 [Konfigurieren von Clientprotokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
