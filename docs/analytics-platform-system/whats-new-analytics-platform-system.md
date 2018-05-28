---
title: Was ist neu in Analytics Platform System – ein horizontaler Datawarehouse
description: Neuigkeiten in Microsoft® Analytics Platform System angezeigt wird, eine horizontale Skalierung einer lokalen Anwendung, die MPP SQL Server Parallel Data Warehouse hostet.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c2408e84e7ff81f54ad00a98f85cd8dce7b04131
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Was ist neu in Analytics Platform System ein horizontaler MPP Datawarehouse
Neuigkeiten Sie in der aktuellen Einheit Updates für Microsoft® Analytics Platform System (APS). APS ist ein lokaler mit horizontaler Skalierung, die MPP SQL Server Parallel Data Warehouse hostet. 


## <a name="aps-au7"></a>APS-AU7
APS2016 ist eine Voraussetzung für die Aktualisierung auf AU7. Es folgen die neuen Funktionen für APS AU7:

### <a name="auto-create-and-auto-update-statistics"></a>Erstellen Sie automatisch "und" Statistiken automatisch aktualisieren
APS-AU7 erstellt und aktualisiert die Statistiken automatisch standardmäßig. Um Einstellungen für Statistiken zu aktualisieren, können Administratoren ein neues Feature-Switch Menüelement in der [Configuration Manager](appliance-configuration.md#CMTasks). Die [funktionsschalter](appliance-feature-switch.md) steuert die Auto-create, automatische Aktualisierung und Verhalten von asynchronen Aktualisieren von Statistiken. Sie können auch die Einstellungen der Treiberstatistik mit Aktualisieren der [ALTER DATABASE (Parallel Data Warehouse)](/sql/t-sql/statements/alter-database-parallel-data-warehouse) Anweisung.

### <a name="t-sql"></a>T-SQL
Wählen Sie @var wird jetzt unterstützt. Weitere Informationen finden Sie unter [select lokale Variable] (/ sql/t-sql/language-elements/select-local-variable-transact-sql) 

Abfragehinweise HASH und ORDER GROUP werden jetzt unterstützt. Weitere Informationen finden Sie unter [Hints(Transact-SQL) - Abfrage] (/ Sql/t-Sql/Abfragen/Hinweise-transact-Sql-Abfrage)

### <a name="feature-switch"></a>Feature-Switch
APS-AU7 führt Feature-Switch in [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled und DmsProcessStopMessageTimeoutInSeconds sind jetzt die konfigurierbare Optionen, die von Administratoren geändert werden können.

### <a name="known-issues"></a>Bekannte Probleme
Mit der APS-AU7 Software sind wir Verpacken und Bereitstellen der Intel-BIOS-Update, das behoben werden "seitenkanalangriffe spekulative Ausführung" (Alias) Absorptionsspektrum und überdauern Sicherheitsrisiken). Obwohl zusammengefasst, wird die BIOS-Aktualisierung manuell installiert und nicht Teil der APS-AU7-Software installieren. Microsoft empfiehlt, alle Kunden, die BIOS-Aktualisierung zu installieren. Microsoft hat die Auswirkung der Kernel virtuelle Adresse Shadowing (KVAS), Kernel Seite Tabelle Dereferenzierung (KPTI) und indirekte Verzweigung Vorhersage Entschärfung (IBP) auf verschiedenen SQL-Arbeitslasten in verschiedenen Umgebungen gemessen und signifikanten Einbußen hinsichtlich auf einige gefunden Arbeitslasten. Es wird empfohlen, zu, die Auswirkung auf die Leistung Testen der BIOS-Update aktivieren, bevor Sie sie in einer produktionsumgebung bereitstellen. Wenn die Auswirkung auf die Leistung dieser Funktionen aktivieren für eine vorhandene Anwendung zu hoch ist, können Sie Wägen Sie, ob Isolieren der APS-Appliance aus nicht vertrauenswürdigen Code ausgeführt wird eine bessere Lösung für Ihre Anwendung. Siehe SQL Server-Leitfaden [hier](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

## <a name="aps-2016"></a>APS-2016
Dies sind die neuen Funktionen für APS 2016:

### <a name="sql-server-2016"></a>SQL Server 2016

APS 2016 wird auf die neueste Version von SQL Server 2016 ausgeführt und verwendet die standardmäßige Datenbank-Kompatibilitätsgrad 130 zur Verfügung.  SQL Server 2016 ermöglicht einige der neuen Features wie z. B. sekundäre Indizes für gruppierte columnstore-Indizes und Kerberos für PolyBase unterstützen. 


### <a name="t-sql"></a>T-SQL
APS-2016 unterstützt diese Verbesserungen der T-SQL-Kompatibilität.  Diese zusätzliche Sprachelemente vereinfachen die Migration von SQL Server und anderen Datenquellen. 

- [SQL-Sortierungen auf Spaltenebene][] werden jetzt zusätzlich zu den Windows-Sortierungen unterstützt.
- [Nicht gruppierte Indizes für gruppierte columnstore-Indizes][] Umfang zur Leistungssteigerung von Abfragen, Suchen nach bestimmten Werten in den gruppierten columnstore-Index. 
- [WÄHLEN SIE... IN][] 
- [sp_spaceused()][] zeigt der Speicherplatz verwendet, oder in einer Tabelle oder Datenbank reserviert.
- [Breite Tabellen][] Unterstützung entspricht dem SQL Server 2016. Das vorherige Limit von 32 KB für die Zeilengröße ist nicht mehr vorhanden. 

**Datentypen**

- [VARCHAR(max)][], [NVARCHAR(MAX)][] und [VARBINARY(MAX)][]. Diese LOB-Datentypen haben eine Maximalgröße von 2 GB. Laden Sie diese Objekte verwenden [bcp Utility][]. Polybase und Dwloader unterstützen derzeit diese Datentypen. 
- [SYSNAME][]
- ["UNIQUEIDENTIFIER"][]
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

### <a name="polybasehadoop-enhancements"></a>PolyBase-Hadoop-Erweiterungen

- Kompatibilität mit Hortonworks HDP 2.4 und HDP 2.5
- Unterstützung für Kerberos über datenbankweit gültige Anmeldeinformationen
- Unterstützung von Anmeldeinformationen mit Azure-Speicher-Blobs

### <a name="install-and-upgrade-enhancements"></a>Installation und Upgrade-Erweiterungen

**Enterprise-Architektur Updates** ein Upgrade Ihrer vorhandene Appliance auf APS 2016 installiert die neuesten Firmware- und Treiberupdates zu erhalten, darunter Sicherheitsupdates. 

Eine neue Einheit von DELL oder HPE enthält die neuesten Updates plus:

- Aktuelle Generation-Prozessor-Unterstützung (Broadwell)
- Aktualisieren auf DDR4 DIMM
- Verbesserte DIMM-Durchsatz

**Integration**

- Vollständig vereinfacht qualifizierten Domänennamen (FQDN)-Unterstützung zum Einrichten einer Vertrauensstellung mit der Einheit. 
- Um FQDN verwenden, müssen Sie führen eine vollständige Aktualisierung und während des Upgrades teilnehmen. 

**Verringerte Ausfallzeiten** installieren oder Aktualisieren von auf APS 2016 ist schneller und erfordert weniger Ausfallzeiten als in vorherigen Versionen. Reduzieren von Ausfallzeiten, die zum Installieren oder aktualisieren: 

 - Anwenden von WSUS-Updates mithilfe eines Bildes optimiert enthält, die alle Updates bis Juni 2016
 - Wendet die Sicherheits-Updates mit den Treiber und Firmware-updates
 - Fügt die neuesten Hotfixes und das Dienstprogramm zum Überprüfen der Appliance (PAV) auf Ihrem Gerät, sodass Sie sie bereit zum Installieren von mit nicht erforderlich, um sie herunterzuladen sind.


<!--MSDN references-->
[database compatibility level 130]:/sql/t-sql/statements/alter-database-transact-sql-compatibility-level
[SQL-Sortierungen auf Spaltenebene]:/sql/relational-databases/collations/collation-and-unicode-support
[Nicht gruppierte Indizes für gruppierte columnstore-Indizes]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR(MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR(MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY(MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[WÄHLEN SIE... IN]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Breite Tabellen]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp Utility]:/sql/tools/bcp-utility
["UNIQUEIDENTIFIER"]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
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


  

  


