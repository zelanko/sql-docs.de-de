---
title: MSSQLSERVER_233 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "233"
helpviewer_keywords:
- 233 (Database Engine error)
ms.assetid: 201665dc-7ac8-4c19-90d3-33354c5caa72
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4e18ce61356947754423cfb878cf47f90534b40f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62869220"
---
# <a name="mssqlserver_233"></a>MSSQLSERVER_233
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|233|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Eine Verbindung mit dem Server wurde erfolgreich hergestellt, aber dann trat während des Anmeldevorgangs ein Fehler auf. (Anbieter: Shared Memory-Anbieter, Fehler: 0 – Kein Prozess ist am anderen Ende der Pipe.) (Microsoft SQL Server, Fehler: 233)|  
  
## <a name="explanation"></a>Erklärung  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client kann keine Verbindung mit dem Server herstellen. Dieser Fehler ist möglicherweise darauf zurückzuführen, dass der Server nicht für die Annahme von Remoteverbindungen konfiguriert ist.  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie das Tool [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager, um zuzulassen, dass in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Remoteverbindungen angenommen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Netzwerkprotokolle und Netzwerk Bibliotheken](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Client-Netzwerkkonfiguration](../../database-engine/configure-windows/client-network-configuration.md)   
 [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
