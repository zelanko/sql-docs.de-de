---
title: Sperren-Ereigniskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 06427f8e-89bb-4710-a0c1-dc5e42b7e95e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2153de0275255f55928f10c0d6d21c0350064a1d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056360"
---
# <a name="lock-events-category"></a>Sperren-Ereigniskategorie
  Die Locked Events-Ereigniskategorie enthält die in der folgenden Tabelle beschriebenen Ereignisklassen.  
  
|Ereignisklasse|Ereignis-ID|Description|  
|-----------------|--------------|-----------------|  
|Deadlock|50|Erfasst alle Deadlockereignisse für Metadatensperren seit Beginn der Ablaufverfolgung.|  
|Lock:timeout|51|Erfasst alle Timeoutereignisse für Metadatensperren seit Beginn der Ablaufverfolgung.|  
|Lock Acquired|52|Sammelt Informationen zu Sperren, die seit Beginn der Ablaufverfolgung erworben wurden.|  
|Lock Released|53|Sammelt Informationen zu Sperren, die seit Beginn der Ablaufverfolgung freigegeben wurden.|  
|Lock Waiting|54|Sammelt Informationen zu Sperren, die sich seit Beginn der Ablaufverfolgung im Wartezustand befinden.|  
  
 Informationen zu den Spalten, die den einzelnen Lock-Ereignisklassen zugeordnet sind, finden Sie unter [Lock Events Data Columns](lock-events-data-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Ablaufverfolgungsereignisse](analysis-services-trace-events.md)  
  
  
