---
description: Fehler und Warnungen-Ereigniskategorie (Datenbank-Engine)
title: Fehler und Warnungen-Ereigniskategorie
ms.date: 06/03/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.custom: seo-lt-2019
ms.openlocfilehash: d40fee49969f019bc325b9a65a28b04f162560f8
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469781"
---
# <a name="errors-and-warnings-event-category-database-engine"></a>Fehler und Warnungen-Ereigniskategorie (Datenbank-Engine)
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
   Die **Fehler und Warnungen**-Ereigniskategorie enthält allgemeine Fehler- und Warnungsereignisse.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Attention-Ereignisklasse](../../relational-databases/event-classes/attention-event-class.md)|Zeigt an, dass ein **Attention** -Ereignis aufgetreten ist.|  
|[Background Job Error-Ereignisklasse](../../relational-databases/event-classes/background-job-error-event-class.md)|Zeigt an, dass ein Hintergrundauftrag fehlerbedingt beendet wurde.|  
|[Bitmap Warning-Ereignisklasse](../../relational-databases/event-classes/bitmap-warning-event-class.md)|Zeigt an, dass das Filtern von Bitmaps in einer Abfrage deaktiviert wurde.|  
|[Blocked Process Report-Ereignisklasse](../../relational-databases/event-classes/blocked-process-report-event-class.md)|Zeigt an, dass ein Task länger als die angegebene Zeitspanne blockiert wurde.|  
|[CPU Threshold Exceeded (Ereignisklasse)](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)|Zeigt an, dass die Ressourcenkontrolle eine Abfrage erkennt, die den angegebenen CPU-Schwellenwert überschreitet.|  
|[ErrorLog-Ereignisklasse](../../relational-databases/event-classes/errorlog-event-class.md)|Zeigt an, dass Fehlerereignisse im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll protokolliert wurden.|  
|[EventLog-Ereignisklasse](../../relational-databases/event-classes/eventlog-event-class.md)|Zeigt an, dass Ereignisse im Windows-Ereignisprotokoll protokolliert wurden.|  
|[Exception-Ereignisklasse](../../relational-databases/event-classes/exception-event-class.md)|Zeigt an, dass in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eine Ausnahme aufgetreten ist.|  
|[Exchange Spill (Ereignisklasse)](../../relational-databases/event-classes/exchange-spill-event-class.md)|Zeigt an, dass Kommunikationspuffer in einem parallelen Abfrageplan in die tempdb-Datenbank geschrieben wurden.|  
|[Execution Warnings (Ereignisklasse)](../../relational-databases/event-classes/execution-warnings-event-class.md)|Zeigt an, dass während der Ausführung einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anweisung oder einer gespeicherten Prozedur Warnungen zur Arbeitsspeicherzuweisung aufgetreten sind.|  
|[Hash Warning-Ereignisklasse](../../relational-databases/event-classes/hash-warning-event-class.md)|Zeigt an, dass während eines Hashvorgangs eine Hashrekursion oder ein Hashabbruch aufgetreten ist.|  
|[Missing Column Statistics-Ereignisklasse](../../relational-databases/event-classes/missing-column-statistics-event-class.md)|Zeigt an, dass Spaltenstatistiken, die vom Optimierer hätten verwendet werden können, nicht verfügbar sind.|  
|[Missing Join Predicate (Ereignisklasse)](../../relational-databases/event-classes/missing-join-predicate-event-class.md)|Zeigt an, dass eine Abfrage ohne JOIN-Prädikat ausgeführt wird.|  
|[Sort Warnings (Ereignisklasse)](../../relational-databases/event-classes/sort-warnings-event-class.md)|Zeigt an, dass der Arbeitsspeicher für Sortiervorgänge nicht ausreicht.|  
|[User Error Message-Ereignisklasse](../../relational-databases/event-classes/user-error-message-event-class.md)|Zeigt die dem Benutzer angezeigten Fehlermeldungen an.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
