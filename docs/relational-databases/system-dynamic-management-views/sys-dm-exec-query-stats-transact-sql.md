---
title: sys. dm_exec_query_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_stats_TSQL
- dm_exec_query_stats
- sys.dm_exec_query_stats
- sys.dm_exec_query_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_stats dynamic management view
ms.assetid: eb7b58b8-3508-4114-97c2-d877bcb12964
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 23fd1a0c896436dad27ab771e2ed04c775938091
ms.sourcegitcommit: 1feba5a0513e892357cfff52043731493e247781
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2020
ms.locfileid: "77429014"
---
# <a name="sysdm_exec_query_stats-transact-sql"></a>sys.dm_exec_query_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt die zusammengefasste Leistungsstatistik für zwischengespeicherte Abfragepläne in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurück. Diese Sicht enthält eine Zeile pro Abfrageanweisung innerhalb des zwischengespeicherten Plans, und die Lebensdauer der Zeilen ist an den Plan selbst gebunden. Wenn ein Plan aus dem Cache entfernt wird, werden die entsprechenden Zeilen aus dieser Sicht entfernt.  
  
> [!NOTE]
> - Die Ergebnisse von **sys. dm_exec_query_stats** können sich bei jeder Ausführung unterscheiden, da die Daten nur abgeschlossene Abfragen widerspiegeln, und keine, die noch aktiv sind.
> - Um dies von oder [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]aus aufzurufen, verwenden Sie den Namen **sys. dm_pdw_nodes_exec_query_stats**.    

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**sql_handle**|**varbinary (64)**  |Ein Token, das den Batch oder die gespeicherte Prozedur eindeutig identifiziert, zu der die Abfrage gehört.<br /><br /> **sql_handle**können mit **statement_start_offset** und **statement_end_offset**zum Abrufen des SQL-Texts der Abfrage verwendet werden, indem die dynamische Verwaltungsfunktion **sys. dm_exec_sql_text** aufgerufen wird.|  
|**statement_start_offset**|**int**|Gibt die Startposition der Abfrage, die in der Zeile beschrieben wird, beginnend mit 0 im Text des zugehörigen persistenten Objekts oder Batchobjekts an (in Bytes).|  
|**statement_end_offset**|**int**|Gibt die Endposition der Abfrage, die in der Zeile beschrieben wird, beginnend mit 0 im Text des zugehörigen persistenten Objekts oder Batchobjekts an (in Bytes). Bei Versionen vor [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]gibt der Wert-1 das Ende des Batches an. Nachfolgende Kommentare sind nicht mehr enthalten.|  
|**plan_generation_num**|**BIGINT**|Eine Sequenznummer, anhand der nach einer Neukompilierung zwischen einzelnen Instanzen von Plänen unterschieden werden kann.|  
|**plan_handle**|**varbinary (64)**|Ein Token, das einen Abfrage Ausführungsplan für einen Batch eindeutig identifiziert, der ausgeführt wurde und dessen Plan sich im Plancache befindet oder gerade ausgeführt wird. Dieser Wert kann an die dynamische Verwaltungsfunktion [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md) übergeben werden, um den Abfrageplan abzurufen.<br /><br /> Ist immer 0x000, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**creation_time**|**datetime**|Der Zeitpunkt, zu dem der Plan kompiliert wurde.|  
|**last_execution_time**|**datetime**|Der Zeitpunkt, zu dem die Ausführung des Plans zuletzt gestartet wurde.|  
|**execution_count**|**BIGINT**|Die Anzahl von Planausführungen seit der letzten Kompilierung.|  
|**total_worker_time**|**BIGINT**|Die CPU-Gesamtzeit in Mikrosekunden (aber nur auf Millisekunden genau) für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> Wenn zahlreiche Ausführungen weniger als 1 Millisekunde dauern, wird **total_worker_time** bei nativ kompilierten gespeicherten Prozeduren u.U. nicht exakt angegeben.|  
|**last_worker_time**|**BIGINT**|Die CPU-Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für die letzte Ausführung des Plans. <sup>1</sup>|  
|**min_worker_time**|**BIGINT**|Die minimale CPU-Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine einzelne Ausführung dieses Plans. <sup>1</sup>|  
|**max_worker_time**|**BIGINT**|Maximale CPU-Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine einzelne Ausführung dieses Plans. <sup>1</sup>|  
|**total_physical_reads**|**BIGINT**|Die Gesamtanzahl physischer Lesevorgänge für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_physical_reads**|**BIGINT**|Die Anzahl physischer Lesevorgänge bei der letzten Ausführung des Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**min_physical_reads**|**BIGINT**|Die bisherige minimale Anzahl physischer Lesevorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_physical_reads**|**BIGINT**|Die bisherige maximale Anzahl physischer Lesevorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_logical_writes**|**BIGINT**|Die Gesamtanzahl logischer Schreibvorgänge für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_logical_writes**|**BIGINT**|Die Anzahl der Pufferpool Seiten, die während der zuletzt abgeschlossenen Ausführung des Plans in der Liste gespeichert wurden.<br /><br />Nachdem eine Seite gelesen wurde, wird die Seite nur bei der ersten Änderung geändert. Wenn eine Seite geändert wird, wird diese Zahl inkrementiert. Nachfolgende Änderungen einer bereits geänderten Seite wirken sich nicht auf diese Zahl aus.<br /><br />Diese Zahl ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.|  
|**min_logical_writes**|**BIGINT**|Die bisherige minimale Anzahl logischer Schreibvorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_logical_writes**|**BIGINT**|Die bisherige maximale Anzahl logischer Schreibvorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_logical_reads**|**BIGINT**|Die Gesamtanzahl logischer Lesevorgänge für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_logical_reads**|**BIGINT**|Die Anzahl logischer Lesevorgänge bei der letzten Ausführung des Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**min_logical_reads**|**BIGINT**|Die bisherige minimale Anzahl logischer Lesevorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_logical_reads**|**BIGINT**|Die bisherige maximale Anzahl logischer Lesevorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_clr_time**|**BIGINT**|Zeit in Mikrosekunden (aber nur auf Millisekunden genau), die in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR)-Objekten durch Ausführungen dieses Plans seit der Kompilierung verbraucht wurde. Die CLR-Objekte können gespeicherte Prozeduren, Funktionen, Trigger, Typen und Aggregate sein.|  
|**last_clr_time**|**BIGINT**|Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für die Ausführung in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR-Objekten während der letzten Ausführung dieses Plans. Die CLR-Objekte können gespeicherte Prozeduren, Funktionen, Trigger, Typen und Aggregate sein.|  
|**min_clr_time**|**BIGINT**|Minimale Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine einzelne Ausführung dieses Plans in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR-Objekten. Die CLR-Objekte können gespeicherte Prozeduren, Funktionen, Trigger, Typen und Aggregate sein.|  
|**max_clr_time**|**BIGINT**|Maximale Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine einzelne Ausführung dieses Plans in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR. Die CLR-Objekte können gespeicherte Prozeduren, Funktionen, Trigger, Typen und Aggregate sein.|  
|**total_elapsed_time**|**BIGINT**|Insgesamt verstrichene Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für abgeschlossene Ausführungen dieses Plans.|  
|**last_elapsed_time**|**BIGINT**|Verstrichene Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für die letzte abgeschlossene Ausführung dieses Plans.|  
|**min_elapsed_time**|**BIGINT**|Mindestens verstrichene Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine beliebige abgeschlossene Ausführung dieses Plans.|  
|**max_elapsed_time**|**BIGINT**|Maximal verstrichene Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine beliebige abgeschlossene Ausführung dieses Plans.|  
|**query_hash**|**Binär (8)**|Binärer Hashwert, der in der Abfrage berechnet wird und zum Identifizieren von Abfragen mit ähnlicher Logik verwendet wird. Sie können den Abfragehash verwenden, um die aggregierte Ressourcennutzung für Abfragen zu ermitteln, die sich nur durch Literalwerte unterscheiden.|  
|**query_plan_hash**|**Binär (8)**|Binärer Hashwert, der im Abfrageausführungsplan wird und zum Identifizieren ähnlicher Abfrageausführungspläne verwendet wird. Sie können diesen Abfrageplan-Hashwert verwenden, um die kumulierten Kosten für Abfragen mit ähnlichen Ausführungsplänen zu suchen.<br /><br /> Ist immer 0x000, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**total_rows**|**BIGINT**|Die Gesamtanzahl der von der Abfrage zurückgegebenen Zeilen. Darf nicht NULL sein.<br /><br /> Ist immer 0, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**last_rows**|**BIGINT**|Die Anzahl der bei der letzten Ausführung der Abfrage zurückgegebenen Zeilen. Darf nicht NULL sein.<br /><br /> Ist immer 0, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**min_rows**|**BIGINT**|Die minimale Anzahl von Zeilen, die von der Abfrage während einer Ausführung zurückgegeben wurden. Darf nicht NULL sein.<br /><br /> Ist immer 0, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**max_rows**|**BIGINT**|Maximale Anzahl von Zeilen, die von der Abfrage während einer Ausführung jemals zurückgegeben wurden. Darf nicht NULL sein.<br /><br /> Ist immer 0, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**statement_sql_handle**|**varbinary (64)**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> Wird nur mit Werten aufgefüllt, die ungleich NULL sind, wenn Abfragespeicher aktiviert ist und die Statistiken für diese bestimmte Abfrage sammelt.|  
|**statement_context_id**|**BIGINT**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> Wird nur mit Werten aufgefüllt, die ungleich NULL sind, wenn Abfragespeicher aktiviert ist und die Statistiken für diese bestimmte Abfrage sammelt.|  
|**total_dop**|**BIGINT**|Die Gesamtsumme der Parallelität, die dieser Plan seit der Kompilierung verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**last_dop**|**BIGINT**|Der Grad an Parallelität bei der letzten Ausführung dieses Plans. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**min_dop**|**BIGINT**|Der minimale Grad an Parallelität, den dieser Plan bei einer Ausführung bisher verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**max_dop**|**BIGINT**|Der maximale Grad an Parallelität, den dieser Plan bei einer Ausführung bisher verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**total_grant_kb**|**BIGINT**|Die Gesamtmenge der reservierten Arbeitsspeicher Zuweisung in KB, die dieser Plan seit der Kompilierung empfangen hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**last_grant_kb**|**BIGINT**|Die Menge der reservierten Arbeitsspeicher Zuweisung in KB, als dieser Plan das letzte Mal ausgeführt wurde. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**min_grant_kb**|**BIGINT**|Die Mindestanzahl reservierter Arbeitsspeicher Zuweisungen in KB, die dieser Plan während einer Ausführung erhalten hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**max_grant_kb**|**BIGINT**|Die maximale Menge an reserviertem Arbeitsspeicher in KB, die dieser Plan während einer Ausführung erhalten hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**total_used_grant_kb**|**BIGINT**|Die Gesamtmenge der reservierten Arbeitsspeicher Zuweisung in KB, die für diesen Plan seit der Kompilierung verwendet wurde. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**last_used_grant_kb**|**BIGINT**|Die Menge der verwendeten Arbeitsspeicher Zuweisung in KB, als dieser Plan das letzte Mal ausgeführt wurde. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**min_used_grant_kb**|**BIGINT**|Die minimale Menge an verwendeter Arbeitsspeicher Zuweisung in KB, die dieser Plan jemals während einer Ausführung verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**max_used_grant_kb**|**BIGINT**|Die maximale Menge an verwendeter Arbeitsspeicher Zuweisung in KB, die dieser Plan jemals während einer Ausführung verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**total_ideal_grant_kb**|**BIGINT**|Die Gesamtmenge der idealen Arbeitsspeicher Zuweisung in KB, die für diesen Plan seit der Kompilierung geschätzt wurde. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**last_ideal_grant_kb**|**BIGINT**|Die Menge der idealen Arbeitsspeicher Zuweisung in KB, als dieser Plan das letzte Mal ausgeführt wurde. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**min_ideal_grant_kb**|**BIGINT**|Die minimale Menge an idealen Arbeitsspeicher Zuweisungen in KB, die dieser Plan bei einer Ausführung jemals geschätzt hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**max_ideal_grant_kb**|**BIGINT**|Die maximale Menge an idealen Arbeitsspeicher Zuweisungen in KB, die dieser Plan bei einer Ausführung jemals geschätzt hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**total_reserved_threads**|**BIGINT**|Die Gesamtsumme der reservierten parallelen Threads, die dieser Plan je seit der Kompilierung verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**last_reserved_threads**|**BIGINT**|Die Anzahl der reservierten parallelen Threads, wenn dieser Plan das letzte Mal ausgeführt wurde. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**min_reserved_threads**|**BIGINT**|Die Mindestanzahl von reservierten parallelen Threads, die dieser Plan jemals während einer Ausführung verwendet hat.  Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**max_reserved_threads**|**BIGINT**|Die maximale Anzahl reservierter paralleler Threads, die dieser Plan jemals während einer Ausführung verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**total_used_threads**|**BIGINT**|Die Gesamtsumme der verwendeten parallelen Threads, die dieser Plan je seit der Kompilierung verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**last_used_threads**|**BIGINT**|Die Anzahl der bei der letzten Ausführung dieses Plans verwendeten parallelen Threads. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**min_used_threads**|**BIGINT**|Die Mindestanzahl von parallelen Threads, die dieser Plan jemals während einer Ausführung verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**max_used_threads**|**BIGINT**|Die maximale Anzahl von parallelen Threads, die dieser Plan jemals während einer Ausführung verwendet hat. Es ist immer 0, wenn eine Speicher optimierte Tabelle abgefragt wird.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.|  
|**total_columnstore_segment_reads**|**BIGINT**|Die Gesamtsumme der von der Abfrage gelesenen columnstore--Segmente. Darf nicht NULL sein.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**last_columnstore_segment_reads**|**BIGINT**|Die Anzahl der von der letzten Ausführung der Abfrage gelesenen columnstore--Segmente. Darf nicht NULL sein.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**min_columnstore_segment_reads**|**BIGINT**|Die Mindestanzahl von columnstore--Segmenten, die von der Abfrage während einer Ausführung gelesen wurden. Darf nicht NULL sein.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**max_columnstore_segment_reads**|**BIGINT**|Die maximale Anzahl von columnstore--Segmenten, die von der Abfrage während einer Ausführung gelesen wurden. Darf nicht NULL sein.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**total_columnstore_segment_skips**|**BIGINT**|Die Gesamtsumme der von der Abfrage übersprungenen columnstore--Segmente. Darf nicht NULL sein.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**last_columnstore_segment_skips**|**BIGINT**|Die Anzahl der columnstore--Segmente, die bei der letzten Ausführung der Abfrage übersprungen wurden. Darf nicht NULL sein.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**min_columnstore_segment_skips**|**BIGINT**|Die Mindestanzahl von columnstore--Segmenten, die von der Abfrage bei einer Ausführung jemals übersprungen wurden. Darf nicht NULL sein.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**max_columnstore_segment_skips**|**BIGINT**|Die maximale Anzahl von columnstore--Segmenten, die von der Abfrage während einer Ausführung jemals übersprungen wurden. Darf nicht NULL sein.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|
|**total_spills**|**BIGINT**|Die Gesamtanzahl der Seiten, die durch die Ausführung dieser Abfrage seit der Kompilierung übergegangen sind.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**BIGINT**|Die Anzahl der Seiten, die bei der letzten Ausführung der Abfrage übergegangen sind.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**BIGINT**|Die Mindestanzahl von Seiten, die diese Abfrage während einer einzelnen Ausführung jemals übergegangen ist.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**BIGINT**|Die maximale Anzahl von Seiten, die diese Abfrage während einer einzelnen Ausführung jemals übergegangen ist.<br /><br /> **Gilt für**: ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**pdw_node_id**|**int**|Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.<br /><br /> **Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]| 
|**total_page_server_reads**|**BIGINT**|Die Gesamtanzahl der Remote-Seiten Server Lesevorgänge, die von Ausführungen dieses Plans seit der Kompilierung durchgeführt wurden.<br /><br /> **Gilt für:** Azure SQL-Daten Bank hyperskalierung |  
|**last_page_server_reads**|**BIGINT**|Anzahl von Lesevorgängen für Remote Seiten Server, die bei der letzten Ausführung des Plans ausgeführt wurden.<br /><br /> **Gilt für:** Azure SQL-Daten Bank hyperskalierung |  
|**min_page_server_reads**|**BIGINT**|Die Mindestanzahl von Lesevorgängen für Remote Seiten Server, die dieser Plan jemals während einer einzelnen Ausführung ausgeführt hat.<br /><br /> **Gilt für:** Azure SQL-Daten Bank hyperskalierung |  
|**max_page_server_reads**|**BIGINT**|Maximale Anzahl von Lesevorgängen für Remote Seiten Server, die dieser Plan jemals während einer einzelnen Ausführung ausgeführt hat.<br /><br /> **Gilt für:** Azure SQL-Daten Bank hyperskalierung |  
> [!NOTE]
> <sup>1</sup> wenn die Statistik Sammlung für System intern kompilierte gespeicherte Prozeduren aktiviert ist, wird die workerzeit in Millisekunden erfasst. Wenn die Abfrage in weniger als einer Millisekunde ausgeführt wird, ist der Wert 0.  
  
## <a name="permissions"></a>Berechtigungen  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ist die `VIEW SERVER STATE` -Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die `VIEW DATABASE STATE` -Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   
   
## <a name="remarks"></a>Bemerkungen  
 Statistiken in der Sicht werden nach Abschluss einer Abfrage aktualisiert.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-finding-the-top-n-queries"></a>A. Suchen der TOP-N-Abfragen  
 Das folgende Beispiel gibt Informationen über die „Top-Fünf“-Abfragen gemessen an durchschnittlicher CPU-Zeit zurück. Die Abfragen werden in diesem Beispiel anhand des Abfragehashes aggregiert, sodass logisch identische Abfragen basierend auf dem kumulierten Ressourcenverbrauch gruppiert werden.  
  
```sql  
SELECT TOP 5 query_stats.query_hash AS "Query Hash",   
    SUM(query_stats.total_worker_time) / SUM(query_stats.execution_count) AS "Avg CPU Time",  
    MIN(query_stats.statement_text) AS "Statement Text"  
FROM   
    (SELECT QS.*,   
    SUBSTRING(ST.text, (QS.statement_start_offset/2) + 1,  
    ((CASE statement_end_offset   
        WHEN -1 THEN DATALENGTH(ST.text)  
        ELSE QS.statement_end_offset END   
            - QS.statement_start_offset)/2) + 1) AS statement_text  
     FROM sys.dm_exec_query_stats AS QS  
     CROSS APPLY sys.dm_exec_sql_text(QS.sql_handle) as ST) as query_stats  
GROUP BY query_stats.query_hash  
ORDER BY 2 DESC;  
```  
  
### <a name="b-returning-row-count-aggregates-for-a-query"></a>B. Zurückgeben der aggregierten Zeilenanzahlen für eine Abfrage  
 Im folgenden Beispiel werden Informationen zu aggregierten Zeilenanzahlen (Gesamtanzahl der Zeilen, minimale Anzahl der Zeilen, maximale Anzahl der Zeilen und letzte Zeilen) für Abfragen zurückgegeben.  
  
```sql  
SELECT qs.execution_count,  
    SUBSTRING(qt.text,qs.statement_start_offset/2 +1,   
                 (CASE WHEN qs.statement_end_offset = -1   
                       THEN LEN(CONVERT(nvarchar(max), qt.text)) * 2   
                       ELSE qs.statement_end_offset end -  
                            qs.statement_start_offset  
                 )/2  
             ) AS query_text,   
     qt.dbid, dbname= DB_NAME (qt.dbid), qt.objectid,   
     qs.total_rows, qs.last_rows, qs.min_rows, qs.max_rows  
FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS qt   
WHERE qt.text like '%SELECT%'   
ORDER BY qs.execution_count DESC;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Dynamische Verwaltungs Sichten und-Funktionen im Zusammenhang mit der Ausführung &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)    
[sys. dm_exec_sql_text &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)    
[sys. dm_exec_query_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys. dm_exec_procedure_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)     
[sys. dm_exec_trigger_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)     
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  


