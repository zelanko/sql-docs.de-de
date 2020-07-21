---
title: MSSQLSERVER_-1 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed9c25be4a4e3cfa6b0c00c9dc790214415d3593
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554235"
---
# <a name="mssqlserver_-1"></a>MSSQLSERVER_-1
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|-1|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Fehler beim Herstellen einer Verbindung mit dem Server.  Beim Herstellen der Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann dieser Fehler dadurch verursacht worden sein, dass die Standardeinstellungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Remoteverbindungen zulassen. (Anbieter: SQL-Netzwerkschnittstellen, Fehler: 28 - Server unterstützt das angeforderte Protokoll nicht) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Fehler: -1)|  
  
## <a name="explanation"></a>Erklärung  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client kann keine Verbindung mit dem Server herstellen. Dieser Fehler kann auf einen der folgenden Gründe zurückzuführen sein:  
  
-   Ein angegebener [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanzenname ist nicht gültig.  
  
-   Die TCP- oder Named Pipes-Protokolle sind nicht aktiviert.  
  
-   Die Firewall auf dem Server hat die Verbindung abgelehnt.  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browserdienst (sqlbrowser) wurde nicht gestartet.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie zum Beheben dieses Fehlers eine der folgenden Aktionen aus:  
  
-   Überprüfen Sie die Rechtschreibung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanznamens, der in der Verbindungszeichenfolge angegeben ist.  
  
-   Verwenden Sie das Tool [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Configuration Manager, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu ermöglichen, Remoteverbindungen mithilfe von TCP oder Named Pipes zu akzeptieren.  
  
-   Stellen Sie sicher, dass Sie die Firewall auf der Serverinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] so konfiguriert haben, dass Ports für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browserport (UDP 1434) geöffnet werden.  
  
-   Stellen Sie sicher, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browserdienst auf dem Server gestartet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren einer Windows-Firewall für den Datenbank-Engine Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Netzwerkprotokolle und Netzwerk Bibliotheken](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Client-Netzwerkkonfiguration](../../database-engine/configure-windows/client-network-configuration.md)   
 [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
