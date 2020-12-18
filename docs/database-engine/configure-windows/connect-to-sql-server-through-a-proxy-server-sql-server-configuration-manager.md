---
title: Verbindungsaufbau mit SQL Server über einen Proxyserver (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit dem SQL Server-Konfigurations-Manager eine Verbindung mit SQL Server über einen Proxyserver herstellen. Zudem erfahren Sie, wie Sie Remote WinSock (RWS) für die Remoteüberwachung verwenden.
ms.custom: ''
ms.date: 12/15/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 74187c8e806e6dd1cadb9ea38860b11ec0bcaba0
ms.sourcegitcommit: f87f2f0f1edc91fe400040d8e3a5810347aa8d70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96857677"
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a>Verbindungsaufbau mit SQL Server über einen Proxyserver (SQL Server-Konfigurations-Manager)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In diesem Thema wird beschrieben, wie Sie über einen Proxyserver in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe des SQL Server-Konfigurations-Managers eine Verbindung zu SQL Server herstellen. Für die Remoteüberwachung über Remote WinSock (RWS) definieren Sie die lokale Adresstabelle (LAT, Local Address Table) für den Proxyserver so, dass sich die Überwachungsknotenadresse außerhalb des Bereichs der lokalen Adresstabelleneinträge befindet.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-enable-connections-to-sql-server-through-proxy-server"></a>Herstellen von Verbindungen mit SQL Server über Proxyserver  
  
1.  Führen Sie die Schritte in [Vorgehensweise: Konfigurieren eines Servers zur Überwachung eines bestimmten TCP-Ports &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md), um zu bestimmen, welche TCP/IP-Ports vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] verwendet werden, oder um das [!INCLUDE[ssDE](../../includes/ssde-md.md)] zu konfigurieren, um einen gewünschten Port zu verwenden.  
  
2.  Definieren Sie auf Ihrem Proxyserver die lokale Adresstabelle (LAT) für den Proxyserver so, dass sich die Überwachungsknotenadresse außerhalb des Bereichs der lokalen Adresstabelleneinträge befindet. Weitere Informationen finden Sie in der Proxyserver-Dokumentation.  
  
> [!NOTE]
>  Dieses Thema betrifft den lokalen [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Informationen zu Verbindungsproblemen im Zusammenhang mit [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]finden Sie unter [Beheben von Verbindungsproblemen mit der Azure SQL-Datenbank](/azure/sql-database/sql-database-troubleshoot-common-connection-issues).
