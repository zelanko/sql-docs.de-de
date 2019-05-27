---
title: Neuerungen in Analytics Platform System - ein horizontaler Datawarehouse
description: Neuigkeiten in Microsoft Analytics Platform System, die beim horizontalen hochskalieren auf lokale Anwendung, die MPP SQL Server Parallel Data Warehouse hostet.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b56791e9fd59aef57c2d107e21eb76896ebb4910
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175044"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Neuerungen in Analytics Platform System, das ein horizontales MPP Datawarehouse
Finden Sie unter Neues in den neuesten Appliance Updates für Microsoft Analytics Platform System (APS). APS ist es sich um eine horizontale Skalierung auf lokale Anwendung, die MPP SQL Server Parallel Data Warehouse hostet. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.4"></a>
## <a name="aps-cu74"></a>APS CU7.4
Datum der Veröffentlichung: Mai 2019

### <a name="loading-large-rows-with-dwloader"></a>Ladevorgänge für umfangreiche Zeilen mit dwloader
Beginnend mit APS CU7.4, werden Kunden eine neue Dwloader zu verwenden, um Zeilen in Tabellen zu laden, die größer als 32 KB (32.768 Bytes). Die neue Dwloader unterstützt der -l-Schalter an, der eine ganze Zahl zwischen 32768 und 33554432 (in Byte) akzeptiert, um Zeilen, die größer als 32 KB zu laden. Verwenden Sie diese Option nur, wenn große Zeilen (mehr als 32 KB) zu laden, diese Option belegt mehr Arbeitsspeicher auf dem Client und dem Server und kann möglicherweise zum verlangsamen lädt. Sie können die neue Dwloader aus [Downloadwebsite](https://www.microsoft.com/download/details.aspx?id=57472).  

### <a name="hdp-30-and-31-support-with-polybase"></a>HDP-3.0 und 3.1 Support mit PolyBase
PolyBase für Zugriffspunkte unterstützt jetzt die HDP-3.0 und 3.1 mit diesem Update. Verwenden Sie Option 7 für HDP-3.x-Versionen. Weitere Informationen finden Sie unter [PolyBase-Konnektivität](https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql) Seite.

### <a name="utf16-file-support-with-polybase"></a>Unterstützung des UTF16-Dateien mit PolyBase
PolyBase unterstützt jetzt das Lesen von durch Trennzeichen getrennte Textdateien, die bei der Codierung UTF16-Format (LE) sind. Finden Sie unter [Erstellen eines externen Dateiformats](https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql) ausführliche Setup. 

<a name="h2-aps-cu7.3"></a>
## <a name="aps-cu73"></a>APS CU7.3
Datum der Veröffentlichung: Dezember 2018

### <a name="common-subexpression-elimination"></a>Entfernen gemeinsamer Teilausdrücke
APS-CU7.3 verbessert die abfrageleistung mit gängiger Unterausdrücke in SQL-Abfrageoptimierer. Die Verbesserung der verbessert die Abfragen auf zwei Arten. Der erste Vorteil ist die Möglichkeit, erkennen und zu eliminieren, z. B. Ausdrücken können SQL-Kompilierungszeit zu reduzieren. Der zweite, wichtigere-Vorteil ist, dass Verschiebevorgänge für Abfragedaten für diesen redundanten Teilausdrücken daher Ausführungszeit behoben wurden, für Abfragen wird schneller. Ausführliche Erläuterung dieser Funktion finden Sie [hier](common-sub-expression-elimination.md).

### <a name="aps-informatica-connector-for-informatica-1020-published"></a>APS Informatica-Connector für Informatica 10.2.0 veröffentlicht
Wir haben eine neue Version der Informatica-Connectors für Zugriffspunkte, die mit Informatica Version 10.2.0 und 10.2.0 veröffentlicht Hotfix 1. Die neuen Connectors können heruntergeladen werden [Downloadwebsite](https://www.microsoft.com/download/details.aspx?id=57472).

#### <a name="supported-versions"></a>Unterstützte Versionen

| APS-Version | Informatica PowerCenter | Treiber |
|:---|:---|:---|
| APS 2016 | 9.6.1 | SQL Server Native Client 11.x |
| APS 2016 und höher | 10.2.0, 10.2.0 Hotfix 1 | SQL Server Native Client 11.x |

<a name="h2-aps-cu7.2"></a>
## <a name="aps-cu72"></a>APS CU7.2
Datum der Veröffentlichung: Oktober 2018

### <a name="support-for-tls-12"></a>Unterstützung für TLS 1.2
APS-CU7.2 unterstützt TLS 1.2. Client-Computer auf Zugriffspunkten und APS knotenübergreifende Kommunikation jetzt festgelegt werden kann, nur über TLS 1.2 zu kommunizieren. Tools wie SSDT, SSIS und Dwloader installiert, die auf Clientcomputern, die festgelegt werden, für die Kommunikation nur über TLS 1.2 können jetzt mit APS mit TLS 1.2 herstellen. Standardmäßig wird APS alle Versionen der TLS (1.0, 1.1 und 1.2) für die Abwärtskompatibilität unterstützt. Wenn Sie Ihre APS-Appliance, auf die Verwendung von TLS 1.2 streng festlegen möchten, können Sie dafür durch Ändern der registrierungseinstellungen. 

Weitere Informationen finden Sie unter [Konfigurieren von TLS 1.2 auf APS](configure-tls12-aps.md).

### <a name="hadoop-encryption-zone-support-for-polybase"></a>Verschlüsselungszone Hadoop für PolyBase unterstützen
PolyBase kann nun mit Hadoop Verschlüsselung Zonen kommunizieren. Finden Sie unter APS-konfigurationsänderungen, die erforderlich sind [Hadoop-Sicherheit konfigurieren](polybase-configure-hadoop-security.md#encryptionzone).

### <a name="insert-select-maxdop-options"></a>INSERT-Select Maxdop-Optionen
Wir haben hinzugefügt eine [featureschalter](appliance-feature-switch.md) , mit der Sie die Maxdop-Einstellungen, die größer als 1 für Insert-Select-Vorgänge auswählen. Sie können jetzt die Maxdop-Einstellung auf 0, 1, 2 oder 4 festgelegt. Der Standardwert lautet 1.

> [!IMPORTANT]  
> Erhöhen der Maxdop kann manchmal langsamer Vorgänge oder Deadlockfehler führen. Wenn in diesem Fall ändern Sie die Einstellung an Maxdop 1, und wiederholen Sie den Vorgang.

### <a name="columnstore-index-health-dmv"></a>Columnstore-Index Integrität DMV
Mit der columnstore-Index Integrität Informationen können Sie anzeigen **Dm_pdw_nodes_db_column_store_row_group_physical_stats** Dmv. Verwenden Sie die folgende Ansicht, um Fragmentierung bestimmen und entscheiden, wann das zum Neuerstellen oder Neuorganisieren eines columnstore-Indexes.

```sql
create view dbo.vCS_rg_physical_stats
as 
with cte
as
(
select   tb.[name]                    AS [logical_table_name]
,        rg.[row_group_id]            AS [row_group_id]
,        rg.[state]                   AS [state]
,        rg.[state_desc]              AS [state_desc]
,        rg.[total_rows]              AS [total_rows]
,        rg.[trim_reason_desc]        AS trim_reason_desc
,        mp.[physical_name]           AS physical_name
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb               ON  sm.[schema_id]          = tb.[schema_id]                             
JOIN    sys.[pdw_table_mappings] mp   ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt     ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[dm_pdw_nodes_db_column_store_row_group_physical_stats] rg      ON  rg.[object_id]     = nt.[object_id]
                                                                            AND rg.[pdw_node_id]   = nt.[pdw_node_id]
                                        AND rg.[pdw_node_id]    = nt.[pdw_node_id]                                          
)
select *
from cte;
```

### <a name="polybase-date-range-increase-for-orc-and-parquet-files"></a>PolyBase Datum Bereich erhöhen, ORC und Parquet-Dateien
Lesen, importieren und Exportieren von Date-Datentypen, die jetzt mithilfe von PolyBase unterstützt die Datumsangaben vor 1970-01-01 und nach 2038-01-20 für ORC und parquet-Dateien.

### <a name="ssis-destination-adapter-for-sql-server-2017-as-target"></a>Zieladapter für SSIS für SQL Server 2017 als Ziel
Zieladapter für den neuen APS SSIS, die SQL Server 2017 unterstützt wird, als Ziel der Bereitstellung heruntergeladen werden kann [Downloadwebsite](https://www.microsoft.com/download/details.aspx?id=57472).

<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
Veröffentlichungsdatum: Juli 2018

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>DBCC-Befehle parallelitätsslots (verhaltensänderung) nicht nutzen.
APS unterstützt eine Teilmenge der T-SQL [DBCC-Befehle](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql) wie z. B. [DBCC DROPCLEANBUFFERS](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql). Zuvor mit diesen Befehlen nutzen würden eine [parallelitätsslot](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots) Reduzieren der Anzahl der Benutzer lädt/Abfragen, die ausgeführt werden konnte. Die `DBCC` Befehle werden jetzt in einer lokalen Warteschlange, die einen Benutzer parallelitätsslot, Verbessern der allgemeinen Leistung bei der abfrageausführung nicht zwingend ausgeführt.

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>Einige Metadaten-Aufrufe ersetzt mit Katalogobjekten
Mithilfe von Katalogobjekten für Metadaten-Aufrufe anstelle von SMO verfügt über leistungsverbesserungen in APS angezeigt. Von CU7.1 beginnen, einige dieser Metadaten-Aufrufe jetzt Catalog-Objekten wird standardmäßig verwendet. Dieses Verhalten kann durch deaktiviert werden [featureschalter](appliance-feature-switch.md) Wenn Kunden Metadatenabfragen Probleme auftreten.

### <a name="bug-fixes"></a>Behebung von Programmfehlern
Wir haben auf SQL Server 2016 SP2 CU2 mit APS CU7.1 aktualisiert. Das Upgrade behebt einige Probleme, die unten beschrieben.

| Titel | Description |
|:---|:---|
| **Potenzielle Tuple Mover Deadlocks** |Das Upgrade behebt eine lange bestehendes Möglichkeit eines Deadlocks in einem verteilten Transaktion und Tuple Mover-Hintergrundthread. Nach der Installation CU7.1 können Kunden, die TF634 zum Beenden der tupelverschiebungsvorgang als SQL Server-Startparameter oder das globale Ablaufverfolgungsflag verwendet es deinstallieren. | 
| **Bestimmte-Lag/Lead-Abfrage ein Fehler auftritt** |Bestimmte Abfragen in CCI-Tabellen mit geschachtelten-Lag/Lead-Funktionen, die Fehler würden wurde jetzt behoben, das Upgrade. | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
Datum der Veröffentlichung: Mai 2018

APS 2016 ist eine Voraussetzung für die ein Upgrade auf AU7 durchführen. Im folgenden finden neue Features in der APS-AU7:

### <a name="auto-create-and-auto-update-statistics"></a>Automatische Erstellung und Aktualisierung von Statistiken
APS-AU7 erstellt und Statistics wird standardmäßig automatisch aktualisiert. Um statistikeinstellungen für zu aktualisieren, können Administratoren ein neues Feature-Switch-Menüelement in der [Configuration Manager](appliance-configuration.md#CMTasks). Die [featureschalter](appliance-feature-switch.md) steuert die Auto-create, automatische Aktualisierung und Verhalten der asynchronen Aktualisieren von Statistiken. Sie können auch die Einstellungen der Treiberstatistik mit aktualisieren die [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) Anweisung.

### <a name="t-sql"></a>T-SQL
Wählen Sie @var wird jetzt unterstützt. Weitere Informationen finden Sie unter [wählen Sie die lokale Variable](/sql/t-sql/language-elements/select-local-variable-transact-sql) 

Abfragehinweise HASH "und" ORDER GROUP werden jetzt unterstützt. Weitere Informationen finden Sie unter [Hints(Transact-SQL) - Abfrage](/sql/t-sql/queries/hints-transact-sql-query)

### <a name="feature-switch"></a>Feature-Switch
APS-AU7 führt Feature-Switch in [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled und DmsProcessStopMessageTimeoutInSeconds werden nun konfigurierbare Optionen, die von Administratoren geändert werden können.

### <a name="known-issues"></a>Bekannte Probleme
Bei APS AU7-Software, wird ein Intel BIOS-Update bereitgestellt, die als Problem behebt *seitenkanalangriffe mit spekulativer Ausführung*. Sollen, dass die Angriffe ausnutzen bezeichnet, was *Spectre und Meltdown Sicherheitsrisiken*. Zwar zusammen mit APS gepackt werden, wird die BIOS-Aktualisierung manuell installiert und nicht als Teil der APS-AU7-Softwareinstallation.

Microsoft empfiehlt, alle Kunden die BIOS-Aktualisierung installiert wird. Microsoft verfügt über die Auswirkungen der Kernel virtuelle Adresse Shadowing (KVAS), Kernel Seite Tabelle Dereferenzierung (KPTI) und indirekte Branch Vorhersage-Lösung (IBP) für verschiedene SQL-Workloads in verschiedenen Umgebungen gemessen. Die Messwerte erheblichen Leistungsabfall auf einige Workloads zu finden. Basierend auf den Ergebnissen, wird empfohlen, dass Sie die leistungsbezogenen Auswirkungen der Aktivierung von BIOS-Update vor der Bereitstellung in einer produktionsumgebung testen. Finden Sie unter SQL Server-Leitfaden [hier](https://support.microsoft.com/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
## <a name="aps-2016"></a>APS 2016
In diesem Abschnitt werden die neuen Features für APS 2016-AU6 beschrieben.

### <a name="sql-server-2016"></a>SQL Server 2016

APS-AU6 auf die neueste Version von SQL Server 2016 ausgeführt wird und der standardmäßige Datenbank-Kompatibilitätsgrad 130 verwendet. SQL Server 2016 ermöglicht die Unterstützung für neue Features wie z. B.:

- Sekundäre Indizes für gruppierte columnstore-Indizes.
- Kerberos für PolyBase.

### <a name="t-sql"></a>T-SQL
APS-AU6 unterstützt diese Verbesserungen der T-SQL-Kompatibilität.  Diese zusätzliche Sprachelemente vereinfachen die Migration von SQL Server und anderen Datenquellen. 

- [SQL-Sortierungen auf Spaltenebene][] werden jetzt unterstützt, zusätzlich zu Windows-Sortierungen.
- [Nicht gruppierte Indizes für gruppierte columnstore-Indizes][] Verbessern der Leistung von Abfragen, die in den gruppierten columnstore-Index nach bestimmten Werten suchen. 
- [SELECT...INTO][] 
- [sp_spaceused()][] zeigt, wie viel Speicherplatz verwendet oder in einer Tabelle oder Datenbank reserviert.
- [Breite Tabellen][] Unterstützung entspricht dem SQL Server 2016. Der vorherige Grenzwert von 32 KB für die Zeilengröße ist nicht mehr vorhanden. 

**Datentypen**

- [VARCHAR(max)][], [NVARCHAR(MAX)][] und [VARBINARY(MAX)][]. Diese LOB-Datentypen haben eine Maximalgröße von 2 GB. Um diese zu laden Objekten [bcp (Hilfsprogramm)][]. PolyBase und Dwloader unterstützen derzeit diese Datentypen. 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMERIC][] und dezimaldatentypen verwendet.

**Fensterfunktionen**

- [ROWS oder RANGE][] in der OVER-Klausel der SELECT-Anweisung.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**Sicherheitsfunktionen**

- [CHECKSUM()][] und [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**Zusätzliche Funktionen**

- [NEWID()][]
- [RAND()][]

### <a name="polybasehadoop-enhancements"></a>PolyBase/Hadoop-Verbesserungen

- Kompatibilität mit Hortonworks HDP 2.4 und HDP 2.5
- Unterstützung für Kerberos über datenbankweit gültige Anmeldeinformationen
- Unterstützung von Anmeldeinformationen mit Azure Storage-Blobs

### <a name="install-and-upgrade-enhancements"></a>Installieren und Aktualisieren von Erweiterungen

**Enterprise-Architektur Updates** ein Upgrade Ihrer vorhandene Appliance auf APS AU6 installiert die neuesten Firmware- und Treiberupdates, einschließlich Sicherheitsupdates. 

Eine neue Einheit von DELL oder HPE enthält die neuesten Updates plus:

- Aktuelle Unterstützung für Generation-Prozessoren (Broadwell)
- Aktualisieren auf DDR4-DIMMs
- Verbesserte DIMM-Durchsatz

**Integration**

- Vollständig ermöglicht vollqualifizierten Domänennamen (FQDN)-Unterstützung zum Einrichten einer Vertrauensstellung an dieses Gerät. 
- Um FQDN verwenden zu können, müssen Sie ein vollständiges Update und während des Upgrades teilnehmen. 

**Verringerte Ausfallzeiten** installieren oder Aktualisieren auf APS AU6 ist schneller und erfordert weniger Ausfallzeiten als mit vorherigen Versionen. Reduzieren von Ausfallzeiten, die Installation oder des Upgrades: 

 - Anwenden von WSUS-Updates unter Verwendung eines Images optimiert enthält, die alle Updates bis Juni 2016
 - Wendet von Sicherheitsupdates mit der Treiber und Firmware-updates
 - Platziert die neuesten Hotfixes und das Gerät Überprüfung-Dienstprogramm (PAV) auf Ihrem Gerät, sodass sie bereit sind, ohne dass diese herunterladen installieren werden.

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[SQL-Sortierungen auf Spaltenebene]: ~/relational-databases/collations/collation-and-unicode-support.md

[Nicht gruppierte Indizes für gruppierte columnstore-Indizes]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR(MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR(MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY(MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[SELECT...INTO]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Breite Tabellen]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp (Hilfsprogramm)]:/sql/tools/bcp-utility
[UNIQUEIDENTIFIER]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[NUMERIC]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS oder RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[CHECKSUM()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[NEWID()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  


