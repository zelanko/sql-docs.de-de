---
title: Zuordnen von TCP/IP-Ports zu NUMA-Knoten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d8b4b63ffb3ee47ed72e0dfe3190fe4231eca5d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48184670"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a>Zuordnen von TCP/IP-Ports zu NUMA-Knoten (SQL Server)
  In diesem Thema wird beschrieben, wie TCP/IP-Ports mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager nicht einheitlichen Speicherzugriffsknoten (Non-Uniform Memory Access, NUMA) zugeordnet werden. Beim Starten schreibt [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Knotendaten in das Fehlerprotokoll.  
  
 Lesen Sie die Knotendaten entweder aus dem Fehlerprotokoll oder aus der **sys.dm_os_schedulers** -Sicht, um die Knotennummer des gewünschten Knotens zu ermitteln. Hängen Sie eine Knoten-ID-Bitmap (eine Affinitätsmaske) in Klammern an die Portnummer an, um eine TCP/IP-Adresse und einen Port für einen oder mehrere Knoten festzulegen. Die Knoten können wahlweise im Dezimal- oder im Hexadezimalformat angegeben werden. Zum Erstellen der Bitmap nummerieren Sie die Knoten zunächst von rechts nach links, beginnend mit Null (z. B. 76543210). Erstellen Sie eine binäre Darstellung der Knotenliste; geben Sie dabei den Wert 1 für die zu verwendenden Knoten an bzw. den Wert 0 für die Knoten, die nicht berücksichtigt werden sollen. Sollen z. B. die NUMA-Knoten 0, 2 und 5 verwendet werden, geben Sie 00100101 an.  
  
|||  
|-|-|  
|NUMA-Knotennummer|76543210|  
|Maske für 0, 2 und 5, von rechts gezählt|00100101|  
  
 Konvertieren Sie die binäre Darstellung (00100101) in eine Dezimalzahl `[37]`oder in eine Hexadezimalzahl `[0x25]`. Sollen alle Knoten überwacht werden, geben Sie keine Knoten-ID an.  
  
 Wenn ein Port mehreren NUMA-Knoten zugeordnet ist, weist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Knoten Verbindungen im Round-Robin-Verfahren zu, ohne zu versuchen, zwischen den Knoten einen Lastenausgleich durchzuführen.  
  
> [!NOTE]  
>  Lesen Sie die Informationen unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konfigurieren der Datenbank-Engine zum Überwachen mehrerer TCP-Ports [, um](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)zu ermöglichen, an mehreren TCP-Ports für jede IP-Adresse zu lauschen.  
  
##  <a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a>So ordnen Sie einen TCP/IP-Port einem NUMA-Knoten zu  
  
1.  Erweitern Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurationsmanager den Eintrag **SQL Server-Netzwerkkonfiguration**, und klicken Sie dann auf **Protokolle für** *\<Instanzname>*.  
  
2.  Doppelklicken Sie im Detailbereich auf **TCP/IP**.  
  
3.  Fügen Sie auf der Registerkarte **IP-Adressen** in dem der zu konfigurierenden IP-Adresse entsprechenden Abschnitt im Feld **TCP-Port** nach der Portnummer die NUMA-Knoten-ID in Klammern hinzu. Z. B. für TCP-Port 1500 und die Knoten 0, 2 und 5, verwenden Sie `1500[37]`, oder `1500[0x25]`.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von SQLServer zur Verwendung von Soft-NUMA &#40;SQLServer&#41;](soft-numa-sql-server.md)  
  
  
