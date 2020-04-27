---
title: MSSQLSERVER_1105 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5ee98c0144d492b74e8ddc2785b21b76a363eb92
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915934"
---
# <a name="mssqlserver_1105"></a>MSSQLSERVER_1105
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1105|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NO_MORE_SPACE_IN_FG|  
|Meldungstext|Speicherplatz für das '%.*ls'%.\*ls-Objekt in der '%.\*ls'-Datenbank konnte nicht zugeordnet werden, da die '%.\*ls'-Dateigruppe voll ist. Speicherplatz kann durch Löschen nicht benötigter Dateien, Löschen von Objekten in der Dateigruppe, Hinzufügen von Dateien zur Dateigruppe oder Festlegen der automatischen Vergrößerung für vorhandene Dateien in der Dateigruppe gewonnen werden.|  
  
## <a name="explanation"></a>Erklärung  
 In einer Dateigruppe ist kein Speicherplatz verfügbar.  
  
## <a name="user-action"></a>Benutzeraktion  
 Durch die folgenden Aktionen kann Speicherplatz in der Dateigruppe verfügbar gemacht werden:  
  
-   Aktivieren Sie die automatische Vergrößerung.  
  
-   Fügen Sie der Dateigruppe weitere Dateien hinzu.  
  
-   Geben Sie Speicherplatz frei, indem Sie Indizes oder Tabellen löschen, die nicht mehr benötigt werden.  
  
-   Weitere Informationen finden Sie unter "Problembehandlung bei unzureichendem Speicherplatz" in der SQL Server-Onlinedokumentation.  
  
> [!NOTE]  
>  Wenn sich ein Index in mehreren Dateien befindet, kann `ALTER INDEX REORGANIZE` Fehler 1105 zurückgeben, wenn eine der Dateien voll ist. Der Neuorganisationsvorgang wird blockiert, wenn während des Prozesses versucht wird, Zeilen in die volle Datei zu verschieben. Führen Sie `ALTER INDEX REBUILD` statt `ALTER INDEX REORGANIZE` aus, oder erhöhen Sie die Erweiterungsgrenze voller Dateien, um diese Einschränkung zu umgehen.  
  
  
