---
title: Erstellen manueller Ablaufverfolgungen mit gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 247548de6f3a89afac2143347d987a6f6d638c55
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62714818"
---
# <a name="create-manual-traces-using-stored-procedures"></a>Erstellen manueller Ablaufverfolgungen mit gespeicherten Prozeduren
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt zum Erstellen von Ablaufverfolgungen für eine Instanz von [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Systemprozeduren zur Verfügung. Sie können aus Ihren Anwendungen heraus diese gespeicherten Systemprozeduren verwenden, um Ablaufverfolgungen statt mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]manuell zu erstellen. Dadurch können Sie benutzerdefinierte Anwendungen schreiben, die den speziellen Anforderungen Ihres Unternehmens entsprechen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In der folgenden Tabelle werden die gespeicherten Systemprozeduren für die Ablaufverfolgung einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]aufgelistet.  
  
|Gespeicherte Prozedur|Ausgeführter Task|  
|----------------------|--------------------|  
|[sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql)|Gibt die Informationen zu in einer Ablaufverfolgung enthaltenen Ereignisse zurück.|  
|[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)|Gibt Informationen zu einer angegebene Ablaufverfolgung oder zu alle vorhandenen Ablaufverfolgungen zurück.|  
|[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)|Erstellt eine Ablaufverfolgungsdefinition. Die neue Ablaufverfolgung weist einen beendeten Status auf.|  
|[sp_trace_generateevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)|Erstellt ein benutzerdefiniertes Ereignis.|  
|[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)|Fügt einer Ablaufverfolgung eine Ereignisklasse oder eine Datenspalte hinzu oder entfernt eine Ereignisklasse oder eine Datenspalte aus einer Ablaufverfolgung.|  
|[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|Startet, beendet oder schließt eine Ablaufverfolgung.|  
|[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)|Gibt Informationen über für eine Ablaufverfolgung angewendete Filter zurück.|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|Wendet einen neuen oder geänderten Filter für eine Ablaufverfolgung an.|  
  
 **So definieren Sie eine eigene Ablaufverfolgung mithilfe von gespeicherten Prozeduren**  
  
1.  Geben Sie die Ereignisse, die aufgezeichnet werden sollen, mit **sp_trace_setevent**an.  
  
2.  Geben Sie Ereignisfilter an. Weitere Informationen finden Sie unter [Festlegen eines Ablaufverfolgungsfilters &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md).  
  
3.  Geben Sie das Ziel für die aufgezeichneten Ereignisdaten mit **sp_trace_create** an.  
  
 Ein Beispiel zum Verwenden gespeicherter Prozeduren der Ablaufverfolgung finden Sie unter [Erstellen einer Ablaufverfolgung &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).  
  
 **So legen Sie die Standardeinstellungen für Ablaufverfolgungsdefinitionen fest**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
 **So legen Sie die Standardeinstellungen für die Ablaufverfolgungsanzeige fest**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **So erstellen Sie eine Ablaufverfolgung**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [Transact-SQL](../sql-trace/create-a-trace-transact-sql.md)  
  
 **So fügen Sie einer Ablaufverfolgungsvorlage Ereignisse hinzu bzw. entfernen sie**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
