---
title: Sicherheitsüberwachung-Ereigniskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d52589fc39376d5dfdfa3f540d3d1d47e89f448
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224240"
---
# <a name="security-audit-event-category"></a>Sicherheitsüberwachung-Ereigniskategorie
  Die Security Audit-Ereigniskategorie enthält die in der folgenden Tabelle beschriebenen Ereignisklassen.  
  
|Ereignisklasse|Ereignis-ID|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|Zeichnet alle neuen Verbindungsereignisse seit dem Start der Ablaufverfolgung auf (z. B. wenn ein Client eine Verbindung mit einem Server anfordert, auf dem eine Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ausgeführt wird).|  
|Audit Logout|2|Zeichnet alle neuen Ereignisse zum Trennen einer Verbindung auf, die seit dem Start der Ablaufverfolgung eingetreten sind, z. B. wenn ein Client einen Befehl zum Trennen der Verbindung ausgibt.|  
|Audit Server Starts and Stops|4|Zeichnet das Starten, Beenden und Anhalten für Dienste auf.|  
|Audit Object Permission Event|18|Zeichnet alle Änderungen von Objektberechtigungen auf.|  
|Audit Admin Operations-Ereignis|19|Zeichnet Servervorgänge für die Sicherung, Wiederherstellung, Synchronisierung, für das Anfügen und Trennen sowie für das Laden und Speichern von Images auf.|  
  
 Informationen zu den Spalten, die den einzelnen Security Audit-Ereignisklassen zugeordnet sind, finden Sie unter [Security Audit Data Columns](security-audit-data-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Ablaufverfolgungsereignisse](analysis-services-trace-events.md)  
  
  
