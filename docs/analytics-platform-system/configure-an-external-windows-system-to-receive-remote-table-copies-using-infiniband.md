---
title: Konfigurieren von Windows zum Empfangen von Remote Tabellen Kopien
description: Hier wird beschrieben, wie ein nicht-Appliance-Windows-System, das über das InfiniBand-Netzwerk verbunden ist, für die Verwendung mit dem Feature zum Kopieren von Remote Tabellen parallel Data Warehouse verwendet wird. Das Windows-System hostet die SQL Server Datenbank, die die Remote Tabellen Kopie aus einer SQL Server PDW-Datenbank empfängt. Sie wird separat von der Appliance gekauft und mit dem InfiniBand-Netzwerk der Anwendung verbunden.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 837d41cc929d90b2494682645127f985b5768546
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401312"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>Konfigurieren eines externen Windows-Systems zum Empfangen von Remote Tabellen Kopien mithilfe von InfiniBand-parallel Data Warehouse
In diesem Thema wird beschrieben, wie Sie ein nicht Appliance-Windows-System, das über das InfiniBand-Netzwerk verbunden ist, für die Verwendung mit dem Feature zum Kopieren von Remote Tabellen in SQL Server PDW Das Windows-System hostet die SQL Server Datenbank, die die Remote Tabellen Kopie aus einer SQL Server PDW-Datenbank empfängt. Sie wird separat von der Appliance gekauft und mit dem InfiniBand-Netzwerk der Anwendung verbunden.  
  
> [!NOTE]  
> Das Herstellen einer Verbindung über das InfiniBand-Netzwerk ist für die Verwendung der Remote Tabellen Kopie nicht erforderlich. Das Herstellen einer Verbindung über das Ethernet-Netzwerk kann erfolgen, wenn die Ethernet-Bandbreite Ihren Anforderungen entspricht.  
  
In diesem Thema wird einer der Konfigurationsschritte zum Konfigurieren der Remote Tabellen Kopie beschrieben. Eine Liste aller Konfigurationsschritte finden Sie unter Kopieren von [Remote Tabellen](remote-table-copy.md) .  
  
## <a name="before-you-begin"></a>Voraussetzungen  
Bevor Sie das externe Windows-System konfigurieren, müssen Sie folgende Schritte ausführen:  
  
1.  Erwerben Sie ein Windows-System, das die Remote Kopien erhält, oder stellen Sie es bereit.  
  
2.  Gestell des Windows-Systems im Steuerungs Gestell (wenn ausreichend Speicherplatz vorhanden ist) oder so nah wie möglich für das Gerät, sodass Sie es mit dem InfiniBand-Netzwerkgerät verbinden können.  
  
3.  Erwerben Sie InfiniBand-Kabel und einen InfiniBand-Netzwerkadapter vom Hersteller der Gerätehardware. Es wird empfohlen, beim Empfang der exportierten Daten einen Netzwerkadapter mit zwei Ports für die Fehlertoleranz zu erwerben. Ein Netzwerkadapter mit zwei Ports wird empfohlen, ist jedoch nicht zwingend erforderlich.  
  
## <a name="HowToWindows"></a>Konfigurieren eines externen Windows-Systems zum Empfangen von Remote Tabellen Kopien  
Führen Sie die folgenden Schritte aus, um das externe Windows-System zu konfigurieren:  
  
1.  Installieren Sie den InfiniBand-Netzwerkadapter in Ihrem Windows-System.  
  
2.  Verbinden Sie den InfiniBand-Netzwerkadapter mit dem InfiniBand-Hauptswitch im Steuerungs Gestell mithilfe von InfiniBand-Kabeln.  
  
3.  Installieren und konfigurieren Sie den entsprechenden Windows-Treiber für den InfiniBand-Netzwerkadapter.  
  
    InfiniBand-Treiber für Windows werden von der openfabrics Alliance entwickelt, einem Branchen Konsortium von InfiniBand-Anbietern.  Der richtige Treiber wurde möglicherweise mit dem InfiniBand-Adapter verteilt. Andernfalls kann der Treiber von www.openfabrics.org heruntergeladen werden.  
  
4.  Konfigurieren Sie die IP-Adresse für jeden Port auf dem Adapter. SMP-Systeme sind erforderlich, um statische IP-Adressen aus einem Adressbereich zu verwenden, der für diesen Zweck reserviert ist. Konfigurieren Sie den ersten Port gemäß den folgenden Parametern:  
  
    -   IP-Netzwerkadresse: 172.16.132. x  
  
    -   IP-Subnetzmaske: 255.255.128.0  
  
    -   IP-Host Bereich: 1-254  
  
    Bei InfiniBand-Netzwerkadaptern mit zwei Ports konfigurieren Sie den zweiten Port gemäß den folgenden Parametern:  
  
    -   IP-Netzwerkadresse: 172.16.132. x  
  
    -   IP-Subnetzmaske: 255.255.128.0  
  
    -   IP-Host Bereich: 1-254  
  
5.  Wenn ein zwei Port Adapter verwendet wird oder mehrere externe Windows-Systeme mit einem Gerät verbunden sind, weisen Sie jedem System in jedem IP-Subnetz eine andere Host Nummer zu.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
