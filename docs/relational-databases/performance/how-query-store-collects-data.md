---
title: Erfassen von Daten im Abfragespeicher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Query Store, data collection
ms.assetid: 8d5eec36-0013-480a-9c11-183e162e4c8e
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||= azure-sqldw-latest||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f60ded18e88d57c5a2975b567fa246923ece7ebe
ms.sourcegitcommit: f6bfe4a0647ce7efebaca11d95412d6a9a92cd98
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974361"
---
# <a name="how-query-store-collects-data"></a>Erfassen von Daten im Abfragespeicher
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Die Funktionsweise des SQL Server-Abfragespeichers ähnelt der von Flugdatenschreibern. Kompilierungs- und Laufzeitinformationen zu Abfragen und Plänen werden durchgehend erfasst. Daten, die sich auf Abfragen beziehen, werden in internen Tabellen gespeichert und Benutzern in mehreren Sichten angezeigt.
  
## <a name="views"></a>Sichten 
 Das folgende Diagramm zeigt Abfragespeichersichten und ihre logischen Beziehungen, wobei Kompilierzeitinformationen als blaue Entitäten dargestellt werden:
  
 ![Sichten des Abfragespeicherprozesses](../../relational-databases/performance/media/query-store-process-2views.png "query-store-process-2views")  
**Sichtbeschreibungen**  
  
|Sicht|und Beschreibung|  
|----------|-----------------|  
|**sys.query_store_query_text**|Stellt eindeutige Abfragetexte dar, die in der Datenbank ausgeführt wurden. Kommentare und Leerzeichen vor und nach dem Abfragetext werden ignoriert. Kommentare und Leerzeichen im Text werden nicht ignoriert. Jede Anweisung im Batch generiert einen separaten Abfragetexteintrag.|  
|**sys.query_context_settings**|Stellt eindeutige Kombinationen von Einstellungen dar, die sich auf Pläne auswirken, mit denen Abfragen ausgeführt werden. Derselbe Abfragetext, der mit unterschiedlichen Einstellungen zur Planauswirkung ausgeführt wurde, erzeugt separate Abfrageeinträge im Abfragespeicher, da `context_settings_id` Teil des Abfrageschlüssels ist.|  
|**sys.query_store_query**|Abfrageeinträge, die im Abfragespeicher separat nachverfolgt und erzwungen werden. Ein einzelner Abfragetext kann mehrere Abfrageeinträge generieren, wenn er unter unterschiedlichen Kontexteinstellungen bzw. außerhalb oder innerhalb verschiedener [!INCLUDE[tsql](../../includes/tsql-md.md)]-Module (z. B. gespeicherte Prozeduren und Trigger) ausgeführt wird.|  
|**sys.query_store_plan**|Stellt den geschätzten Plan für die Abfrage mit den Kompilierzeitstatistiken dar. Der gespeicherte Plan entspricht einem Plan, den Sie durch die Verwendung von `SET SHOWPLAN_XML ON` erhalten würden.|  
|**sys.query_store_runtime_stats_interval**|Der Abfragespeicher trennt die Zeit in automatisch generierte Zeitfenster (Intervalle) und speichert aggregierte Statistiken für jeden ausgeführten Plan auf diesem Intervall. Die Größe des Intervalls wird durch die Konfigurationsoption **Statistiksammlungsintervall** (in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]) oder durch `INTERVAL_LENGTH_MINUTES` mithilfe von [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) gesteuert.|  
|**sys.query_store_runtime_stats**|Aggregierte Laufzeitstatistiken für ausgeführte Pläne. Alle erfassten Metriken werden in Form von vier statistischen Funktionen ausgedrückt: Average, Minimum, Maximum und Standard Deviation (Durchschnitt, Maximum, Minimum, Standardabweichung)|  
  
 Weitere Informationen zu Abfragespeichersichten finden Sie im Abschnitt „Zugehörige Sichten, Funktionen und Prozeduren“ in [Leistungsüberwachung mit dem Abfragespeicher](monitoring-performance-by-using-the-query-store.md). 
  
## <a name="query-processing"></a>Abfrageverarbeitung
 Der Abfragespeicher interagiert an den folgenden wichtigen Punkten mit der Abfrageverarbeitungspipeline:
  
1.  Wenn eine Abfrage zum ersten Mal kompiliert wird, werden der Abfragetext und der ursprüngliche Plan an den Abfragespeicher gesendet.
  
2.  Wenn eine Abfrage neu kompiliert wird, wird der Plan im Abfragespeicher aktualisiert. Wenn ein neuer Plan erstellt wird, fügt der Abfragespeicher den neuen Planeintrag für die Abfrage ein und behält die vorherigen Pläne zusammen mit deren Ausführungsstatistiken bei.
  
3.  Bei der Abfrageausführung werden Laufzeitstatistiken an den Abfragespeicher gesendet. Der Abfragespeicher sorgt für genaue aggregierte Statistiken für jeden Plan, der innerhalb des aktuell aktiven Intervalls ausgeführt wurde. 
  
4.  Während der Kompilierung und Prüfung für Neukompilierungsphasen ermittelt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ob sich im Abfragespeicher ein Plan befindet, der auf die aktuell ausgeführte Abfrage angewendet werden sollte. Wenn ein erzwungener Plan vorliegt, und der Plan im Prozedurcache sich vom erzwungenen Plan unterscheidet, wird die Abfrage neu kompiliert. Dies entspricht der gleichen Vorgehensweise, die angewendet wird, wenn PLAN HINT auf die Abfrage angewendet wurde. Dieser Vorgang erfolgt transparent in der Benutzeranwendung. 
  
 Im folgenden Diagramm werden die Integrationspunkte aus den vorherigen Schritten dargestellt:
  
 ![Abfragespeicherprozess](../../relational-databases/performance/media/query-store-process-2processor.png "query-store-process-2processor") 

## <a name="remarks"></a>Remarks
 Zur Minimierung des E/A-Aufwands werden neue Daten im Speicher erfasst. Schreibvorgänge werden in eine Warteschlange eingereiht und danach auf den Datenträger entleert. Abfrage- und Planinformationen, die im folgenden Diagramm als „Plan Store“ (Planspeicher) angezeigt werden, werden mit minimaler Latenz geleert. Die Laufzeitstatistiken (angezeigt als „Runtime Stats“) verbleiben solange wie die `DATA_FLUSH_INTERVAL_SECONDS`-Option der `SET QUERY_STORE`-Anweisung im Arbeitsspeicher. Sie können das Dialogfeld des [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]-Abfragespeichers verwenden, um einen Wert für **Datenleerungsintervall (Minuten)** einzugeben, der intern in Sekunden konvertiert wird. 
  
 ![Plan für den Abfragespeicherprozess](../../relational-databases/performance/media/query-store-process-3.png "query-store-process-3plan") 
  
 Wenn das System abstürzt oder heruntergefahren wird, während das [Ablaufverfolgungsflag 7745](../../relational-databases/performance/best-practice-with-the-query-store.md#Recovery) verwendet wird, kann der Abfragespeicher in einem mit `DATA_FLUSH_INTERVAL_SECONDS` definierten Zeitraum Laufzeitdaten verlieren, die zwar erfasst, aber noch nicht gespeichert wurden. Der Standardwert von 900 Sekunden (15 Minuten) wird empfohlen, um ein Gleichgewicht zwischen der Abfrageerfassungsleistung und der Datenverfügbarkeit zu erzielen.
 
 > [!IMPORTANT] 
 > Der Grenzwert **Maximale Größe (MB)** wird nicht erzwungen. Die Speichergröße wird nur überprüft, wenn der Abfragespeicher Daten auf einen Datenträger schreibt. Das Intervall wird durch den Wert von **Datenleerungsintervall** festgelegt. Wenn der Abfragespeicher die maximale Größe zwischen Speichergrößenüberprüfungen überschritten hat, geht er in den schreibgeschützten Modus über. Bei Aktivierung von **Größenbasierter Bereinigungsmodus** wird auch der Bereinigungsmechanismus zum Erzwingen der maximalen Größe ausgelöst.
 
 > [!NOTE]
 > Wenn eine Arbeitsspeicherauslastung des Systems auftritt, können Laufzeitstatistiken früher auf den Datenträger geleert werden als durch `DATA_FLUSH_INTERVAL_SECONDS` definiert.
 
 Während die Abfragespeicherdaten gelesen werden, werden arbeitsspeicherinterne und auf dem Datenträger gespeicherte Daten transparent zusammengeführt. 
 
 Wenn eine Sitzung beendet oder die Clientanwendung neu gestartet wird oder abstürzt, werden keine Abfragestatistiken aufgezeichnet. 
  
 ![Informationen zum Prozessplan des Abfragespeichers](../../relational-databases/performance/media/query-store-process-4planinfo.png "query-store-process-4planinfo")    

## <a name="see-also"></a>Siehe auch
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [Bewährte Methode für den Abfragespeicher](../../relational-databases/performance/best-practice-with-the-query-store.md)  
 [Katalogsichten des Abfragespeichers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md) 
  
  
