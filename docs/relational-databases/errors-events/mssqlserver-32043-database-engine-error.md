---
title: MSSQLSERVER_32043 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 32043 (Database Engine error)
ms.assetid: a0c48ae3-4c8c-419c-afb5-579fcefac01d
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 23abab0c3c1c98669f29e5bf1ec1b9998c3f11e6
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34322241"
---
# <a name="mssqlserver32043"></a>MSSQLSERVER_32043
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|32043|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum32043|  
|Meldungstext|Die Warnung für 'nicht wiederhergestelltes Protokoll' wurde ausgelöst. Der aktuelle Wert von '%d' überschreitet den Threshold '%d'.|  
  
## <a name="explanation"></a>Erklärung  
Dieses Ereignis der Datenbankspiegelung wird für die Spiegelserverinstanz ausgelöst, um anzugeben, dass der Umfang des nicht wiederhergestellten Protokolls einen vom Benutzer angegebenen Schwellenwert erreicht hat. Normalerweise tritt dieses Ereignis auf, weil sich die Leistung des Systems geändert hat. Entweder hat sich die Bandbreite zwischen den beiden Systemen reduziert, oder die Last hat sich erhöht.  
  
Ein nicht wiederhergestelltes Protokoll ist ein Protokoll, das von der Spiegelserverinstanz empfangen und auf einen Datenträger geschrieben wurde, das jedoch noch für die Spiegeldatenbank wiederhergestellt werden muss. Der Umfang des nicht wiederhergestellten Protokolls in Kilobyte (KB) ist eine Leistungsmetrik, mit der Sie die aktuelle Failoverzeit abschätzen können. Die zum Übernehmen des nicht wiederhergestellten Protokolls erforderliche Zeit stellt den Hauptfaktor der Failoverzeit dar – zusammen mit einer kurzen zusätzlichen Zeit, die erforderlich ist, um die Datenbank wiederherzustellen und sie online zu schalten.  
  
> [!NOTE]  
> Bei einem automatischen Failover ist die Zeit, die das System benötigt, um den Fehler zu erkennen, unabhängig von der Failoverzeit.  
  
## <a name="user-action"></a>Benutzeraktion  
Prüfen Sie die Auslastung für die Instanzen des Prinzipalservers und des Spiegelservers sowie die entsprechenden Netzwerkverbindungen, um die Ursache zu ermitteln.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Datenbankspiegelung &#40;SQL Server&#41;](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[Verwenden von Warnungsschwellenwerten und Warnmeldungen für Spiegelungsleistungsmetriken &#40;SQL Server&#41;](~/database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
