---
title: Leistung (Ereigniskategorie) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7f387145077e5a562279b6c72bc0f7eefadde36
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63023304"
---
# <a name="performance-event-category"></a>Leistung (Ereigniskategorie)
  Verwenden Sie die **Leistung** -Ereigniskategorie zum Überwachen von **Showplan** -Ereignisklassen und von Ereignisklassen, die durch das Ausführen von SQL-DML-Operatoren (SQL Data Manipulation Language) erzeugt werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Auto Stats-Ereignisklasse](auto-stats-event-class.md)|Gibt an, dass eine automatische Aktualisierung der Index- und Spaltenstatistiken aufgetreten ist.|  
|[Degree of Parallelism &#40;7.0 Insert&#41;-Ereignisklasse](degree-of-parallelism-7-0-insert-event-class.md)|Zeigt an, dass von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine SELECT-, INSERT-, UPDATE- oder DELETE-Anweisung mit einem seriellen oder parallelen Plan ausgeführt wurde. Darüber hinaus wird die Anzahl der CPUs, die für den Vorgang verwendet wurden, zurückgegeben.|  
|[Performance Statistics-Ereignisklasse](performance-statistics-event-class.md)|Überwacht die Leistung der Abfragen, die ausgeführt werden.|  
|[Showplan All (Ereignisklasse)](showplan-all-event-class.md)|Identifiziert **Showplan** -Operatoren in einer SQL-Anweisung.|  
|[Showplan All for Query Compile-Ereignisklasse](showplan-all-for-query-compile-event-class.md)|Zeigt Kompilierzeitdaten für **Showplan** -Operatoren an.|  
|[Showplan Statistics Profile (Ereignisklasse)](showplan-statistics-profile-event-class.md)|Zeigt die geschätzten Kosten einer Abfrage an.|  
|[Showplan XML (Ereignisklasse)](showplan-xml-event-class.md)|Identifiziert die **Showplan** -Operatoren in einer SQL-Anweisung. Die Ereignisklasse speichert jedes Ereignis als definiertes XML-Dokument.|  
|[Showplan XML for Query Compile (Ereignisklasse)](showplan-xml-for-query-compile-event-class.md)|Zeigt Kompilierzeitdaten für **Showplan** -Operatoren im XML-Format an.|  
|[Showplan XML Statistics Profile-Ereignisklasse](showplan-xml-statistics-profile-event-class.md)|Identifiziert die einer SQL-Anweisung zugeordneten **Showplan** -Operatoren. Die Ausgabe erfolgt als XML-Dokument.|  
|[SQL:FullTextQuery-Ereignisklasse](sql-fulltextquery-event-class.md)|Gibt an, dass in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Volltextabfrage ausgeführt wurde.|  
|[Plan Guide Successful (Ereignisklasse)](plan-guide-successful-event-class.md)|Zeigt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfolgreich einen Ausführungsplan für eine Abfrage oder einen Batch mit einer Planhinweisliste erzeugt hat.|  
|[Plan Guide Unsuccessful (Ereignisklasse)](plan-guide-unsuccessful-event-class.md)|Zeigt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keinen Ausführungsplan für eine Abfrage oder einen Batch mit einer Planhinweisliste erzeugen konnte.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)  
  
  
