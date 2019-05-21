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
manager: craigg
ms.openlocfilehash: 4f849d6c282fda16709b556131e44dd1ce9cd5ce
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380191"
---
# <a name="sql-server-xtp-io-governor"></a>SQL Server XTP IO Governor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Das Leistungsobjekt „SQL Server XTP IO Governor“ enthält Leistungsindikatoren, die sich auf den In-Memory OLTP IO Rate Governor beziehen.

In dieser Tabelle werden die Leistungsindikatoren für **SQL Server XTP IO Governor** beschrieben.

|Leistungsindikator|Beschreibung|  
|-------------|-----------------|  
|**Nicht genügend Guthabenwartezeiten/Sekunde**|Anzahl von Wartevorgängen aufgrund unzureichenden Guthabens in den Ratenobjekten (pro Sekunde).|
|**E/A ausgestellt/Sekunde**|Anzahl der durch Leerungsthreads ausgegeben E/A pro Sekunde.|
|**Protokollblöcke/Sekunde**|Anzahl der Protokollblöcke, die vom Controller pro Sekunde verarbeitet werden.|
|**Slots für verpasste Guthaben**|Anzahl der Slots für verpasste Guthaben, die beim Warten auf Guthaben vom Ratenobjekt verpasst wurden.|
|**Wartezeit/s für veraltete Ratenobjekte**|Anzahl der Wartevorgänge aufgrund veralteter Ratenobjekte (pro Sekunde).|
|**Gesamtrate veröffentlichter Objekte**|Gesamtanzahl der veröffentlichten Ratenobjekte.|
 

## <a name="see-also"></a>Weitere Informationen  
[Leistungsindikatoren für SQL Server XTP &#40;In-Memory OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
