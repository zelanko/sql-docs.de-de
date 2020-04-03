---
title: Neuigkeiten
description: Sehen Sie sich die Neuerungen in Microsoft Analytics Platform System an, einer lokalen Scale-Out-Appliance, die MPP SQL Server Parallel Data Warehouse hostet.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: faf3bd1f487fb5c850759fdde3ddecd32bdd3b1f
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625542"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Neuerungen in Analytics Platform System, einem scale-out MPP-Data Warehouse
Sehen Sie, was in den neuesten Appliance-Updates für Microsoft Analytics Platform System (APS) neu ist. APS ist eine lokale Scale-Out-Appliance, die MPP SQL Server Parallel Data Warehouse hostet. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.6"></a>
## <a name="aps-cu76"></a>APS CU7.6
Veröffentlichungsdatum - April 2020

### <a name="rename-column"></a>Rename Column (Spalte umbenennen)
Nach dem Upgrade auf CU7.6 können Kunden eine Spalte einer vom Benutzer erstellten Tabelle umbenennen. Syntax, Beispiele, Einschränkungen und weitere Informationen finden Sie unter [RENAME (Transact-SQL).](https://docs.microsoft.com/sql/t-sql/statements/rename-transact-sql)

### <a name="alter-view"></a>Ändern der Ansicht
Kunden können nun Ansichten ändern. Weitere Informationen finden Sie unter [ALTER VIEW (Transact-SQL).](https://docs.microsoft.com/sql/t-sql/statements/alter-view-transact-sql)

<a name="h2-aps-cu7.5"></a>
## <a name="aps-cu75"></a>APS CU7.5
Veröffentlichungsdatum - September 2019

### <a name="alter-external-data-source"></a>Externe Datenquelle ändern
Kunden können die externe Datenquellendefinition mit dem CU7.5-Update ändern. Kunden mit hoher Verfügbarkeit des Hadoop-Namensknotens können nun die Datenquelle ändern, um die Argumente zu ändern, wenn ein Failover auftritt. Für APS können nur die LOCATION, RESOURCE_MANAGER_LOCATION und CREDENTIAL geändert werden. Weitere Informationen finden Sie [unter Ändern der externen Datenquelle.](https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql?view=sql-server-2017)

### <a name="cdh-515-and-516-support-with-polybase"></a>CDH 5.15 und 5.16 Unterstützung mit PolyBase
PolyBase auf APS mit CU7.5-Update unterstützt jetzt CDH 5.15 und 5.16 Versionen der Hadoop-Distribution von Cloudera. Verwenden Sie Option 6 für CDH 5.x-Versionen. 

### <a name="try_convert-and-try_cast-support"></a>Try_Convert und Try_Cast Unterstützung
CU7.5 APS unterstützt jetzt [TRY_CAST](https://docs.microsoft.com/sql/t-sql/functions/try-cast-transact-sql?view=sql-server-2017) und [TRY_CONVERT](https://docs.microsoft.com/sql/t-sql/functions/try-convert-transact-sql?view=sql-server-2017) tsql-Funktionen. Beide Funktionen geben einen in den angegebenen Datentyp konvertierten Wert zurück, wenn die Konvertierung erfolgreich ist. Andernfalls wird null zurückgegeben.

<a name="h2-aps-cu7.4"></a>
## <a name="aps-cu74"></a>APS CU7.4
Veröffentlichungsdatum - Mai 2019

### <a name="loading-large-rows-with-dwloader"></a>Laden großer Zeilen mit dwloader
Ab APS CU7.4 können Kunden einen neuen Dwloader verwenden, um Zeilen in Tabellen zu laden, die größer als 32 KB (32.768 Bytes) sind. Der neue dwloader unterstützt den Schalter -l, der einen Ganzzahlwert zwischen 32768 und 33554432 (in Bytes) benötigt, um Zeilen zu laden, die größer als 32 KB sind. Verwenden Sie diese Option nur beim Laden großer Zeilen (größer als 32 KB), da dieser Switch mehr Arbeitsspeicher auf dem Client und dem Server reserviert und die Lasten verlangsamen kann. Sie können den neuen dwloader von der [Download-Site](https://www.microsoft.com/download/details.aspx?id=57472)herunterladen.  

### <a name="hdp-30-and-31-support-with-polybase"></a>HDP 3.0- und 3.1-Unterstützung mit PolyBase
PolyBase auf APS unterstützt jetzt HDP 3.0 und 3.1 mit diesem Update. Verwenden Sie Option 7 für HDP 3.x-Versionen. Weitere Informationen finden Sie auf der [PolyBase-Verbindungsseite.](https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql)

### <a name="utf16-file-support-with-polybase"></a>UTF16-Dateiunterstützung mit PolyBase
PolyBase unterstützt jetzt das Lesen von Textdateien mit trennzeichen durch Trennzeichen, die in UTF16 (LE)-Codierung enthalten sind. Siehe [Erstellen eines externen Dateiformats](https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql) für Setupdetails. 

<a name="h2-aps-cu7.3"></a>
## <a name="aps-cu73"></a>APS CU7.3
Veröffentlichungsdatum - Dezember 2018

### <a name="common-subexpression-elimination"></a>Entfernen gemeinsamer Teilausdrücke
APS CU7.3 verbessert die Abfrageleistung mit der allgemeinen Subexpression-Eliminierung im SQL-Abfrageoptimierer. Die Verbesserung verbessert Abfragen auf zwei Arten. Der erste Vorteil ist die Möglichkeit, solche Ausdrücke zu identifizieren und zu eliminieren, um die SQL-Kompilierungszeit zu reduzieren. Der zweite und wichtigere Vorteil ist, dass Datenverschiebungsvorgänge für diese redundanten Unterausdrücke eliminiert werden, sodass die Ausführungszeit für Abfragen schneller wird. Ausführliche Erläuterungen zu diesem Feature finden Sie [hier](common-sub-expression-elimination.md).

### <a name="aps-informatica-connector-for-informatica-1020-published"></a>APS Informatica-Steckverbinder für Informatica 10.2.0 veröffentlicht
Wir haben eine neue Version von Informatica-Connectors für APS veröffentlicht, die mit Informatica Version 10.2.0 und 10.2.0 Hotfix 1 funktioniert. Die neuen Connectors können von der [Download-Site](https://www.microsoft.com/download/details.aspx?id=57472)heruntergeladen werden.

#### <a name="supported-versions"></a>Unterstützte Versionen

| APS-Version | Informatica PowerCenter | Treiber |
|:---|:---|:---|
| APS 2016 | 9.6.1 | SQL Server Native Client 11.x |
| APS 2016 und höher | 10.2.0, 10.2.0 Hotfix 1 | SQL Server Native Client 11.x |

<a name="h2-aps-cu7.2"></a>
## <a name="aps-cu72"></a>APS CU7.2
Veröffentlichungsdatum - Oktober 2018

### <a name="support-for-tls-12"></a>Unterstützung für TLS 1.2
APS CU7.2 unterstützt TLS 1.2. Clientcomputer zu APS und APS-Kommunikation innerhalb von Knoten können jetzt so eingestellt werden, dass sie nur über TLS1.2 kommuniziert. Tools wie SSDT, SSIS und Dwloader, die auf Clientcomputern installiert sind und nur über TLS 1.2 kommunizieren sollen, können jetzt mithilfe von TLS 1.2 eine Verbindung mit APS herstellen. Standardmäßig unterstützt APS alle TLS-Versionen (1.0, 1.1 und 1.2) aus Gründen der Abwärtskompatibilität. Wenn Sie Ihre APS-Appliance so einstellen möchten, dass TLS 1.2 strikt verwendet wird, können Sie dies tun, indem Sie die Registrierungseinstellungen ändern. 

Weitere Informationen finden Sie [unter Konfigurieren von TLS1.2 auf APS](configure-tls12-aps.md).

### <a name="hadoop-encryption-zone-support-for-polybase"></a>Hadoop-Verschlüsselungszonenunterstützung für PolyBase
PolyBase kann jetzt mit Hadoop-Verschlüsselungszonen kommunizieren. Siehe APS-Konfigurationsänderungen, die zum Konfigurieren der [Hadoop-Sicherheit](polybase-configure-hadoop-security.md#encryptionzone)erforderlich sind.

### <a name="insert-select-maxdop-options"></a>Insert-Select maxdop-Optionen
Wir haben einen [Feature-Schalter](appliance-feature-switch.md) hinzugefügt, mit dem Sie maxdop-Einstellungen größer als 1 für Insert-Select-Vorgänge auswählen können. Sie können nun die maxdop-Einstellung auf 0, 1, 2 oder 4 setzen. Der Standardwert ist 1.

> [!IMPORTANT]  
> Das Erhöhen von maxdop kann manchmal zu langsameren Vorgängen oder Deadlockfehlern führen. Ändern Sie in diesem Fall die Einstellung zurück auf maxdop 1, und wiederholen Sie den Vorgang.

### <a name="columnstore-index-health-dmv"></a>ColumnStore Indexintegrität DMV
Sie können die Integritätsinformationen des Spaltenspeicherindexes mithilfe **dm_pdw_nodes_db_column_store_row_group_physical_stats** dmv anzeigen. Verwenden Sie die folgende Ansicht, um die Fragmentierung zu bestimmen und zu entscheiden, wann ein Columnstore-Index neu erstellt oder neu organisiert werden soll.

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

### <a name="polybase-date-range-increase-for-orc-and-parquet-files"></a>Erhöhung des PolyBase-Datumsbereichs für ORC- und Parkettdateien
Das Lesen, Importieren und Exportieren von Datumsdatentypen mit PolyBase unterstützt jetzt Datumsangaben vor dem 11.01.und nach dem 2038-01-20 für ORC- und Parkettdateitypen.

### <a name="ssis-destination-adapter-for-sql-server-2017-as-target"></a>SSIS-Zieladapter für SQL Server 2017 als Ziel
Neuer APS SSIS-Zieladapter, der SQL Server 2017 als Bereitstellungsziel unterstützt, kann von der [Downloadsite](https://www.microsoft.com/download/details.aspx?id=57472)heruntergeladen werden.

<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
Veröffentlichungsdatum - Juli 2018

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>DBCC-Befehle verbrauchen keine Parallelitätsslots (Verhaltensänderung)
APS unterstützt eine Teilmenge der T-SQL [DBCC-Befehle](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql) wie [DBCC DROPCLEANBUFFERS](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql). Bis jetzt haben diese Befehle einen [Parallelitätsslot](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots) belegt, wodurch sich die Zahl der ausführbaren Benutzerauslastungen/Abfragen verringert hat. Die `DBCC` Befehle werden jetzt in einer lokalen Warteschlange ausgeführt, die keinen Benutzerparallelitätsslot verwendet, der die Gesamtleistung der Abfrageausführung verbessert.

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>Ersetzt einige Metadatenaufrufe durch Katalogobjekte
Die Verwendung von Katalogobjekten für Metadatenaufrufe anstelle von SMO hat eine Leistungsverbesserung in APS gezeigt. Ab CU7.1 verwenden einige dieser Metadatenaufrufe jetzt standardmäßig Katalogobjekte. Dieses Verhalten kann durch [den Feature-Switch](appliance-feature-switch.md) deaktiviert werden, wenn Kunden, die Metadatenabfragen verwenden, Probleme auftreten.

### <a name="bug-fixes"></a>Behebung von Programmfehlern
Wir haben ein Upgrade auf SQL Server 2016 SP2 CU2 mit APS CU7.1 durchgeführt. Das Upgrade behebt einige unten beschriebene Probleme.

| Titel | BESCHREIBUNG |
|:---|:---|
| **Potenzielle Tupel-Mover-Deadlock** |Das Upgrade behebt eine langjährige Möglichkeit eines Deadlocks in einer verteilten Transaktion und eines Tupel-Mover-Hintergrundthreads. Nach der Installation von CU7.1 können Kunden, die TF634 verwendet haben, um Tupelmover als SQL Server-Startparameter oder globales Ablaufverfolgungsflag zu stoppen, es sicher entfernen. | 
| **Bestimmte Verzögerungs-/Leadabfrage schlägt fehl** |Bestimmte Abfragen in CCI-Tabellen mit geschachtelten Verzögerungs-/Leadfunktionen, die fehlerfrei wären, werden jetzt mit diesem Upgrade behoben. | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
Veröffentlichungsdatum - Mai 2018

APS 2016 ist eine Voraussetzung für ein Upgrade auf AU7. Im Folgenden sind die neuen Funktionen in APS AU7:

### <a name="auto-create-and-auto-update-statistics"></a>Statistiken zur automatischen Erstellung und automatischen Aktualisierung
APS AU7 erstellt und aktualisiert Statistiken standardmäßig automatisch. Zum Aktualisieren der Statistikeinstellungen können Administratoren ein neues Menüelement des Feature-Switches im [Configuration Manager](appliance-configuration.md#CMTasks)verwenden. Der [Feature-Switch](appliance-feature-switch.md) steuert das Automatische Erstellen, automatische Aktualisieren und asynchrone Aktualisierungsverhalten von Statistiken. Sie können die Statistikeinstellungen auch mit der Anweisung [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) aktualisieren.

### <a name="t-sql"></a>T-SQL
Select @var wird jetzt unterstützt. Weitere Informationen finden Sie [unter Auswählen der lokalen Variablen](/sql/t-sql/language-elements/select-local-variable-transact-sql) 

Abfragehinweise HASH und ORDER GROUP werden jetzt unterstützt. Weitere Informationen finden Sie unter [Hinweise(Transact-SQL) - Abfrage](/sql/t-sql/queries/hints-transact-sql-query)

### <a name="feature-switch"></a>Feature-Schalter
APS AU7 führt Feature Switch in [Configuration Manager ein.](launch-the-configuration-manager.md) AutoStatsEnabled und DmsProcessStopMessageTimeoutInSeconds sind jetzt konfigurierbare Optionen, die von Administratoren geändert werden können.

### <a name="known-issues"></a>Bekannte Probleme
Mit der APS AU7-Software wird ein Intel BIOS-Update bereitgestellt, das ein Problem behebt, das als *spekulative Ausführungside-Channel-Angriffe*beschrieben wird. Die Angriffe zielen darauf ab, die so genannten *Spectre- und Meltdown-Schwachstellen*auszunutzen. Obwohl das BIOS-Update zusammen mit APS verpackt ist, wird es manuell installiert und nicht als Teil der APS AU7-Softwareinstallation.

Microsoft rät allen Kunden, das aktualisierte BIOS zu installieren. Microsoft hat die Auswirkungen von Kernel Virtual Address Shadowing (KVAS), Kernel Page Table Indirection (KPTI) und Indirect Branch Prediction Mitigation (IBP) auf verschiedene SQL-Workloads in verschiedenen Umgebungen gemessen. Die Messungen ergaben eine signifikante Verschlechterung bei einigen Workloads. Basierend auf den Ergebnissen empfiehlt es sich, den Leistungseffekt der Aktivierung der BIOS-Aktualisierung zu testen, bevor Sie sie in einer Produktionsumgebung bereitstellen. Siehe SQL Server-Anleitung [hier](https://support.microsoft.com/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
## <a name="aps-2016"></a>APS 2016
In diesem Abschnitt wurden die neuen Funktionen für APS 2016-AU6 beschrieben.

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 wird auf der neuesten SQL Server 2016-Version ausgeführt und verwendet die Standard-Datenbankkompatibilitätsstufe 130. SQL Server 2016 ermöglicht die Unterstützung für neue Funktionen, z. B.:

- Sekundäre Indizes für gruppierte Columnstore-Indizes.
- Kerberos für PolyBase.

### <a name="t-sql"></a>T-SQL
APS AU6 unterstützt diese T-SQL-Kompatibilitätsverbesserungen.  Diese zusätzlichen Sprachelemente erleichtern die Migration von SQL Server und anderen Datenquellen. 

- [SQL-Sortierungen][] auf Spaltenebene werden jetzt zusätzlich zu Windows-Sortierungen unterstützt.
- [Nicht gruppierte Indizes auf gruppierten Columnstore-Indizes][] verbessern die Leistung von Abfragen, die nach bestimmten Werten im gruppierten Columnstore-Index suchen. 
- [INTO-Klausel][] 
- [sp_spaceused()][] zeigt den in einer Tabelle oder Datenbank verwendeten oder reservierten Speicherplatz an.
- [Die][] Unterstützung für breite Tabellen ist die gleiche wie SQL Server 2016. Das vorherige Limit von 32 K für die Zeilengröße ist nicht mehr vorhanden. 

**Datentypen**

- [VARCHAR(MAX)][], [NVARCHAR(MAX)][] und [VARBINARY(MAX)][]. Diese LOB-Datentypen haben eine maximale Größe von 2 GB. Um diese Objekte zu laden, verwenden Sie [bcp Utility][]. PolyBase und dwloader unterstützen diese Datentypen derzeit nicht. 
- [SYSNAME][]
- [Uniqueidentifier][]
- [NUMERIC-][] und DECIMAL-Datentypen.

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

### <a name="polybasehadoop-enhancements"></a>PolyBase/Hadoop-Erweiterungen

- Kompatibilität mit Hortonworks HDP 2.4 und HDP 2.5
- Kerberos-Unterstützung über Datenbank-Zugangsdaten
- Unterstützung von Anmeldeinformationen mit Azure Storage Blobs

### <a name="install-and-upgrade-enhancements"></a>Installations- und Upgrade-Erweiterungen

**Aktualisierungen der Unternehmensarchitektur** Durch das Upgrade Ihrer vorhandenen Appliance auf APS AU6 werden die neuesten Firmware- und Treiberupdates installiert, die Sicherheitsupdates enthalten. 

Eine neue Appliance von HPE oder DELL enthält alle neuesten Updates sowie:

- Prozessorunterstützung der neuesten Generation (Broadwell)
- Update auf DDR4-DIMMs
- Verbesserter DIMM-Durchsatz

**Integration**

- Die Unterstützung für vollständig qualifizierte Domänennamen (FQDN) ermöglicht das Einrichten einer Domänenvertrauensstellung für die Appliance. 
- Um FQDN verwenden zu können, müssen Sie während des Upgrades ein vollständiges Upgrade durchführen und sich anmelden. 

**Reduzierte Ausfallzeiten** Die Installation oder Aktualisierung auf APS AU6 ist schneller und erfordert weniger Ausfallzeiten als frühere Versionen. Um Ausfallzeiten zu reduzieren, wird die Installation oder das Upgrade ausgeführt: 

 - Optimiert die Anwendung von WSUS-Updates mithilfe eines Abbilds, das alle Aktualisierungen bis Juni 2016 enthält
 - Wendet Sicherheitsupdates mit Treiber- und Firmware-Updates an
 - Platziert die neuesten Hotfixes und das Appliance Verification Utility (PAV) auf Ihrer Appliance, damit sie installiert werden können, ohne sie herunterladen zu müssen.

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[SQL-Sortierungen auf Spaltenebene]: ~/relational-databases/collations/collation-and-unicode-support.md

[Nicht gruppierte Indizes für gruppierte Columnstore-Indizes]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR(MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR(MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY(MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[INTO-Klausel]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Breite Tabellen]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp (Hilfsprogramm)]:/sql/tools/bcp-utility
[Uniqueidentifier]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[Numerischen]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS oder RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[PRÜFSUMME()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[NEWID()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  


