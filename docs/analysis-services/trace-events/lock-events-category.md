---
title: Sperren-Ereigniskategorie | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 62804b077f43b5123b1992a6f52b29af288e2821
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040334"
---
# <a name="lock-events-category"></a>Sperren-Ereigniskategorie
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die Locked Events-Ereigniskategorie enthält die in der folgenden Tabelle beschriebenen Ereignisklassen.  
  
|Ereignisklasse|Ereignis-ID|Description|  
|-----------------|--------------|-----------------|  
|Deadlock|50|Erfasst alle Deadlockereignisse für Metadatensperren seit Beginn der Ablaufverfolgung.|  
|Lock:timeout|51|Erfasst alle Timeoutereignisse für Metadatensperren seit Beginn der Ablaufverfolgung.|  
|Lock Acquired|52|Sammelt Informationen zu Sperren, die seit Beginn der Ablaufverfolgung erworben wurden.|  
|Lock Released|53|Sammelt Informationen zu Sperren, die seit Beginn der Ablaufverfolgung freigegeben wurden.|  
|Lock Waiting|54|Sammelt Informationen zu Sperren, die sich seit Beginn der Ablaufverfolgung im Wartezustand befinden.|  
  
 Informationen zu den Spalten, die den einzelnen Lock-Ereignisklassen zugeordnet sind, finden Sie unter [Lock Events Data Columns](../../analysis-services/trace-events/lock-events-data-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Ablaufverfolgungsereignisse](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
