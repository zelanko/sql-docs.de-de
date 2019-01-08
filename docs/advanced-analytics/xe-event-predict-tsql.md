---
title: Erweiterte Ereignisse für die Überwachung von PREDICT-Anweisungen – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e680da7485069e6838edff260a505461a22c472b
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432243"
---
# <a name="extended-events-for-monitoring-predict-statements"></a>Erweiterte Ereignisse für die Überwachung von PREDICT-Anweisungen

Dieser Artikel beschreibt die erweiterten Ereignisse, bereitgestellt in SQL Server verwenden, Sie verwenden können, zum Überwachen und Analysieren von Aufträgen [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) auszuführenden echtzeitbewertung in SQL Server.

Echtzeitbewertung generiert Ergebnisse von einem Machine learning-Modell, das in SQL Server gespeichert wurde. Die PREDICT-Funktion erfordert keine externe Laufzeit wie R oder Python, nur ein Modell, das mit einem bestimmten binären Format erstellt wurde. Weitere Informationen finden Sie unter [in Echtzeit bewerten](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

## <a name="prerequisites"></a>Erforderliche Komponenten

Allgemeine Informationen zu erweiterten Ereignissen (XEvents bezeichnet) und wie Sie Ereignisse in einer Sitzung zu überwachen finden Sie in diesen Artikeln:

+ [Erweiterte Ereignisse-Konzepte und-Architektur](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Richten Sie ereignisaufzeichnungen in SSMS](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Verwalten von ereignissitzungen im Objekt-Explorer](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)

## <a name="table-of-extended-events"></a>Tabelle erweiterter Ereignisse

Die folgende erweiterte Ereignisse stehen in allen Versionen von SQL Server, die Unterstützung der [VORHERZUSAGEN, T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) -Anweisung, einschließlich SQL Server unter Linux und Azure SQL-Datenbank. 

Die VORHERSAGE von T-SQL-Anweisung wurde in SQL Server 2017 eingeführt. 

|NAME |object_type|description| 
|----|----|----|
|predict_function_completed |Ereignis  |"Vordefiniert" Ausführungszeit Aufschlüsselung|
|predict_model_cache_hit |Ereignis|Tritt auf, wenn ein Modell aus dem Modellcache der PREDICT-Funktion abgerufen wird. Verwenden Sie dieses Ereignis zusammen mit anderen Predict_model_cache_ *-Ereignissen, um durch den Modellcache der PREDICT-Funktion verursachte Probleme zu beheben.|
|predict_model_cache_insert |Ereignis  |   Tritt auf, wenn ein Modell einfügen, in den Modellcache der PREDICT-Funktion. Verwenden Sie dieses Ereignis zusammen mit anderen Predict_model_cache_ *-Ereignissen, um durch den Modellcache der PREDICT-Funktion verursachte Probleme zu beheben.    |
|predict_model_cache_miss   |Ereignis|Tritt auf, wenn ein Modell nicht in den Modellcache der PREDICT-Funktion gefunden wird. Ein häufige Auftreten dieses Ereignisses hinweisen, dass SQL Server mehr Arbeitsspeicher benötigt. Verwenden Sie dieses Ereignis zusammen mit anderen Predict_model_cache_ *-Ereignissen, um durch den Modellcache der PREDICT-Funktion verursachte Probleme zu beheben.|
|predict_model_cache_remove |Ereignis| Tritt auf, wenn ein Modell aus dem Modellcache für die PREDICT-Funktion entfernt wird. Verwenden Sie dieses Ereignis zusammen mit anderen Predict_model_cache_ *-Ereignissen, um durch den Modellcache der PREDICT-Funktion verursachte Probleme zu beheben.|

## <a name="query-for-related-events"></a>Abfrage nach verwandten Ereignissen

Um eine Liste aller Spalten zurückgegeben, die für diese Ereignisse anzuzeigen, führen Sie die folgende Abfrage in SQL Server Management Studio aus:

```sql
SELECT * FROM sys.dm_xe_object_columns WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>Beispiele

So erfassen Sie Informationen zur Leistung einer Bewertung Sitzung VORHERSAGEN:

1. Erstellen Sie eine neue erweiterte ereignissitzung mit Management Studio oder eines anderen unterstützten [Tool](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).
2. Fügen Sie die Ereignisse `predict_function_completed` und `predict_model_cache_hit` mit der Sitzung.
3. Starten Sie die Sitzung für erweiterte Ereignisse.
4. Führen Sie die Abfrage verwendet, die VORHERSAGEN.

Überprüfen Sie in den Ergebnissen dieser Spalten aus:

+ Der Wert für `predict_function_completed` zeigt, wie viel Zeit die Abfrage, die für das Laden des Modells und die Bewertung aufgewendet.
+ Der boolesche Wert für `predict_model_cache_hit` gibt an, ob die Abfrage ein zwischengespeichertes Modell oder nicht verwendet. 

### <a name="native-scoring-model-cache"></a>Native Bewertung Modellcache

Zusätzlich zu den Ereignissen, die speziell für VORHERSAGEN können Sie die folgenden Abfragen um weitere Informationen zu den cachemodell und die cachenutzung zu erhalten:

Ansicht der nativen Bewertung Modellcache:

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

Zeigen Sie die Objekte im Speicher des Modell-Caches:

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

