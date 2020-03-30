---
title: Leistung (Ereigniskategorie) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 42eb4676454f71bbc7b1dd1def4ec5de3d0b3867
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68050414"
---
# <a name="performance-event-category"></a>Leistung (Ereigniskategorie)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Verwenden Sie die **Leistung** -Ereigniskategorie zum Überwachen von **Showplan** -Ereignisklassen und von Ereignisklassen, die durch das Ausführen von SQL-DML-Operatoren (SQL Data Manipulation Language) erzeugt werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Auto Stats-Ereignisklasse](../../relational-databases/event-classes/auto-stats-event-class.md)|Gibt an, dass eine automatische Aktualisierung der Index- und Spaltenstatistiken aufgetreten ist.|  
|[Degree of Parallelism &#40;7.0 Insert&#41;-Ereignisklasse](../../relational-databases/event-classes/degree-of-parallelism-7-0-insert-event-class.md)|Zeigt an, dass von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine SELECT-, INSERT-, UPDATE- oder DELETE-Anweisung mit einem seriellen oder parallelen Plan ausgeführt wurde. Darüber hinaus wird die Anzahl der CPUs, die für den Vorgang verwendet wurden, zurückgegeben.|  
|[Performance Statistics-Ereignisklasse](../../relational-databases/event-classes/performance-statistics-event-class.md)|Überwacht die Leistung der Abfragen, die ausgeführt werden.|  
|[Showplan All (Ereignisklasse)](../../relational-databases/event-classes/showplan-all-event-class.md)|Identifiziert **Showplan** -Operatoren in einer SQL-Anweisung.|  
|[Showplan All for Query Compile-Ereignisklasse](../../relational-databases/event-classes/showplan-all-for-query-compile-event-class.md)|Zeigt Kompilierzeitdaten für **Showplan** -Operatoren an.|  
|[Showplan Statistics Profile (Ereignisklasse)](../../relational-databases/event-classes/showplan-statistics-profile-event-class.md)|Zeigt die geschätzten Kosten einer Abfrage an.|  
|[Showplan XML (Ereignisklasse)](../../relational-databases/event-classes/showplan-xml-event-class.md)|Identifiziert die **Showplan** -Operatoren in einer SQL-Anweisung. Die Ereignisklasse speichert jedes Ereignis als definiertes XML-Dokument.|  
|[Showplan XML for Query Compile (Ereignisklasse)](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)|Zeigt Kompilierzeitdaten für **Showplan** -Operatoren im XML-Format an.|  
|[Showplan XML Statistics Profile-Ereignisklasse](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)|Identifiziert die einer SQL-Anweisung zugeordneten **Showplan** -Operatoren. Die Ausgabe erfolgt als XML-Dokument.|  
|[SQL:FullTextQuery-Ereignisklasse](../../relational-databases/event-classes/sql-fulltextquery-event-class.md)|Gibt an, dass in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Volltextabfrage ausgeführt wurde.|  
|[Plan Guide Successful (Ereignisklasse)](../../relational-databases/event-classes/plan-guide-successful-event-class.md)|Zeigt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfolgreich einen Ausführungsplan für eine Abfrage oder einen Batch mit einer Planhinweisliste erzeugt hat.|  
|[Plan Guide Unsuccessful (Ereignisklasse)](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md)|Zeigt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keinen Ausführungsplan für eine Abfrage oder einen Batch mit einer Planhinweisliste erzeugen konnte.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
