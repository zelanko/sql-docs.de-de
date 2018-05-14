---
title: Abfrageverarbeitung (Ereigniskategorie) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77ee9a6a5533145809fe1f8a1bbf32e72cbcad3e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="query-processing-events-category"></a>Abfrageverarbeitung (Ereigniskategorie)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die Query Processing-Ereigniskategorie enthält die in der folgenden Tabelle beschriebenen Ereignisklassen.  
  
|**Ereignisklasse**|**Ereignis-ID**|**Description**|  
|---------------------|------------------|---------------------|  
|Query Subcube|11|Query Subcube für verwendungsbasierte Optimierung.|  
|Query Subcube Verbose|12|Query Subcube mit detaillierten Informationen. Dieses Ereignis kann sich bei Aktivierung negativ auf die Leistung auswirken.|  
|Get Data From Aggregation|60|Abfrage durch Abrufen von Daten aus der Aggregation beantworten. Dieses Ereignis kann sich bei Aktivierung negativ auf die Leistung auswirken.|  
|Get Data From Cache|61|Abfrage durch Abrufen von Daten aus einem der Caches beantworten. Dieses Ereignis kann sich bei Aktivierung negativ auf die Leistung auswirken.|  
|Query Cube Begin|70|Sammelt alle Query Cube Begin-Ereignisse seit dem Start der Ablaufverfolgung.|  
|Query Cube End|71|Sammelt alle Query Cube End-Ereignisse seit dem Start der Ablaufverfolgung.|  
|Calculate Non Empty Begin|72|Die Berechnung von nicht leeren Elementen wird gestartet.|  
|Calculate Non Empty Current|73|Die Berechnung nicht leerer Elemente wird ausgeführt.|  
|Calculate Non Empty End|74|Die Berechnung nicht leerer Elemente wird beendet.|  
|Serialize Results Begin|75|Die Serialisierung von Ergebnissen wird gestartet.|  
|Serialize Results Current|76|Die Serialisierung von Ergebnissen wird ausgeführt.|  
|Serialize Results End|77|Die Serialisierung von Ergebnissen wird beendet.|  
|Execute MDX Script Begin|78|Die Ausführung des MDX-Skripts wird gestartet.|  
|Execute MDX Script Current|79|Das MDX-Skript wird ausgeführt.|  
|Execute MDX Script End|80|Die Ausführung des MDX-Skripts wird beendet.|  
|Query Dimension|81|Die Abfragedimension.|  
|VertiPaq SE Query Begin|82|VertiPaq SE-Abfrage|  
|VertiPaq SE Query End|83|VertiPaq SE-Abfrage|  
  
 Informationen zu den Spalten, die den einzelnen Ereignisklassen der Abfrageverarbeitungsereignisse zugeordnet sind, finden Sie unter [Query Processing Events Data Columns](../../analysis-services/trace-events/query-processing-events-data-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Ablaufverfolgungsereignisse](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
