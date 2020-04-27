---
title: Verbessern der Leistung von Volltextindizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], full-text search
- full-text queries [SQL Server], performance
- crawls [full-text search]
- full-text indexes [SQL Server], performance
- full-text search [SQL Server], performance
- batches [SQL Server], full-text search
ms.assetid: ef39ef1f-f0b7-4582-8e9c-31d4bd0ad35d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 42aa89a111697f17f23613761eeeb462494bdd27
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011261"
---
# <a name="improve-the-performance-of-full-text-indexes"></a>Verbessern der Leistung von Volltextindizes
  Die Leistung für Volltextindizes und Volltextabfragen wird von den Hardwareressourcen wie Arbeitsspeicher, Datenträgergeschwindigkeit, CPU-Geschwindigkeit und Computerarchitektur beeinflusst.  
  
##  <a name="common-causes-of-performance-issues"></a><a name="causes"></a>Häufige Ursachen für Leistungsprobleme  
 Der Hauptgrund für eine eingeschränkte Leistung beim Erstellen von Volltextindizes sind Einschränkungen bei den Hardwareressourcen:  
  
-   Wenn die CPU-Nutzung des Filterdaemon-Hostprozesses (fdhost.exe) oder des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozesses (sqlservr.exe) fast 100 % beträgt, dann ist die CPU der Engpass.  
  
-   Wenn die durchschnittliche Warteschlangenlänge des Datenträgers zweimal so groß wie die Anzahl von Leseköpfen ist, dann besteht ein Engpass auf dem Datenträger. Die erste Problemumgehung ist das Erstellen von Volltextkatalogen, die getrennt von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankendateien und -protokollen sind. Platzieren Sie Protokolle, die Datenbankdateien und Volltextkataloge auf getrennten Datenträgern. Kaufen Sie schnellere Datenträger, und verwenden Sie RAID, um die Indexleistung zu verbessern.  
  
-   Wenn ein Mangel an physischem Speicher (3-GB-Grenze) besteht, kann ggf. der Arbeitsspeicher der Engpass sein. Einschränkungen des physischen Arbeitsspeichers sind auf allen Systemen möglich, und auf 32-Bit-Systemen kann knapper virtueller Arbeitsspeicher die Volltextindizierung verlangsamen.  
  
    > [!NOTE]  
    >  Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] kann die Volltext-Engine den AWE-Speicher verwenden, weil die Volltext-Engine Teil von sqlservr.exe ist.  
  
 Wenn auf dem System keine Hardwareengpässe vorhanden sind, hängt die Indizierungsleistung der Volltextsuche vor allem von folgenden Faktoren ab:  
  
-   Wie lange das Erstellen von Volltextbatches durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dauert.  
  
-   Wie schnell der Filterdaemon diese Batches verarbeiten kann.  
  
> [!NOTE]  
>  Im Gegensatz zur vollständigen Auffüllung eignet sich die inkrementelle, manuelle und automatische Änderungsnachverfolgung der Auffüllung nicht zum Maximieren von Hardwareressourcen, um schnellere Geschwindigkeiten zu erzielen. Deshalb können diese Optimierungsvorschläge nicht die Leistung für Volltextindizes verbessern.  
  
 Nach dem Ende einer Auffüllung wird ein abschließender Mergeprozess ausgelöst, der die Indexfragmente zu einem Mastervolltextindex zusammenführt. Dies ermöglicht eine verbesserte Abfrageleistung, da statt mehrerer Indexfragmente nur der Masterindex abgefragt werden muss. Zudem können bessere Bewertungsstatistiken zum Erstellen der Relevanzrangfolge verwendet werden. Beachten Sie, dass die Masterzusammenführung E/A-intensiv sein kann, da beim Zusammenführen der Indexfragmente umfangreiche Datenmengen geschrieben und gelesen werden müssen. Eingehende Abfragen werden dadurch jedoch nicht blockiert.  
  
> [!IMPORTANT]  
>  Die Masterzusammenführung einer großen Datenmenge kann eine Transaktion mit langer Ausführungszeit erzeugen und das Abschneiden des Transaktionsprotokolls während des Prüfpunkts verzögern. In diesem Fall kann das Transaktionsprotokoll unter dem vollständigen Wiederherstellungsmodell erheblich anwachsen. Sie sollten sicherstellen, dass das Transaktionsprotokoll vor dem Reorganisieren eines großen Volltextindexes in einer Datenbank, die das vollständige Wiederherstellungsmodell verwendet, genügend Speicherplatz für eine Transaktion mit langer Laufzeit bietet. Weitere Informationen finden Sie unter [Verwalten der Größe der Transaktionsprotokolldatei](../logs/manage-the-size-of-the-transaction-log-file.md).  
  
  
  
##  <a name="tuning-the-performance-of-full-text-indexes"></a><a name="tuning"></a>Optimieren der Leistung von voll Text Indizes  
 Sie können die Leistung Ihrer Volltextindizes mit den folgenden bewährten Methoden maximieren:  
  
-   Um alle Prozessoren oder Kerne maximal zu verwenden, legen Sie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)'`max full-text crawl ranges`' auf die Anzahl der CPUs im System fest. Informationen zu dieser Konfigurationsoption finden Sie unter [Max. Bereich für Volltextdurchforstung (Serverkonfigurationsoption)](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md).  
  
-   Stellen Sie sicher, dass die Basistabelle einen gruppierten Index besitzt. Verwenden Sie einen ganzzahligen Datentyp für die erste Spalte des gruppierten Index. Vermeiden Sie das Verwenden von GUIDs in der ersten Spalte des gruppierten Index. Eine Mehrbereichsauffüllung für einen gruppierten Index kann die höchste Auffüllungsgeschwindigkeit erzielen. Es ist ratsam, für die Spalte, die als Volltextschlüssel dient, einen ganzzahligen Datentyp zu verwenden.  
  
-   Aktualisieren Sie die Statistiken der Basistabelle mithilfe der [UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql) -Anweisung. Noch wichtiger ist das Aktualisieren der Statistik für den gruppierten Index bzw. des Volltextschlüssels für eine vollständige Auffüllung. Dies unterstützt eine Mehrbereichsauffüllung beim Erzeugen guter Partitionen in der Tabelle.  
  
-   Erstellen Sie einen zweiten Index in einer `timestamp`-Spalte, wenn Sie die Leistung der inkrementellen Auffüllung verbessern möchten.  
  
-   Bevor Sie eine vollständige Auffüllung auf einem großen Multi-CPU-Computer ausführen, sollten Sie die Größe des Pufferpools vorübergehend einschränken, indem Sie den `max server memory`-Wert so festlegen, dass noch genug Speicher für den fdhost.exe-Prozess und die Betriebssystemprozesse verfügbar ist. Weitere Informationen finden Sie unter "Schätzen der Arbeitsspeicheranforderungen des Filterdaemon-Hostprozesses (fdhost.exe)" weiter unten in diesem Thema.  
  
  
  
##  <a name="troubleshooting-the-performance-of-full-populations"></a><a name="full"></a>Problembehandlung bei vollständigen Auffüllungen  
 Leistungsprobleme diagnostizieren Sie, indem Sie die Protokolle für den Volltextcrawl überprüfen. Informationen zu Durchforstungsprotokollen finden Sie unter [Auffüllen von Volltextindizes](../indexes/indexes.md).  
  
 Es ist ratsam, bei der Problembehandlung die folgende Reihenfolge einzuhalten, falls die Leistung der vollständigen Auffüllungen nicht zufriedenstellend ist.  
  
### <a name="physical-memory-usage"></a>Verwendung des physischen Speichers  
 Während einer Volltextauffüllung ist es möglich, dass fdhost.exe oder sqlservr.exe viel Arbeitsspeicher beansprucht oder nicht genügend Arbeitsspeicher vorhanden ist. Wenn das Protokoll der Volltextdurchforstung zeigt, dass fdhost.exe häufig neu gestartet oder dass Fehlercode 8007008 zurückgegeben wird, bedeutet dies, dass für einen der Prozesse kein Speicher mehr verfügbar ist. Wenn fdhost.exe Dumps erzeugt, insbesondere auf großen Multi-CPU-Computern, steht möglicherweise nicht genügend Arbeitsspeicher zur Verfügung.  
  
> [!NOTE]  
>  Informationen zu Arbeitsspeicherpuffern, die von einer Volltextdurchforstung verwendet werden, finden Sie unter [sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql).  
  
 Die folgenden Ursachen sind möglich:  
  
-   Wenn der physische Speicher, der während einer vollständigen Auffüllung verfügbar ist, 0 (null) ist, kann es sein, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Pufferpool den größten Teil des physischen Speichers des Systems belegt.  
  
     Der Prozess "sqlservr.exe" versucht, den gesamten verfügbaren Speicher für den Pufferpool bis zum konfigurierten maximalen Serverarbeitsspeicher für sich zu beanspruchen. Wenn die `max server memory`-Zuordnung zu groß ist, können Probleme aufgrund ungenügenden Arbeitsspeichers und Fehler bei der Zuordnung von gemeinsam genutzten Speicherbereich für den Prozess "fdhost.exe" auftreten.  
  
    > [!NOTE]  
    >  Während einer Volltextauffüllung können auf Multi-CPU-Computern Konflikte zwischen fdhost.exe oder sqlservr.exe um den Pufferpoolarbeitsspeicher auftreten. Der daraus resultierende Mangel an gemeinsam genutztem Speicherbereich verursacht Batchwiederholungen, Arbeitsspeicherüberlastung und Dumps durch den Prozess "fdhost.exe".  
  
     Sie können dieses Problem beheben, indem Sie den Wert `max server memory` des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Pufferpools entsprechend anpassen. Weitere Informationen finden Sie unter "Schätzen der Arbeitsspeicheranforderungen des Filterdaemon-Hostprozesses (fdhost.exe)" weiter unten in diesem Thema. Möglicherweise ist es auch hilfreich, die verwendete Batchgröße für die Volltextindizierung zu reduzieren.  
  
-   Ein Auslagerungsproblem  
  
     Eine zu kleine Auslagerungsdatei, z. B. wenn ein System über eine kleine Auslagerungsdatei mit eingeschränkter Vergrößerung verfügt, kann ebenfalls dazu führen, dass fdhost.exe oder sqlservr.exe nicht mehr auf genügend Arbeitsspeicher zugreifen können.  
  
     Wenn die Crawlprotokolle keine speicherbezogenen Fehler anzeigen, ist die Leistung wahrscheinlich aufgrund zu vieler Auslagerungen beeinträchtigt.  
  
  
  
### <a name="estimating-the-memory-requirements-of-the-filter-daemon-host-process-fdhostexe"></a>Schätzen der Arbeitsspeicheranforderungen des Filterdaemon-Hostprozesses (fdhost.exe)  
 Der vom fdhost.exe-Prozess für eine Auffüllung benötigte Arbeitsspeicher hängt hauptsächlich von den verwendeten Volltext-Crawlbereichen, der Größe des Inbound Shared Memory (ISM) und der maximalen Anzahl von ISM-Instanzen ab.  
  
 Der vom Filterdaemonhost verwendete Arbeitsspeicher (in Bytes) kann mit der folgenden Formel ungefähr geschätzt werden:  
  
 *number_of_crawl_ranges* \`ism_size "*max_outstanding_isms* \* 2  
  
 Die Standardwerte der Variablen in der vorangehenden Formel lauten wie folgt:  
  
|**Variable**|**Standardwert**|  
|------------------|-----------------------|  
|*number_of_crawl_ranges*|Die Anzahl der CPUs|  
|*ism_size*|1 MB für x86-Computer<br /><br /> 4 MB, 8 MB oder 16 MB für x64-Computer, abhängig vom gesamten physischen Arbeitsspeicher|  
|*max_outstanding_isms*|25 für x86-Computer<br /><br /> 5 für x64-Computer|  
  
 Die folgende Tabelle enthält Richtlinien zum Schätzen der Arbeitsspeicheranforderungen von fdhost.exe. Die Formeln in dieser Tabelle verwenden die folgenden Werte:  
  
-   *F*, eine Schätzung des Arbeitsspeichers, den „fdhost.exe“ (in MB) benötigt.  
  
-   *T*, der gesamte physische Speicher, der für das System (in MB) verfügbar ist.  
  
-   *M*, die optimale `max server memory` Einstellung.  
  
> [!IMPORTANT]  
>  Wichtige Informationen zu den Formeln finden Sie unten unter <sup>1</sup>, <sup>2</sup>und <sup>3</sup>.  
  
|Plattform|Schätzen der Arbeitsspeicher Anforderungen von "f. exe" in MB-*F*<sup>1</sup>|Formel zum Berechnen des maximalen Server Arbeitsspeichers-*M*<sup>2</sup>|  
|--------------|---------------------------------------------------------------------|---------------------------------------------------------------|  
|x86|_F_ **=** _Anzahl der_ Durchforstungs Bereiche **&#42;** 50|_M_ **= minimal (** _T_ **,** 2000 **)-*`F`* ** 500|  
|x64|_F_ **=** _Anzahl der_ Durchforstungs Bereiche **&#42;** 10 **&#42;** 8|_M_ **=** _T_ T **-** _F_ F **-** 500|  
  
 <sup>1</sup> wenn mehrere vollständige Auffüllungen ausgeführt werden, berechnen Sie die Arbeitsspeicher Anforderungen von "sdhost. exe" separat, als *F1*, *F2*usw. Berechnen Sie anschließend *M* als _T_**-** sigma **(**_F_i **)**.  
  
 <sup>2</sup> 500 MB ist eine Schätzung des Arbeitsspeichers, der von anderen Prozessen im System benötigt wird. Wenn das System noch weitere Aufgaben durchführt, sollten Sie diesen Wert entsprechend erhöhen.  
  
 <sup>3</sup> . für x64-Plattformen wird *ism_size* als 8 MB angenommen.  
  
 **Beispiel: Schätzen der Arbeitsspeicheranforderungen von "fdhost.exe"**  
  
 Dieses Beispiel gilt für einen AMD64-Computer mit 8 GB Arbeitsspeicher und 4 Dual Core-Prozessoren. Die erste Berechnung schätzt den Speicher, der von „fdhost.exe“ benötigt wird: *F*. Die Anzahl der Durchforstungsbereiche beträgt `8`.  
  
 `F = 8*10*8=640`  
  
 Die nächste Berechnung erhält den optimalen Wert für `max server memory` - *M*. *T*Der gesamte auf diesem System verfügbare physische Arbeitsspeicher in MB-*T*- `8192`ist.  
  
 `M = 8192-640-500=7052`  
  
 **Beispiel: Festlegen von "max server memory"**  
  
 In diesem Beispiel werden die Anweisungen [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) und [RECONFIGURE](/sql/t-sql/language-elements/reconfigure-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] verwendet `max server memory` , um auf den Wert festzulegen, der im vorherigen `7052`Beispiel für *M* berechnet wurde:  
  
```  
USE master;  
GO  
EXEC sp_configure 'max server memory', 7052;  
GO  
RECONFIGURE;  
GO  
```  
  
 **So legen Sie die Konfigurationsoption "max server memory" fest**  
  
-   [Serverkonfigurationsoptionen für den Serverarbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
  
### <a name="factors-that-can-reduce-cpu-consumption"></a>Faktoren, die den CPU-Verbrauch reduzieren können  
 Es ist wahrscheinlich, dass die Leistung von vollständigen Auffüllungen nicht optimal ist, wenn der mittlere CPU-Verbrauch weniger als 30 Prozent beträgt. In diesem Abschnitt werden einige Faktoren behandelt, die sich auf den CPU-Verbrauch auswirken.  
  
-   Langes Warten auf Seiten  
  
     Um herauszufinden, ob die Wartezeit für Seiten hoch ist, führen Sie die folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung aus:  
  
    ```  
    Execute SELECT TOP 10 * FROM sys.dm_os_wait_stats ORDER BY wait_time_ms DESC;  
    ```  
  
     In der folgenden Tabelle sind die relevanten Wartetypen aufgeführt.  
  
    |Wartetyp|Beschreibung|Mögliche Lösung|  
    |---------------|-----------------|-------------------------|  
    |PAGEIO_LATCH_SH (_EX oder _UP)|Dies kann auf einen E/A-Engpass hinweisen. In diesem Fall ist normalerweise auch eine hohe durchschnittliche Warteschlangenlänge des Datenträgers zu erkennen.|Sie können den E/A-Engpass ggf. reduzieren, indem Sie den Volltextindex in eine andere Dateigruppe auf einem anderen Datenträger verschieben.|  
    |PAGELATCH_EX (oder _UP)|Dies kann auf eine hohe Zahl von Konflikten zwischen Threads hinweisen, die versuchen, in dieselbe Datenbankdatei zu schreiben.|Diese Konflikte können ggf. verringert werden, indem Sie Dateien der Dateigruppe hinzufügen, auf der sich der Volltextindex befindet.|  
  
     Weitere Informationen finden Sie unter [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).  
  
-   Ineffizienzen beim Durchsuchen der Basistabelle  
  
     Eine vollständige Auffüllung durchsucht die Basistabelle, um Batches zu erzeugen. Dieses Durchsuchen der Tabelle kann in den folgenden Szenarios ineffizient sein:  
  
    -   Wenn die Basistabelle über einen hohen Prozentsatz an Außerhalb-Spalten (out-of-row) verfügt, für die eine Volltextindizierung durchgeführt wird, kann das Durchsuchen der Basistabelle zum Erzeugen von Batches den Engpass bewirken. In diesem Fall kann es helfen, die kleineren Daten mithilfe von `varchar(max)` oder `nvarchar(max)` in die Zeilen zu verschieben.  
  
    -   Wenn die Basistabelle stark fragmentiert ist, kann das Durchsuchen ggf. ineffizient sein. Informationen zur Berechnung von Außerhalb-Spalten-Daten und zur Indexfragmentierung finden Sie unter [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql) und [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).  
  
         Um die Fragmentierung zu reduzieren, können Sie den gruppierten Index neu organisieren oder neu erstellen. Weitere Informationen finden Sie unter [Neuorganisieren und Neuerstellen von Indizes](../indexes/reorganize-and-rebuild-indexes.md).  
  
  
  
##  <a name="troubleshooting-slow-indexing-performance-due-to-filters"></a><a name="filters"></a>Problembehandlung bei langsamer Indizierungs Leistung aufgrund von Filtern  
 Beim Auffüllen eines Volltextindexes werden von der Volltext-Engine zwei Arten von Filtern verwendet: Multithread-Filter und Filter mit einem einzigen Thread. Einige Dokumente, wie z. B. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word-Dokumente, werden mit einem Multithreadfilter gefiltert. Andere Dokumente, wie z. B. Adobe Acrobat PDF-Dokumente (Portable Document Format), werden hingegen mit einem Filter mit einem einzigen Thread gefiltert.  
  
 Aus Sicherheitsgründen werden Filter mit Filterdaemon-Hostprozessen geladen. Eine Serverinstanz verwendet einen Multithreadprozess für alle Multithreadfilter und einen Singlethreadprozess für alle Filter mit einem einzigen Thread. Wenn in einem Dokument, für das ein Multithreadfilter verwendet wird, ein Dokument eingebettet ist, für das ein Filter mit einem einzigen Thread verwendet wird, startet die Volltext-Engine einen Singlethreadprozess für das eingebettete Dokument. Beispiel: Bei einem Word-Dokument, das ein PDF-Dokument enthält, verwendet die Volltext-Engine einen Multithreadprozess für den Inhalt des Word-Dokuments und einen Singlethreadprozess für den Inhalt des PDF-Dokuments. Ein Filter mit einem einzigen Thread funktioniert in dieser Umgebung jedoch möglicherweise nicht ordnungsgemäß und kann die Stabilität des Filterprozesses gefährden. Unter bestimmten Umständen mit vielen eingebetteten Dokumenten kann dies zum Absturz des Filterprozesses führen. In diesem Fall verbindet die Volltext-Engine alle Dokumente, bei denen Fehler auftraten (z. B. ein Word-Dokument mit eingebettetem PDF-Inhalt), erneut mit dem Singlethread-Filterprozess. Kommt dies häufig vor, hat das eine Leistungsminderung des Volltextindizierungsprozesses zur Folge.  
  
 Sie müssen den Filter für das Containerdokument (hier das Word-Dokument) als Filter mit einem einzigen Thread kennzeichnen, um dieses Problem zu umgehen. Sie können den Filterregistrierungswert ändern, um einen gegebenen Filter als Filter mit einem einzigen Thread zu kennzeichnen. Um einen Filter als Filter mit einem einzigen Thread zu kennzeichnen, müssen Sie den Registrierungs Wert **ThreadingModel** für den Filter auf `Apartment Threaded`festlegen. Informationen zu Singlethreadapartments finden Sie im Whitepaper [Understanding and Using COM Threading Models](https://go.microsoft.com/fwlink/?LinkId=209159)(Grundlegendes zur Verwendung von COM-Threadingmodellen).  
  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Server Konfigurationsoptionen für den Server Arbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Max. Volltext-Durchforstungs Bereich (Server Konfigurations Option)](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md)   
 [Auffüllen von voll Text Indizes](populate-full-text-indexes.md)   
 [Erstellen und Verwalten von Volltextindizes](create-and-manage-full-text-indexes.md)   
 [sys. dm_fts_memory_buffers &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)   
 [sys. dm_fts_memory_pools &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)   
 [Behandeln von Problemen mit der Volltextindizierung](troubleshoot-full-text-indexing.md)  
  
  
