---
title: Zuordnen von TCP/IP-Ports zu NUMA-Knoten (SQL Server) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie den SQL Server-Konfigurations-Manager verwenden können, um TCP/IP-Ports zu NUMA-Knoten (Non-Uniform Memory Access) zuzuordnen. Zudem erfahren Sie, wie Sie eine Knoten-ID-Bitmap erstellen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 055821c4d005c52ff20b79967fca35ac2994ff9f
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362618"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a>Zuordnen von TCP/IP-Ports zu NUMA-Knoten (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie TCP/IP-Ports mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager nicht einheitlichen Speicherzugriffsknoten (Non-Uniform Memory Access, NUMA) zugeordnet werden. Beim Starten schreibt [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Knotendaten in das Fehlerprotokoll.  
  
 Lesen Sie die Knotendaten entweder aus dem Fehlerprotokoll oder aus der **sys.dm_os_schedulers** -Sicht, um die Knotennummer des gewünschten Knotens zu ermitteln. Hängen Sie eine Knoten-ID-Bitmap (eine Affinitätsmaske) in Klammern an die Portnummer an, um eine TCP/IP-Adresse und einen Port für einen oder mehrere Knoten festzulegen. Die Knoten können wahlweise im Dezimal- oder im Hexadezimalformat angegeben werden. Zum Erstellen der Bitmap nummerieren Sie die Knoten zunächst von rechts nach links, beginnend mit Null (z. B. 76543210). Erstellen Sie eine binäre Darstellung der Knotenliste; geben Sie dabei den Wert 1 für die zu verwendenden Knoten an bzw. den Wert 0 für die Knoten, die nicht berücksichtigt werden sollen. Sollen z. B. die NUMA-Knoten 0, 2 und 5 verwendet werden, geben Sie 00100101 an.  
  
```text
NUMA node number                            76543210
Mask for 0, 2, and 5 counting from right    00100101
```
  
 Konvertieren Sie die binäre Darstellung (00100101) in eine Dezimalzahl `[37]`oder in eine Hexadezimalzahl `[0x25]`. Sollen alle Knoten überwacht werden, geben Sie keine Knoten-ID an.  
  
 Wenn ein Port mehreren NUMA-Knoten zugeordnet ist, weist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Knoten Verbindungen im Round-Robin-Verfahren zu, ohne zu versuchen, zwischen den Knoten einen Lastenausgleich durchzuführen.  
  
> [!NOTE]  
>  Lesen Sie die Informationen unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konfigurieren der Datenbank-Engine zum Überwachen mehrerer TCP-Ports [, um](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)zu ermöglichen, an mehreren TCP-Ports für jede IP-Adresse zu lauschen.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a>So ordnen Sie einen TCP/IP-Port einem NUMA-Knoten zu  
  
1.  Erweitern Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager den Eintrag **SQL Server-Netzwerkkonfiguration**, und klicken Sie dann auf **Protokolle für** *\<instance name>* .  
  
2.  Doppelklicken Sie im Detailbereich auf **TCP/IP**.  
  
3.  Fügen Sie auf der Registerkarte **IP-Adressen** in dem der zu konfigurierenden IP-Adresse entsprechenden Abschnitt im Feld **TCP-Port** nach der Portnummer die NUMA-Knoten-ID in Klammern hinzu. Verwenden Sie z.B. für den TCP-Port 1500 und die Knoten 0, 2 und 5 den Eintrag **1500[37]** oder **1500[0x25]** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Soft-NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
