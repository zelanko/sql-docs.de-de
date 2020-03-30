---
title: SQL Server XTP IO Governor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 975dca6fe0151b5bd1fc1d72b9d14e47a57413d2
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67915211"
---
# <a name="sql-server-xtp-io-governor"></a>SQL Server XTP IO Governor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Das Leistungsobjekt „SQL Server XTP IO Governor“ enthält Leistungsindikatoren, die sich auf den In-Memory OLTP IO Rate Governor beziehen.

In dieser Tabelle werden die Leistungsindikatoren für **SQL Server XTP IO Governor** beschrieben.

|Leistungsindikator|BESCHREIBUNG|  
|-------------|-----------------|  
|**Nicht genügend Guthabenwartezeiten/Sekunde**|Anzahl von Wartevorgängen aufgrund unzureichenden Guthabens in den Ratenobjekten (pro Sekunde).|
|**E/A ausgestellt/Sekunde**|Anzahl der durch Leerungsthreads ausgegeben E/A pro Sekunde.|
|**Protokollblöcke/Sekunde**|Anzahl der Protokollblöcke, die vom Controller pro Sekunde verarbeitet werden.|
|**Slots für verpasste Guthaben**|Anzahl der Slots für verpasste Guthaben, die beim Warten auf Guthaben vom Ratenobjekt verpasst wurden.|
|**Wartezeit/s für veraltete Ratenobjekte**|Anzahl der Wartevorgänge aufgrund veralteter Ratenobjekte (pro Sekunde).|
|**Gesamtrate veröffentlichter Objekte**|Gesamtanzahl der veröffentlichten Ratenobjekte.|
 

## <a name="see-also"></a>Weitere Informationen  
[Leistungsindikatoren für SQL Server XTP &#40;In-Memory-OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
