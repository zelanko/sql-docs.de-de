---
title: SQL Server, Latches-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a6d0d9249a5cfb801e07a85132060bb4d1781346
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63251101"
---
# <a name="sql-server-latches-object"></a>SQL Server, Latches-Objekt
  Das **SQLServer: Latches** -Objekt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft bietet Leistungsindikatoren zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überwachen interner Ressourcen sperren, die als Latches bezeichnet werden. Das Überwachen der Latches für die Ermittlung der Benutzeraktivität und der Ressourcennutzung kann Ihnen dabei helfen, Leistungsengpässe zu erkennen.  
  
 In dieser Tabelle werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Batches** -Leistungsindikatoren beschrieben.  
  
|Batches-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|---------------------------------|-----------------|  
|**Durchschnittliche Latchwartezeit (MS)**|Durchschnittliche Latchwartezeit (in Millisekunden) für wartende Latchanforderungen.|  
|**Latchwartevorgänge/Sek.**|Anzahl der Latchanforderungen, für die Batches nicht sofort erteilt werden konnten.|  
|**Anzahl der SuperLatches**|Anzahl der Batches, die zurzeit SuperLatches-Objekte sind.|  
|**SuperLatch-Herabstufungen/Sekunde**|Anzahl der SuperLatches-Objekte, die in der letzten Sekunde zu normalen Batches herabgestuft wurden.|  
|**SuperLatch-herauf stufungen/Sekunde**|Anzahl der Batches, die in der letzten Sekunde zu SuperLatches-Objekten heraufgestuft wurden.|  
|**Latchwartezeit Gesamt (MS)**|Gesamtwartezeit (in Millisekunden) für Latchanforderungen, die in der vergangenen Sekunde warten mussten.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
