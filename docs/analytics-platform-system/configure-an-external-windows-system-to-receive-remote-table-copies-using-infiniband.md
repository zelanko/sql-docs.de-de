---
title: Konfigurieren von Windows zum Empfangen von remotetabellenkopien - Parallel Data Warehouse | Microsoft-Dokumentation
description: Beschreibt das erwerben und konfigurieren Sie eine nicht zur Appliance gehört Windows-System über das InfiniBand-Netzwerk für die Verwendung mit der remotetabellenkopie-Features in Parallel Data Warehouse verbunden sind. Das Windows-System hostet SQL Server-Datenbank, die die remotetabellenkopie aus einer SQL Server-PDW-Datenbank empfängt. Dabei handelt es sich aus der Appliance inbegriffene mit dem Gerät InfiniBand-Netzwerk verbunden.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ed7122f497b0bdebd893eec75606bbb6382e9a73
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224857"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>Konfigurieren eines externen Windows-Systems zum Empfangen von remotetabellenkopien mit InfiniBand - Parallel Data Warehouse
Beschreibt das erwerben und konfigurieren ein nicht zur Appliance gehört Windows-System über das InfiniBand-Netzwerk für die Verwendung mit der remotetabellenkopie-Features in SQL Server PDW verbunden sind. Das Windows-System hostet SQL Server-Datenbank, die die remotetabellenkopie aus einer SQL Server-PDW-Datenbank empfängt. Dabei handelt es sich aus der Appliance inbegriffene mit dem Gerät InfiniBand-Netzwerk verbunden.  
  
> [!NOTE]  
> Herstellen einer Verbindung über das InfiniBand-Netzwerk ist nicht für die Verwendung von remotetabellenkopie erforderlich. Herstellen einer Verbindung über das Ethernet-Netzwerk kann durchgeführt werden, wenn die Ethernet-Bandbreite Ihre Anforderungen erfüllt.  
  
Dieses Thema beschreibt eine Konfigurationsschritte für die Konfiguration von remote-Tabelle kopieren. Eine Liste der alle Konfigurationsschritte, finden Sie unter [Remotetabellenkopie](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
Bevor Sie das externe Windows-System konfigurieren, müssen Sie folgende Schritte ausführen:  
  
1.  Geben Sie ein Windows-System, das die remote-Kopien erhält, oder erwerben.  
  
2.  Einbauen Sie das Windows-System in das Steuerelement Rack, (sofern genügend Speicherplatz vorhanden ist), oder schließen Sie genug, um das Gerät, damit Sie das Gerät InfiniBand-Netzwerk hergestellt werden können.  
  
3.  InfiniBand-Kabel und einem InfiniBand-Netzwerkadapter vom Geräteanbieter Hardware zu erwerben. Es wird empfohlen, einen Netzwerkadapter mit zwei Ports für die Fehlertoleranz erwerben, wenn Sie die exportierten Daten zu empfangen. Ein Netzwerkadapter für die beiden wird empfohlen, aber es ist nicht erforderlich.  
  
## <a name="HowToWindows"></a>Konfigurieren eines externen Windows-Systems zum Empfangen von Remotetabellenkopien  
Um das externe Windows-System zu konfigurieren, verwenden Sie die folgenden Schritte aus:  
  
1.  Installieren Sie den InfiniBand-Netzwerkadapter in Ihr Windows-System.  
  
2.  Verbinden Sie den InfiniBand-Netzwerkadapter mit dem wichtigsten InfiniBand-Switch in das Steuerelement Rack mit InfiniBand-Kabel.  
  
3.  Installieren Sie und konfigurieren Sie den entsprechenden Windows-Treiber für das InfiniBand-Netzwerkadapter.  
  
    InfiniBand-Treibern für Windows werden durch die OpenFabrics Alliance, ein Branchenkonsortium von InfiniBand-Anbietern entwickelt.  Der richtige Treiber möglicherweise mit Ihrem Adapter InfiniBand verteilt wurden. Wenn dies nicht der Fall ist, kann der Treiber www.openfabrics.org heruntergeladen werden.  
  
4.  Konfigurieren Sie die IP-Adresse für jeden Port auf dem Adapter. SMP-Systemen sind erforderlich, um die statische IP-Adressen aus einem Bereich von reservierten Adressen zu diesem Zweck verwenden. Konfigurieren Sie den ersten Port entsprechend den folgenden Parametern:  
  
    -   IP-Netzwerkadresse: 172.16.132.x  
  
    -   IP-Subnetzmaske: 255.255.128.0  
  
    -   IP-Host-Bereich: 1-254  
  
    Konfigurieren Sie für InfiniBand-Netzwerkadapter mit zwei Ports des zweiten Ports entsprechend den folgenden Parametern aus:  
  
    -   IP-Netzwerkadresse: 172.16.132.x  
  
    -   IP-Subnetzmaske: 255.255.128.0  
  
    -   IP-Host-Bereich: 1-254  
  
5.  Wenn ein Portadapter zwei wird verwendet, oder mehreren externe Windows-Systemen in einer Anwendung verbunden sind, weisen Sie jedes System einen anderen Host Anzahl in jedem IP-Subnetz.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
