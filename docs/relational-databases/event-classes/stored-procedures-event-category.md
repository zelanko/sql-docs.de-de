---
description: Gespeicherte Prozeduren (Ereigniskategorie)
title: Gespeicherte Prozeduren (Ereigniskategorie) | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dfb42d75870d029be20171a45d0fcfb693eecb58
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97483592"
---
# <a name="stored-procedures-event-category"></a>Gespeicherte Prozeduren (Ereigniskategorie)
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
   Die **Gespeicherte Prozeduren**-Ereigniskategorie enthält allgemeine Ereignisse für gespeicherte Prozeduren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[RPC:Completed (Ereignisklasse)](../../relational-databases/event-classes/rpc-completed-event-class.md)|Gibt an, dass ein Remoteprozeduraufruf (RPC, Remote Procedure Call) abgeschlossen wurde.|  
|[PreConnect:Completed (Ereignisklasse)](../../relational-databases/event-classes/preconnect-completed-event-class.md)|Gibt an, dass die Ausführung einer Klassifizierungsfunktion der Ressourcenkontrolle beendet wird.|  
|[PreConnect:Starting-Ereignisklasse](../../relational-databases/event-classes/preconnect-starting-event-class.md)|Gibt an, dass die Ausführung einer Klassifizierungsfunktion der Ressourcenkontrolle gestartet wird.|  
|[RPC Output Parameter (Ereignisklasse)](../../relational-databases/event-classes/rpc-output-parameter-event-class.md)|Verfolgt die Ausgabeparameterwerte von Remoteprozeduraufrufen nach deren Ausführung nach.|  
|[RPC:Starting (Ereignisklasse)](../../relational-databases/event-classes/rpc-starting-event-class.md)|Gibt an, dass ein Remoteprozeduraufruf gestartet wird.|  
|[SP:CacheHit (Ereignisklasse)](../../relational-databases/event-classes/sp-cachehit-event-class.md)|Gibt an, dass sich die gespeicherte Prozedur im Cache befindet.|  
|[SP:CacheInsert (Ereignisklasse)](../../relational-databases/event-classes/sp-cacheinsert-event-class.md)|Gibt an, dass die gespeicherte Prozedur in den Cache übertragen wurde.|  
|[SP:CacheMiss (Ereignisklasse)](../../relational-databases/event-classes/sp-cachemiss-event-class.md)|Gibt an, dass die gespeicherte Prozedur nicht im Cache gefunden wurde.|  
|[SP:CacheRemove (Ereignisklasse)](../../relational-databases/event-classes/sp-cacheremove-event-class.md)|Gibt an, dass die gespeicherte Prozedur aus dem Cache entfernt wurde.|  
|[SP:Completed (Ereignisklasse)](../../relational-databases/event-classes/sp-completed-event-class.md)|Gibt an, dass die Ausführung der gespeicherten Prozedur abgeschlossen wurde.|  
|[SP:Recompile-Ereignisklasse](../../relational-databases/event-classes/sp-recompile-event-class.md)|Gibt an, dass die gespeicherte Prozedur neu kompiliert wurde.|  
|[SP:Starting (Ereignisklasse)](../../relational-databases/event-classes/sp-starting-event-class.md)|Gibt an, dass die Ausführung der gespeicherten Prozedur beginnt.|  
|[SP:StmtCompleted (Ereignisklasse)](../../relational-databases/event-classes/sp-stmtcompleted-event-class.md)|Gibt an, dass eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung in einer gespeicherten Prozedur abgeschlossen wurde.|  
|[SP:StmtStarting-Ereignisklasse](../../relational-databases/event-classes/sp-stmtstarting-event-class.md)|Gibt an, dass eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung in einer gespeicherten Prozedur gestartet wurde.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
