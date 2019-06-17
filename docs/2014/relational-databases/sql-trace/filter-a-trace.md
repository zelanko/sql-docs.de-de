---
title: Filtern einer Ablaufverfolgung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- events [SQL Server], filters
- filters [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 019c10ab-68f6-4e40-a5e8-735b2e1270db
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 381007cb26f74cdf945900436d8a9fcea5a4ef39
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62714717"
---
# <a name="filter-a-trace"></a>Filtern einer Ablaufverfolgung
  Durch Filter werden die in einer Ablaufverfolgung aufgezeichneten Ereignisse eingeschränkt. Ist kein Filter eingerichtet, werden alle Ereignisse der ausgewählten Ereignisklassen in der Ablaufverfolgungsausgabe zurückgegeben. Wenn Sie z. B. die Benutzernamen von Windows in der Ablaufverfolgung auf bestimmte Benutzer beschränken, werden die Ausgabedaten auf die für Sie interessanten Benutzer reduziert.  
  
 Es ist nicht obligatorisch, einen Filter für eine Ablaufverfolgung festzulegen. Durch einen Filter wird jedoch der bei der Ablaufverfolgung entstehende Verarbeitungsaufwand verringert. Durch einen Filter werden genauer ausgewählte Daten zurückgegeben, wodurch sich Leistungsanalyse und -überwachung vereinfachen.  
  
 Um die bei einer Ablaufverfolgung aufgezeichneten Ereignisdaten zu filtern, wählen Sie die entsprechenden Kriterien für das Ablaufverfolgungsereignis aus, sodass bei der Ablaufverfolgung nur die benötigten Daten zurückgegeben werden. Sie können beispielsweise festlegen, dass die Überwachung der Aktivität einer bestimmten Anwendung bei der Ablaufverfolgung eingeschlossen oder ausgeschlossen wird.  
  
> [!NOTE]  
>  Wenn Ablaufverfolgungen durch [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] erstellt werden, werden die Profiler-Aktivitäten standardmäßig herausgefiltert.  
  
 Ein weiteres Beispiel ist die Überwachung von Abfragen, um die Batches zu ermitteln, deren Ausführung am längsten dauert. Hier können Sie die Kriterien für die Ereignisablaufverfolgung so festlegen, dass ausschließlich jene Batches überwacht werden, deren Ausführung länger als 30 Sekunden dauert (ein CPU-Mindestwert von 30.000 Millisekunden).  
  
## <a name="filter-creation-guidelines"></a>Richtlinien für die Erstellung von Filtern  
 Um eine Ablaufverfolgung zu filtern, gehen Sie im Allgemeinen nach der folgenden Schrittfolge vor.  
  
1.  Entscheiden Sie, welche Ereignisse in die Ablaufverfolgung eingeschlossen werden sollen.  
  
2.  Bestimmen Sie die Daten und Datenspalten, die die benötigten Informationen enthalten.  
  
3.  Bestimmen Sie eine Untergruppe der benötigten Daten, und definieren Sie auf der Grundlage dieser Datenuntergruppe Filter.  
  
 Beispielsweise möchten Sie nur Ereignisse verfolgen, die länger als eine bestimmte Zeit dauern. In diesem Fall können Sie eine Ablaufverfolgung erstellen, die Ereignisse umfasst, bei denen die Datenspalte **Duration** größer ist als 300 Millisekunden. Ereignisse, deren Ausführung weniger als 300 Millisekunden dauert, werden bei der Ablaufverfolgung nicht berücksichtigt.  
  
 Zur Erstellung von Filtern können Sie gespeicherte Prozeduren aus SQL Server Profiler oder Transact-SQL verwenden.  
  
 **So filtern Sie Ereignisse in einer Ablaufverfolgungsvorlage**  
  
 [Filtern von Ereignissen in einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
 [Festlegen eines Ablaufverfolgungsfilters &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)  
  
 **So ändern Sie Filter**  
  
 [Ändern eines Filters &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
 Ob Filter verfügbar sind, ist von der Datenspalte abhängig. Einige Datenspalten können nicht gefiltert werden. Filterbare Datenspalten können nur durch bestimmte relationale Operatoren gefiltert werden, wie Sie der folgenden Tabelle entnehmen können.  
  
|Relationaler Operator|Operatorsymbol|Description|  
|-------------------------|---------------------|-----------------|  
|Wie|Wie|Die Ereignisablaufverfolgungsdaten müssen dem eingegebenen Text entsprechen. Mehrere Werte sind zulässig.|  
|Nicht wie|Nicht wie|Die Ereignisablaufverfolgungsdaten dürfen nicht dem eingegebenen Text entsprechen. Mehrere Werte sind zulässig.|  
|Ist gleich|=|Die Ereignisablaufverfolgungsdaten müssen dem eingegebenen Wert entsprechen. Mehrere Werte sind zulässig.|  
|Ungleich|<>|Die Ereignisablaufverfolgungsdaten dürfen dem eingegebenen Wert nicht entsprechen. Mehrere Werte sind zulässig.|  
|Größer als|>|Die Ereignisablaufverfolgungsdaten müssen größer als der eingegebene Wert sein.|  
|Größer als oder gleich|>=|Die Ereignisablaufverfolgungsdaten müssen mindestens so groß wie der eingegebene Wert sein.|  
|Kleiner als|<|Die Ereignisablaufverfolgungsdaten müssen kleiner als der eingegebene Wert sein.|  
|Kleiner als oder gleich|<=|Die Ereignisablaufverfolgungsdaten dürfen höchstens so groß wie der eingegebene Wert sein.|  
  
 In der folgenden Tabelle sind die filterbaren Datenspalten und die verfügbaren relationalen Operatoren aufgelistet.  
  
|Datenspalten|Relationale Operatoren|  
|------------------|--------------------------|  
|**ApplicationName**|LIKE, NOT LIKE|  
|**BigintData1**|=, <>, >=, <=|  
|**BigintData2**|=, <>, >=, <=|  
|**BinaryData**|Verwenden Sie [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um die Ereignisse in dieser Datenspalte zu filtern. Weitere Informationen finden Sie unter [Filtern von Ablaufverfolgungen mit SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**ClientProcessID**|=, <>, >=, <=|  
|**ColumnPermissions**|=, <>, >=, <=|  
|**CPU**|=, <>, >=, <=|  
|**DatabaseID**|=, <>, >=, <=|  
|**DatabaseName**|LIKE, NOT LIKE|  
|**DBUserName**|LIKE, NOT LIKE|  
|**Dauer**|=, <>, >=, \<=|  
|**EndTime**|>=, <=|  
|**Fehler**|=, <>, >=, <=|  
|**EventSubClass**|=, <>, >=, <=|  
|**FileName**|LIKE, NOT LIKE|  
|**GUID**|Verwenden Sie [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um die Ereignisse in dieser Datenspalte zu filtern. Weitere Informationen finden Sie unter [Filtern von Ablaufverfolgungen mit SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**Handle**|=, <>, >=, <=|  
|**HostName**|LIKE, NOT LIKE|  
|**IndexID**|=, <>, >=, <=|  
|**IntegerData**|=, <>, >=, <=|  
|**IntegerData2**|=, <>, >=, <=|  
|**IsSystem**|=, <>, >=, <=|  
|**LineNumber**|=, <>, >=, <=|  
|**LinkedServerName**|LIKE, NOT LIKE|  
|**LoginName**|LIKE, NOT LIKE|  
|**LoginSid**|Verwenden Sie [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um die Ereignisse in dieser Datenspalte zu filtern. Weitere Informationen finden Sie unter [Filtern von Ablaufverfolgungen mit SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**MethodName**|LIKE, NOT LIKE|  
|**Mode**|=, <>, >=, <=|  
|**NestLevel**|=, <>, >=, <=|  
|**NTDomainName**|LIKE, NOT LIKE|  
|**NTUserName**|LIKE, NOT LIKE|  
|**ObjectID**|=, <>, >=, <=|  
|**ObjectID2**|=, <>, >=, <=|  
|**ObjectName**|LIKE, NOT LIKE|  
|**ObjectType**|=, <>, >=, <=|  
|**Offset**|=, <>, >=, <=|  
|**OwnerID**|=, <>, >=, <=|  
|**OwnerName**|LIKE, NOT LIKE|  
|**ParentName**|LIKE, NOT LIKE|  
|**Berechtigungen**|=, <>, >=, <=|  
|**ProviderName**|LIKE, NOT LIKE|  
|**Reads**|=, <>, >=, <=|  
|**RequestID**|=, <>, >=, <=|  
|**RoleName**|LIKE, NOT LIKE|  
|**RowCounts**|=, <>, >=, <=|  
|**SessionLoginName**|LIKE, NOT LIKE|  
|**Severity**|=, <>, >=, <=|  
|**SourceDatabaseID**|=, <>, >=, <=|  
|**SPID**|=, <>, >=, \<=|  
|**SqlHandle**|Verwenden Sie [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um die Ereignisse in dieser Datenspalte zu filtern. Weitere Informationen finden Sie unter [Filtern von Ablaufverfolgungen mit SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**StartTime**|>=, <=|  
|**Zustand**|=, <>, >=, <=|  
|**Success**|=, <>, >=, <=|  
|**TargetLoginName**|LIKE, NOT LIKE|  
|**TargetLoginSid**|Verwenden Sie [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um die Ereignisse in dieser Datenspalte zu filtern. Weitere Informationen finden Sie unter [Filtern von Ablaufverfolgungen mit SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**TargetUserName**|LIKE, NOT LIKE|  
|**TextData** <sup>1</sup>|LIKE, NOT LIKE|  
|**TransactionID**|=, <>, >=, <=|  
|**Typ**|=, <>, >=, <=|  
|**Writes**|=, <>, >=, <=|  
|**XactSequence**|=, <>, >=, <=|  
  
 <sup>1</sup> Wenn die Ablaufverfolgung für Ereignisse aus der **Osql** Hilfsprogramm oder **Sqlcmd** Dienstprogramm immer angefügt **%** Filtern in der **TextData**  Datenspalte.  
  
 Die SQL-Ablaufverfolgung nimmt aus Gründen der Sicherheit automatisch alle Informationen aus sicherheitsbezogenen gespeicherten Prozeduren von der Ablaufverfolgung aus, die sich auf Kennwörter auswirken. Dieser Sicherheitsmechanismus kann nicht konfiguriert werden und ist immer wirksam. Auf diese Weise wird die Aufzeichnung von Kennwörtern durch Benutzer verhindert, die normalerweise berechtigt sind, Ablaufverfolgungen für alle Aktivitäten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auszuführen.  
  
 Die folgenden sicherheitsbezogenen Prozeduren werden zwar überwacht, es wird jedoch keine Ausgabe in die **TextData** -Datenspalte geschrieben:  
  
 [sp_addapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addapprole-transact-sql)  
  
 [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)  
  
 [sp_adddistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql)  
  
 [sp_adddistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql)  
  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)  
  
 [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)  
  
 [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)  
  
 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)  
  
 [sp_addremotelogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql)  
  
 [sp_addsubscriber &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql)  
  
 [sp_approlepassword &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-approlepassword-transact-sql)  
  
 [sp_changedistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql)  
  
 [sp_changesubscriber &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql)  
  
 [sp_dsninfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dsninfo-transact-sql)  
  
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)  
  
 [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)  
  
 [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)  
  
 [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)  
  
  
