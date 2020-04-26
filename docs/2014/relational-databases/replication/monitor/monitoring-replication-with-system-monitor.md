---
title: Überwachen der Replikation mit dem Systemmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], System Monitor
- System Monitor [SQL Server], replication
- performance counters [SQL Server replication]
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b5d1a63937a11da4703ec4ef0338dee89a5c33f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62667305"
---
# <a name="monitoring-replication-with-system-monitor"></a>Überwachen der Replikation mit dem Systemmonitor
  Der Systemmonitor von[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ermöglicht es Ihnen, Diagramme und Berichte zu verwenden, um die Effizienz des Computers zu messen, mögliche Probleme zu identifizieren und zu behandeln (wie z. B. unausgeglichene Ressourcenverwendung, unzureichende Hardware oder einen schlechten Programmentwurf) und um zusätzlichen Hardwarebedarf zu planen. Weitere Informationen finden Sie unter [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../performance-monitor/monitor-resource-usage-system-monitor.md).  
  
 Der Systemmonitor verwendet Leistungsobjekte und -indikatoren, die Informationen zur Leistung verschiedener Prozesse bereitstellen. Die Replikationsleistung kann mithilfe von Indikatoren gemessen werden, die den Replikations-Agents zugeordnet sind.  
  
|Agent|Leistungsobjekt|Leistungsindikator|BESCHREIBUNG|  
|-----------|------------------------|-------------|-----------------|  
|Alle Agents|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Agents|Wird ausgeführt|Die Anzahl der Replikations-Agents, die gerade ausgeführt werden.|  
|Momentaufnahme-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsmomentaufnahme|Momentaufnahme: Übermittelte Befehle/Sekunde|Die Anzahl der Befehle, die pro Sekunde an den Verteiler übermittelt wurden.|  
|Momentaufnahme-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsmomentaufnahme|Momentaufnahme: Übermittelte Transaktionen/Sekunde|Die Anzahl der Transaktionen, die pro Sekunde an den Verteiler übermittelt wurden.|  
|Protokolllese-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsprotokollleser|Protokollleser: Übermittelte Befehle/Sekunde|Die Anzahl der Befehle, die pro Sekunde an den Verteiler übermittelt wurden.|  
|Protokolllese-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsprotokollleser|Protokollleser: Übermittelte Transaktionen/Sekunde|Die Anzahl der Transaktionen, die pro Sekunde an den Verteiler übermittelt wurden.|  
|Protokolllese-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsprotokollleser|Protokollleser: Übermittlungslatenz|Die aktuelle Zeitspanne (in Millisekunden), die vom Zeitpunkt der Übernahme von Transaktionen auf dem Verleger bis zu ihrer Übermittlung an den Verteiler verstrichen ist.|  
|Verteilungs-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsverteilung|Verteiler: Übermittelte Befehle/Sekunde|Die Anzahl der Befehle, die pro Sekunde an den Abonnenten übermittelt wurden.|  
|Verteilungs-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsverteilung|Verteiler: Übermittelte Transaktionen/Sekunde|Die Anzahl der Transaktionen, die pro Sekunde an den Abonnenten übermittelt wurden.|  
|Verteilungs-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsverteilung|Verteiler: Übermittlungslatenz|Die aktuelle Zeitspanne (in Millisekunden), die vom Zeitpunkt der Übermittlung von Transaktionen an den Verteiler bis zu ihrer Übernahme auf dem Abonnenten verstrichen ist.|  
|Merge-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsmerge|Konflikte/Sekunde|Die Anzahl der Konflikte pro Sekunde, die im Rahmen des Mergevorgangs aufgetreten sind.|  
|Merge-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsmerge|Änderungen per Download/Sekunde|Die Anzahl der Zeilen, die pro Sekunde vom Verleger auf den Abonnenten repliziert wurden.|  
|Merge-Agent|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replikationsmerge|Änderungen per Upload/Sekunde|Die Anzahl der Zeilen, die pro Sekunde vom Abonnenten auf den Verleger repliziert wurden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachung (Replikation)](../monitoring-replication.md)  
  
  
