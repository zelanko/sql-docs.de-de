---
title: Statusberichte (Ereigniskategorie) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f3e48e34e5b85093793b0ea70786b106d72235a7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="progress-reports-event-category"></a>Fortschrittsbericht (Ereigniskategorie)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die Progress Reports-Ereigniskategorie enthält die in der folgenden Tabelle beschriebenen Ereignisklassen.  
  
|Ereignisklasse|Ereignis-ID|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|Sammelt alle Progress Report Begin-Ereignisse seit dem Start der Ablaufverfolgung.|  
|Progress Report End|6|Sammelt alle Progress Report End-Ereignisse seit dem Start der Ablaufverfolgung.|  
|Progress Report Current|7|Sammelt alle Progress Report Current-Ereignisse seit dem Start der Ablaufverfolgung. Beispielsweise enthalten während der Verarbeitung die Current Reports Verarbeitungsinformationen zu den verarbeiteten Objekten (Dimensionen, Partitionen, Cube usw.).|  
|Progress Report Error|8|Sammelt alle Progress Report Error-Ereignisse seit dem Start der Ablaufverfolgung.|  
  
 Jedes Progress Report Begin-Ereignis beginnt mit einem Datenstrom aus Progress-Ereignissen und wird durch ein Progress Report End-Ereignis beendet. Der Datenstrom kann jede beliebige Anzahl von Progress Report Current- und Progress Report Error-Ereignissen enthalten.  
  
 Informationen zu den Spalten, die den einzelnen Progress Reports-Ereignisklassen zugeordnet sind, finden Sie unter [Progress Reports Data Columns](../../analysis-services/trace-events/progress-reports-data-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Ablaufverfolgungsereignisse](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
