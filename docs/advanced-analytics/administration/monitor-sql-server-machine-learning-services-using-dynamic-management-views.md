---
title: Überwachen der Python-und R-Skriptausführung mithilfe von DMVs
description: Verwenden Sie dynamische Verwaltungs Sichten (DMVs), um die Ausführung externer python-und R-Skripts in SQL Server Machine Learning Services zu überwachen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0e541e1d0eb2a8bb1ac512276fa395f8d8c6379f
ms.sourcegitcommit: 1c3f56deaa4c1ffbe5d7f75752ebe10447c3e7af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "70978406"
---
# <a name="monitor-sql-server-machine-learning-services-using-dynamic-management-views-dmvs"></a>Überwachen von SQL Server Machine Learning Services mithilfe dynamischer Verwaltungs Sichten (DMVs)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mithilfe dynamischer Verwaltungs Sichten (DMVs) können Sie die Ausführung externer Skripts (python und R), der verwendeten Ressourcen, der Diagnose von Problemen und der Optimierung der Leistung in SQL Server Machine Learning Services überwachen.

In diesem Artikel finden Sie die DMVs, die für SQL Server Machine Learning Services spezifisch sind. Außerdem finden Sie Beispiele für Abfragen, die Folgendes anzeigen:

+ Einstellungen und Konfigurationsoptionen für Machine Learning
+ Aktive Sitzungen, die externe python oder Skripts ausführen
+ Ausführungs Statistik für die externe Laufzeit für python und R
+ Leistungsindikatoren für externe Skripts
+ Arbeitsspeicher Auslastung für das Betriebssystem, SQL Server und externe Ressourcenpools
+ Speicherkonfiguration für SQL Server und externe Ressourcenpools
+ Resource Governor von Ressourcenpools, einschließlich externer Ressourcenpools
+ Installierte Pakete für python und R

Weitere allgemeine Informationen zu DMVs finden Sie unter [dynamische System Verwaltungs Sichten](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).

> [!TIP]
> Sie können die benutzerdefinierten Berichte auch verwenden, um SQL Server Machine Learning Services zu überwachen. Weitere Informationen finden Sie unter [Überwachen von Machine Learning mithilfe von benutzerdefinierten Berichten in Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="dynamic-management-views"></a>Dynamische Verwaltungssichten

Die folgenden dynamischen Verwaltungs Sichten können beim Überwachen von Machine Learning-Workloads in SQL Server verwendet werden. Um die DMVs abzufragen, benötigen `VIEW SERVER STATE` Sie die-Berechtigung für die-Instanz.

| Dynamische Verwaltungssicht | Typ | Beschreibung |
|-------------------------|------|-------------|
| [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) | Ausführung | Gibt eine Zeile für jedes aktive Workerkonto zurück, das ein externes Skript ausführt. |
| [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) | Ausführung | Gibt eine Zeile für jeden Typ von externer Skriptanforderung zurück. |
| [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) | Ausführung | Gibt eine Zeile pro Leistungsindikator zurück, der vom Server verwaltet wird. Wenn Sie die Such Bedingung `WHERE object_name LIKE '%External Scripts%'`verwenden, können Sie anhand dieser Informationen festzustellen, wie viele Skripts ausgeführt wurden, welche Skripts mit welchem Authentifizierungsmodus ausgeführt wurden oder wie viele R-oder python-Aufrufe für die Instanz insgesamt ausgegeben wurden. |
| [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) | Resource Governor | Gibt Informationen über den aktuellen Status des externen Ressourcenpools in Resource Governor, die aktuelle Konfiguration von Ressourcenpools und Ressourcenpool Statistiken zurück. |
| [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md) | Resource Governor | Gibt Informationen zur CPU-Affinität zur aktuellen externen Ressourcenpool Konfiguration in Resource Governor zurück. Gibt eine Zeile pro Zeitplanungsmodul in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] zurück, wobei jedes Zeitplanungsmodul einem einzelnen Prozessor zugeordnet ist. Mithilfe dieser Sicht können Sie den Zustand eines Zeitplanungsmoduls überwachen oder Endlostasks identifizieren. |

Weitere Informationen zum über [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Wachen von Instanzen finden Sie unter [Katalog Sichten](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) und [Resource Governor verwandte dynamische Verwaltungs Sichten](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="settings-and-configuration"></a>Einstellungen und Konfiguration

Zeigen Sie die Installationseinstellungen für Machine Learning Services und die Konfigurationsoptionen an.

![Ausgabe der Einstellungs-und Konfigurations Abfrage](media/dmv-settings-and-configuration.png "Ausgabe der Einstellungs-und Konfigurations Abfrage")

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Weitere Informationen zu den verwendeten Sichten und Funktionen finden Sie unter [sys. DM _server_registry](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md), [sys. Konfigurationen](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)und [SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md).

```sql
SELECT CAST(SERVERPROPERTY('IsAdvancedAnalyticsInstalled') AS INT) AS IsMLServicesInstalled
    , CAST(value_in_use AS INT) AS ExternalScriptsEnabled
    , COALESCE(SIGN(SUSER_ID(CONCAT (
                    CAST(SERVERPROPERTY('MachineName') AS NVARCHAR(128))
                    , '\SQLRUserGroup'
                    , CAST(serverproperty('InstanceName') AS NVARCHAR(128))
                    ))), 0) AS ImpliedAuthenticationEnabled
    , COALESCE((
            SELECT CAST(r.value_data AS INT)
            FROM sys.dm_server_registry AS r
            WHERE r.registry_key LIKE 'HKLM\Software\Microsoft\Microsoft SQL Server\%\SuperSocketNetLib\Tcp'
            AND r.value_name = 'Enabled'
            ), - 1) AS IsTcpEnabled
FROM sys.configurations
WHERE name = 'external scripts enabled';
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Beschreibung |
|--------|-------------|
| IsMLServicesInstalled | Gibt 1 zurück, wenn SQL Server-Machine Learning Services für die-Instanz installiert ist. Andernfalls wird 0 zurückgegeben. |
| Externalscriptsenabled | Gibt 1 zurück, wenn externe Skripts für die-Instanz aktiviert sind. Andernfalls wird 0 zurückgegeben. |
| ImpliedAuthenticationEnabled | Gibt 1 zurück, wenn die implizite Authentifizierung aktiviert ist. Andernfalls wird 0 zurückgegeben. Die Konfiguration für die implizite Authentifizierung wird überprüft, indem überprüft wird, ob eine Anmeldung für sqlrusergroup vorhanden ist. |
| IsTcpEnabled | Gibt 1 zurück, wenn das TCP/IP-Protokoll für die-Instanz aktiviert ist. Andernfalls wird 0 zurückgegeben. Weitere Informationen finden Sie unter [Standard SQL Server Netzwerkprotokoll Konfiguration](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md). |

## <a name="active-sessions"></a>Aktive Sitzungen

Anzeigen der aktiven Sitzungen, die externe Skripts ausführen.

![Ausgabe der aktiven Einstellungs Abfrage](media/dmv-active-sessions.png "Ausgabe der aktiven Einstellungs Abfrage")

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Weitere Informationen zu den verwendeten dynamischen Verwaltungs Sichten finden Sie unter [sys. DM _exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md), [sys. DM _external_script_requests](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)und [sys. DM _exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).

```sql
SELECT r.session_id, r.blocking_session_id, r.status, DB_NAME(s.database_id) AS database_name
    , s.login_name, r.wait_time, r.wait_type, r.last_wait_type, r.total_elapsed_time, r.cpu_time
    , r.reads, r.logical_reads, r.writes, er.language, er.degree_of_parallelism, er.external_user_name
FROM sys.dm_exec_requests AS r
INNER JOIN sys.dm_external_script_requests AS er
ON r.external_script_request_id = er.external_script_request_id
INNER JOIN sys.dm_exec_sessions AS s
ON s.session_id = r.session_id;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Beschreibung |
|--------|-------------|
| session_id | Identifiziert die einer aktiven primären Verbindung zugeordnete Sitzung. |
| blocking_session_id | ID der Sitzung, die die Anforderung blockiert. Wenn diese Spalte den Wert NULL aufweist, wird die Anforderung nicht blockiert, oder die Sitzungsinformationen der blockierenden Sitzung sind nicht verfügbar (bzw. können nicht identifiziert werden). |
| status | Status der Anforderung. |
| database_name | Der Name der aktuellen Datenbank für jede Sitzung. |
| login_name | SQL Server Anmelde Name, unter dem die Sitzung gerade ausgeführt wird. |
| wait_time | Wenn die Anforderung zurzeit blockiert wird, gibt diese Spalte die Dauer des aktuellen Wartevorgangs in Millisekunden an. Lässt keine NULL-Werte zu. |
| wait_type | Wenn die Anforderung zurzeit blockiert wird, gibt diese Spalte den Wartetyp zurück. Weitere Informationen zu warte Typen finden Sie unter [sys. DM _os_wait_stats](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). |
| last_wait_type | Wenn diese Anforderung zuvor bereits blockiert war, gibt diese Spalte den Typ des letzten Wartevorgangs zurück. |
| total_elapsed_time | Gesamtzeit seit dem Eintreffen der Anforderung (in Millisekunden). |
| cpu_time | Von der Anforderung beanspruchte CPU-Zeit (in Millisekunden). |
| reads | Anzahl der von dieser Anforderung ausgeführten Lesevorgänge. |
| logical_reads | Anzahl der von dieser Anforderung ausgeführten logischen Lesevorgänge. |
| writes | Anzahl der von dieser Anforderung ausgeführten Schreibvorgänge. |
| language | Schlüsselwort, das einer unterstützten Skriptsprache entspricht. |
| degree_of_parallelism | Zahl, die die Anzahl von parallelen Prozessen angibt, die erstellt wurden. Dieser Wert kann sich von der Anzahl von parallelen Prozessen unterscheiden, die angefordert wurden. |
| external_user_name | Das Windows-Workerkonto, unter dem das Skript ausgeführt wurde. |

## <a name="execution-statistics"></a>Ausführungsstatistiken

Anzeigen der Ausführungs Statistik für die externe Laufzeit für R und python. Zurzeit sind nur Statistiken von revoscaler-, revoscalepy-oder microsoftml-Paketfunktionen verfügbar.

![Ausgabe der Abfrage der Ausführungs Statistik](media/dmv-execution-statistics.png "Ausgabe der Abfrage der Ausführungs Statistik")

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Weitere Informationen zur verwendeten dynamischen Verwaltungs Sicht finden Sie unter [sys. DM _external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). Die Abfrage gibt nur Funktionen zurück, die mehrmals ausgeführt wurden.

```sql
SELECT language, counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE counter_value > 0
ORDER BY language, counter_name;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Beschreibung |
|--------|-------------|
| language | Name der registrierten externen Skriptsprache. |
| counter_name | Name einer registrierten externen Skriptfunktion. |
| counter_value | Gesamtanzahl der Instanzen, die von der registrierten externen Skriptfunktion auf dem Server aufgerufen wurden. Dieser Wert ist kumulativ und beginnt mit dem Zeitpunkt, zu dem das Feature auf der Instanz installiert wurde. Der Wert kann nicht zurückgesetzt werden. |

## <a name="performance-counters"></a>Leistungsindikatoren

Anzeigen der Leistungsindikatoren im Zusammenhang mit der Ausführung externer Skripts.

![Ausgabe der Leistungsindikator Abfrage](media/dmv-performance-counters.png "Ausgabe der Leistungsindikator Abfrage")

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Weitere Informationen zur verwendeten dynamischen Verwaltungs Sicht finden Sie unter [sys. DM _os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md).

```sql
SELECT counter_name, cntr_value
FROM sys.dm_os_performance_counters 
WHERE object_name LIKE '%External Scripts%'
```

**sys. DM _os_performance_counters** gibt die folgenden Leistungsindikatoren für externe Skripts aus:

| Leistungsindikator | Beschreibung |
|---------|-------------|
| Total Executions | Anzahl externer Prozesse, die von lokalen oder Remote Aufrufen gestartet werden. |
| Parallel Executions | Gibt an, wie oft ein Skript die  _\@parallele_ Spezifikation enthielt und [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ob ein paralleler Abfrageplan generiert und verwendet werden konnte. |
| Streaming Executions | Gibt an, wie oft das Streaming-Feature aufgerufen wurde. |
| SQL CC Executions | Anzahl externer Skripts, die ausgeführt werden, wenn der-Befehl Remote instanziiert wurde und SQL Server als computekontext verwendet wurde. |
| Implied Auth. Anmeldungen | Gibt an, wie oft ein ODBC-Loopback-Rückruf mit implizierter Authentifizierung durchgeführt wurde. Das heißt, der [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] hat den-Befehl im Auftrag des Benutzers ausgeführt, der die Skript Anforderung sendet. |
| Total Execution Time (ms) | Verstrichene Zeit zwischen dem Aufruf und dem Abschluss des Aufrufes. |
| Execution Errors | Gibt an, wie oft Skripts Fehler gemeldet haben. Diese Anzahl umfasst keine R-oder python-Fehler. |

## <a name="memory-usage"></a>Speicherauslastung

Anzeigen von Informationen zum Arbeitsspeicher, der vom Betriebssystem, SQL Server und den externen Pools verwendet wird.

![Ausgabe der Speicher] Auslastungs Abfrage (media/dmv-memory-usage.png "Ausgabe der Speicher") Auslastungs Abfrage

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Weitere Informationen zu den verwendeten dynamischen Verwaltungs Sichten finden Sie unter [sys. DM _resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) und [sys. DM _os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md).

```sql
SELECT physical_memory_kb, committed_kb
    , (SELECT SUM(peak_memory_kb)
        FROM sys.dm_resource_governor_external_resource_pools AS ep
        ) AS external_pool_peak_memory_kb
FROM sys.dm_os_sys_info;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Beschreibung |
|--------|-------------|
| physical_memory_kb | Die Gesamtmenge an physischem Arbeitsspeicher auf dem Computer. |
| committed_kb | Der zugesicherte Speicher in Kilobyte (KB) im Speicher-Manager. Reservierter Arbeitsspeicher im Speicher-Manager ist nicht eingeschlossen. |
| external_pool_peak_memory_kb | Die Summe der maximalen Menge an verwendeter Arbeitsspeicher in Kilobyte für alle externen Ressourcenpools. |

## <a name="memory-configuration"></a>Konfiguration des Arbeitsspeichers

Anzeigen von Informationen zur maximalen Arbeitsspeicher Konfiguration als Prozentsatz von SQL Server und externen Ressourcenpools. Wenn SQL Server mit dem Standardwert `max server memory (MB)`ausgeführt wird, wird er als 100% des Betriebssystem Arbeitsspeichers betrachtet.

![Ausgabe der Arbeitsspeicher-Konfigurations Abfrage](media/dmv-memory-configuration.png "Ausgabe der Arbeitsspeicher-Konfigurations Abfrage")

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Weitere Informationen zu den verwendeten Sichten finden Sie unter [sys. Konfigurationen](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) und [sys. DM _resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT 'SQL Server' AS name
    , CASE CAST(c.value AS BIGINT)
        WHEN 2147483647 THEN 100
        ELSE (SELECT CAST(c.value AS BIGINT) / (physical_memory_kb / 1024.0) * 100 FROM sys.dm_os_sys_info)
        END AS max_memory_percent
FROM sys.configurations AS c
WHERE c.name LIKE 'max server memory (MB)'
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name, ep.max_memory_percent
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Beschreibung |
|--------|-------------|
| NAME | Der Name des externen Ressourcenpools oder SQL Server. |
| max_memory_percent | Der maximale Arbeitsspeicher, der von SQL Server oder dem externen Ressourcenpool verwendet werden kann. |

## <a name="resource-pools"></a>Ressourcenpools

In [SQL Server Resource Governor](../../relational-databases/resource-governor/resource-governor.md)stellt ein [Ressourcenpool](../../relational-databases/resource-governor/resource-governor-resource-pool.md) eine Teilmenge der physischen Ressourcen einer Instanz dar. Sie können Grenzwerte für die CPU, physische e/a und den Arbeitsspeicher angeben, die von der eingehenden Anwendung angefordert werden, einschließlich der Ausführung externer Skripts, die innerhalb des Ressourcenpools verwendet werden kann. Anzeigen der Ressourcenpools, die für SQL Server und externe Skripts verwendet werden.

![Ausgabe der Abfrage für Ressourcenpools](media/dmv-resource-pools.png "Ausgabe der Abfrage für Ressourcenpools")

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Weitere Informationen zu den verwendeten dynamischen Verwaltungs Sichten finden Sie unter [sys. DM _resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md) und [sys. DM _resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT CONCAT ('SQL Server - ', p.name) AS pool_name
    , p.total_cpu_usage_ms, p.read_io_completed_total, p.write_io_completed_total
FROM sys.dm_resource_governor_resource_pools AS p
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name
    , ep.total_cpu_user_ms, ep.read_io_count, ep.write_io_count
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Beschreibung |
|--------|-------------|
| pool_name | Name des Ressourcenpools. SQL Server Ressourcenpools wird das Präfix `SQL Server` vorangestellt, und externen Ressourcenpools wird `External Pool`das Präfix vorangestellt.
| total_cpu_usage_hours | Die kumulierte CPU-Auslastung in Millisekunden seit dem Zurücksetzen der Ressourcen-govenstatistiken. |
| read_io_completed_total | Die Gesamtanzahl der E/A-Lesevorgänge, die seit dem Zurücksetzen der Ressourcenkontrollstatistiken abgeschlossen wurden. |
| write_io_completed_total | Die Gesamtanzahl der E/A-Schreibvorgänge, die seit dem Zurücksetzen der Ressourcenkontrollstatistiken abgeschlossen wurden. |

## <a name="installed-packages"></a>Installierte Pakete

Sie können die in SQL Server Machine Learning Services installierten r-und Python-Pakete anzeigen, indem Sie ein r-oder Python-Skript ausführen, das diese ausgibt.

### <a name="installed-packages-for-r"></a>Installierte Pakete für R

Sehen Sie sich die in SQL Server Machine Learning Services installierten R-Pakete an.

![Ausgabe der installierten Pakete für R-Abfragen](media/dmv-installed-packages-r.png "Ausgabe der installierten Pakete für R-Abfragen")

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Die Abfrage verwendet ein r-Skript, um die mit SQL Server installierten r-Pakete zu bestimmen.

```sql
EXEC sp_execute_external_script @language = N'R'
, @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
    , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
```

Die zurückgegebenen Spalten lauten:

| Spalte | Beschreibung |
|--------|-------------|
| Package | Der Name des installierten Pakets. |
| Version | Version des Pakets. |
| Depends (Abhängig) | Listet die Pakete auf, von denen das installierte Paket abhängt. |
| License (Lizenz) | Lizenz für das installierte Paket. |
| LibPath | Das Verzeichnis, in dem Sie das Paket finden können. |

### <a name="installed-packages-for-python"></a>Installierte Pakete für python

Zeigen Sie die in SQL Server Machine Learning Services installierten Python-Pakete an.

![Ausgabe der installierten Pakete für die python-Abfrage](media/dmv-installed-packages-python.png "Ausgabe der installierten Pakete für die python-Abfrage")

Führen Sie die folgende Abfrage aus, um diese Ausgabe zu erhalten. Die Abfrage verwendet ein Python-Skript, um die mit SQL Server installierten Python-Pakete zu bestimmen.

```sql
EXEC sp_execute_external_script @language = N'Python'
, @script = N'
import pip
OutputDataSet = pandas.DataFrame([(i.key, i.version, i.location) for i in pip.get_installed_distributions()])'
WITH result sets((Package NVARCHAR(128), Version NVARCHAR(128), Location NVARCHAR(1000)));
```

Die zurückgegebenen Spalten lauten:

| Spalte | Beschreibung |
|--------|-------------|
| Package | Der Name des installierten Pakets. |
| Version | Version des Pakets. |
| Speicherort | Das Verzeichnis, in dem Sie das Paket finden können. |

## <a name="next-steps"></a>Nächste Schritte

+ [Verwalten und Überwachen von Machine Learning-Lösungen](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
+ [Erweiterte Ereignisse für Machine Learning](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)
+ [Resource Governor verwandte dynamische Verwaltungs Sichten](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)
+ [Dynamische System Verwaltungs Sichten](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Überwachen von Machine Learning mithilfe von benutzerdefinierten Berichten in Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)
