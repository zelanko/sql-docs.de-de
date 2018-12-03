---
title: SQL Server XTP IO Governor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c5c66968245ff2944d1d16e73ed766b7e09ef122
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158538"
---
# <a name="sql-server-xtp-io-governor"></a>SQL Server XTP IO Governor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Das Leistungsobjekt „SQL Server XTP IO Governor“ enthält Leistungsindikatoren, die sich auf den In-Memory OLTP IO Rate Governor beziehen.

In dieser Tabelle werden die Leistungsindikatoren für **SQL Server XTP IO Governor** beschrieben.

|Leistungsindikator|und Beschreibung|  
|-------------|-----------------|  
|**Nicht genügend Guthabenwartezeiten/Sekunde**|Anzahl von Wartevorgängen aufgrund unzureichenden Guthabens in den Ratenobjekten (pro Sekunde).|
|**E/A ausgestellt/Sekunde**|Anzahl der durch Leerungsthreads ausgegeben E/A pro Sekunde.|
|**Protokollblöcke/Sekunde**|Anzahl der Protokollblöcke, die vom Controller pro Sekunde verarbeitet werden.|
|**Slots für verpasste Guthaben**|Anzahl der Slots für verpasste Guthaben, die beim Warten auf Guthaben vom Ratenobjekt verpasst wurden.|
|**Wartezeit/s für veraltete Ratenobjekte**|Anzahl der Wartevorgänge aufgrund veralteter Ratenobjekte (pro Sekunde).|
|**Gesamtrate veröffentlichter Objekte**|Gesamtanzahl der veröffentlichten Ratenobjekte.|
 

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Leistungsindikatoren für SQL Server XTP &#40;In-Memory OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
