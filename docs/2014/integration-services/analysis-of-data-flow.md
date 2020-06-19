---
title: Analyse des Datenflusses | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 5723ba6fcbcd8e5b2280fc977aa5f405d461b805
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925561"
---
# <a name="analysis-of-data-flow"></a>Analyse des Datenflusses
  Mithilfe der Daten Bank Sicht [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) können Sie `SSISDB` den Datenfluss von Paketen analysieren. In dieser Sicht wird immer dann eine Zeile angezeigt, wenn eine Datenflusskomponente Daten an eine Downstreamkomponente sendet. Anhand der Informationen können Sie ein tieferes Verständnis der Zeilen erhalten, die an jede Komponente gesendet werden.  
  
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
  
-   **wall_clock_time_ms** -die insgesamt verstrichene Ausführungszeit (in Millisekunden) für jede Komponente.  
  
-   **num_rows_per_millisecond** : die Anzahl der pro Millisekunde von jeder Komponente gesendeten Zeilen.  
  
 Die- `HAVING` Klausel wird verwendet, um einen Fehler aufgrund einer Division durch 0 in den Berechnungen zu vermeiden.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Daten in Datenflüssen](data-flow/data-in-data-flows.md)  
  
  
