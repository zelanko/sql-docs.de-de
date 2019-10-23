---
title: 'Monitor: Vorhersagen von T-SQL mit erweiterten Ereignissen'
description: Erfahren Sie, wie Sie erweiterte Ereignisse verwenden, um Vorhersage-T-SQL-Anweisungen in SQL Server Machine Learning Services zu überwachen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 958ac3e24a9deec231e7fd4d5da14477d693f4de
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714304"
---
# <a name="monitor-predict-t-sql-statements-with-extended-events-in-sql-server-machine-learning-services"></a>Überwachen Sie die Vorhersage von T-SQL-Anweisungen mit erweiterten Ereignissen in SQL Server Machine Learning Services

Erfahren Sie, wie Sie erweiterte Ereignisse verwenden, um [Vorhersage](../../t-sql/queries/predict-transact-sql.md) -T-SQL-Anweisungen in SQL Server Machine Learning Services zu überwachen.

## <a name="table-of-extended-events"></a>Tabelle erweiterter Ereignisse

Die folgenden erweiterten Ereignisse sind in allen Versionen von SQL Server verfügbar, die die [Vorhersage](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) -T-SQL-Anweisung unterstützen. 

|NAME |object_type|description| 
|----|----|----|
|predict_function_completed |Ereignis  |Aufschlüsselung der buildausführungszeit|
|predict_model_cache_hit |Ereignis|Tritt auf, wenn ein Modell aus dem Modell Cache für Vorhersagefunktionen abgerufen wird. Verwenden Sie dieses Ereignis zusammen mit anderen predict_model_cache_ *-Ereignissen, um Probleme zu beheben, die durch den Vorhersage Funktionsmodell-Cache verursacht werden.|
|predict_model_cache_insert |Ereignis  |   Tritt auf, wenn ein Modell in den Vorhersage Funktionsmodell Cache eingefügt wird. Verwenden Sie dieses Ereignis zusammen mit anderen predict_model_cache_ *-Ereignissen, um Probleme zu beheben, die durch den Vorhersage Funktionsmodell-Cache verursacht werden.    |
|predict_model_cache_miss   |Ereignis|Tritt auf, wenn ein Modell nicht im Vorhersage Funktionsmodell Cache gefunden wird. Häufige Vorkommen dieses Ereignisses können darauf hindeuten, dass SQL Server mehr Arbeitsspeicher benötigt. Verwenden Sie dieses Ereignis zusammen mit anderen predict_model_cache_ *-Ereignissen, um Probleme zu beheben, die durch den Vorhersage Funktionsmodell-Cache verursacht werden.|
|predict_model_cache_remove |Ereignis| Tritt auf, wenn ein Modell für die Vorhersagefunktion aus dem Modell Cache entfernt wird. Verwenden Sie dieses Ereignis zusammen mit anderen predict_model_cache_ *-Ereignissen, um Probleme zu beheben, die durch den Vorhersage Funktionsmodell-Cache verursacht werden.|

## <a name="query-for-related-events"></a>Abfragen von verknüpften Ereignissen

Führen Sie die folgende Abfrage in SQL Server Management Studio aus, um eine Liste aller für diese Ereignisse zurückgegebenen Spalten anzuzeigen:

```sql
SELECT * 
FROM sys.dm_xe_object_columns 
WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>Beispiele

So erfassen Sie Informationen zur Leistung einer Bewertungs Sitzung mithilfe von Vorhersagen:

1. Erstellen Sie eine neue Sitzung für erweiterte Ereignisse mit Management Studio oder einem anderen unterstützten [Tool](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).
2. Fügen Sie die `predict_function_completed` Ereignisse `predict_model_cache_hit` und der Sitzung hinzu.
3. Starten Sie die Sitzung für erweiterte Ereignisse.
4. Führen Sie die Abfrage aus, die die Vorhersage verwendet.

Überprüfen Sie in den Ergebnissen die folgenden Spalten:

+ Der Wert für `predict_function_completed` zeigt, wie lange die Abfrage zum Laden des Modells und der Bewertung aufgewendet hat.
+ Der boolesche Wert für `predict_model_cache_hit` gibt an, ob für die Abfrage ein zwischengespeichertes Modell verwendet wurde. 

### <a name="native-scoring-model-cache"></a>Cache für Native Bewertungsmodell

Zusätzlich zu den vorher zusagenden Ereignissen können Sie die folgenden Abfragen verwenden, um weitere Informationen zum zwischengespeicherten Modell und zur Cache Verwendung zu erhalten:

Anzeigen des nativen Bewertungsmodell Caches:

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

Anzeigen der Objekte im Modell Cache:

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu erweiterten Ereignissen (manchmal auch als xevents bezeichnet) und zum Nachverfolgen von Ereignissen in einer Sitzung finden Sie in den folgenden Artikeln:

+ [Überwachen von Python-und R-Skripts mit erweiterten Ereignissen in SQL Server Machine Learning Services](extended-events.md)
+ [Konzepte und Architektur für erweiterte Ereignisse](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Einrichten der Ereignis Erfassung in SSMS](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Verwalten von Ereignis Sitzungen im Objekt-Explorer](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)
