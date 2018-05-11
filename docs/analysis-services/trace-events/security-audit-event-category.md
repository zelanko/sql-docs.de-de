---
title: Sicherheitsüberwachung-Ereigniskategorie | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 39c5198bc94a081ee796be13971a0a2ad985cf3f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="security-audit-event-category"></a>Sicherheitsüberwachung-Ereigniskategorie
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die Security Audit-Ereigniskategorie enthält die in der folgenden Tabelle beschriebenen Ereignisklassen.  
  
|Ereignisklasse|Ereignis-ID|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|Zeichnet alle neuen Verbindungsereignisse seit dem Start der Ablaufverfolgung auf (z. B. wenn ein Client eine Verbindung mit einem Server anfordert, auf dem eine Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ausgeführt wird).|  
|Audit Logout|2|Zeichnet alle neuen Ereignisse zum Trennen einer Verbindung auf, die seit dem Start der Ablaufverfolgung eingetreten sind, z. B. wenn ein Client einen Befehl zum Trennen der Verbindung ausgibt.|  
|Audit Server Starts and Stops|4|Zeichnet das Starten, Beenden und Anhalten für Dienste auf.|  
|Audit Object Permission Event|18|Zeichnet alle Änderungen von Objektberechtigungen auf.|  
|Audit Admin Operations-Ereignis|19|Zeichnet Servervorgänge für die Sicherung, Wiederherstellung, Synchronisierung, für das Anfügen und Trennen sowie für das Laden und Speichern von Images auf.|  
  
 Informationen zu den Spalten, die den einzelnen Security Audit-Ereignisklassen zugeordnet sind, finden Sie unter [Security Audit Data Columns](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Ablaufverfolgungsereignisse](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
