---
title: Analyse des Datenflusses | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cb8a2a6df2e3b43486329c023a1aaf948064b425
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047457"
---
# <a name="analysis-of-data-flow"></a>Analyse des Datenflusses
  Sie können die [execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` -Datenbanksicht analysieren Sie den Datenfluss von Paketen. In dieser Sicht wird immer dann eine Zeile angezeigt, wenn eine Datenflusskomponente Daten an eine Downstreamkomponente sendet. Anhand der Informationen können Sie ein tieferes Verständnis der Zeilen erhalten, die an jede Komponente gesendet werden.  
  
> [!NOTE]  
>  Der Protokollierungsgrad muss auf **Ausführlich** festgelegt werden, um Informationen mit der catalog.execution_data_statistics-Sicht aufzuzeichnen.  
  
 Im folgenden Beispiel wird die Anzahl der Zeilen angezeigt, die zwischen Komponenten eines Pakets gesendet wurden.  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 Im folgenden Beispiel wird die Anzahl der Zeilen pro Millisekunde berechnet, die von jeder Komponente für eine bestimmte Ausführung gesendet wurden. Die berechneten Werte lauten wie folgt:  
  
-   **total_rows** : Die Summe aller von der Komponente gesendeten Zeilen  
  
-   **wall_clock_time_ms** : Die insgesamt verstrichene Ausführungszeit, in Millisekunden, für jede Komponente  
  
-   **num_rows_per_millisecond** : Die Anzahl der pro Millisekunde von jeder Komponente gesendeten Zeilen  
  
 Die `HAVING` -Klausel wird verwendet, um zu verhindern, dass eine Fehler aufgrund einer Division durch Null in den Berechnungen.  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a>Related Tasks  
 [Debuggen des Datenflusses](troubleshooting/debugging-data-flow.md)  
  
 [Behandlung von Problemen mit Paketausführungstools](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Daten in Datenflüssen](data-flow/data-in-data-flows.md)  
  
  