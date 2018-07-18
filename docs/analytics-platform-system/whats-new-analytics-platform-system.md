---
title: Neuerungen in Analytics Platform System – ein horizontaler Datawarehouse
description: Neuigkeiten in Microsoft® Analytics Platform System, die beim horizontalen hochskalieren auf lokale Anwendung, die MPP SQL Server Parallel Data Warehouse hostet.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b1eee6b3ca692c7935b061696b37842cda0f8326
ms.sourcegitcommit: 1d81c645dd4fb2f0a6f090711719528995a34583
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2018
ms.locfileid: "37137889"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Neuerungen in Analytics Platform System, das ein horizontales MPP Datawarehouse
Finden Sie unter Neues in den neuesten Appliance Updates für Microsoft® Analytics Platform System (APS). APS ist es sich um eine horizontale Skalierung auf lokale Anwendung, die MPP SQL Server Parallel Data Warehouse hostet. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"

## <a name="aps-au7"></a>APS-AU7
APS 2016 ist eine Voraussetzung für die ein Upgrade auf AU7 durchführen. Folgendes ist neu in der APS-AU7:

### <a name="auto-create-and-auto-update-statistics"></a>Automatische Erstellung und Aktualisierung von Statistiken
APS-AU7 erstellt und Statistics wird standardmäßig automatisch aktualisiert. Um statistikeinstellungen für zu aktualisieren, können Administratoren ein neues Feature-Switch-Menüelement in der [Configuration Manager](appliance-configuration.md#CMTasks). Die [featureschalter](appliance-feature-switch.md) steuert die Auto-create, automatische Aktualisierung und Verhalten der asynchronen Aktualisieren von Statistiken. Sie können auch die Einstellungen der Treiberstatistik mit aktualisieren die [ALTER DATABASE (Parallel Data Warehouse)](/sql/t-sql/statements/alter-database-parallel-data-warehouse) Anweisung.

### <a name="t-sql"></a>T-SQL
Wählen Sie @var wird jetzt unterstützt. Weitere Informationen finden Sie unter [auf lokale Variablen] (/ sql/t-sql/language-elements/select-local-variable-transact-sql) 

Abfragehinweise HASH "und" ORDER GROUP werden jetzt unterstützt. Weitere Informationen finden Sie unter [Hints(Transact-SQL) - Abfrage] (/ Sql/t-Sql/Abfragen/Hinweise-transact-Sql-Abfrage)

### <a name="feature-switch"></a>Feature-Switch
APS-AU7 führt Feature-Switch in [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled und DmsProcessStopMessageTimeoutInSeconds werden nun konfigurierbare Optionen, die von Administratoren geändert werden können.

### <a name="known-issues"></a>Bekannte Probleme
Bei APS AU7-Software, wird ein Intel BIOS-Update bereitgestellt, die als Problem behebt *seitenkanalangriffe mit spekulativer Ausführung*. Sollen, dass die Angriffe ausnutzen bezeichnet, was *Spectre und Meltdown Sicherheitsrisiken*. Zwar zusammen mit APS gepackt werden, wird die BIOS-Aktualisierung manuell installiert und nicht als Teil der APS-AU7-Softwareinstallation.

Microsoft empfiehlt, alle Kunden die BIOS-Aktualisierung installiert wird. Microsoft verfügt über die Auswirkungen der Kernel virtuelle Adresse Shadowing (KVAS), Kernel Seite Tabelle Dereferenzierung (KPTI) und indirekte Branch Vorhersage-Lösung (IBP) für verschiedene SQL-Workloads in verschiedenen Umgebungen gemessen. Die Messwerte erheblichen Leistungsabfall auf einige Workloads zu finden. Basierend auf den Ergebnissen, wird empfohlen, dass Sie die leistungsbezogenen Auswirkungen der Aktivierung von BIOS-Update vor der Bereitstellung in einer produktionsumgebung testen. Finden Sie unter SQL Server-Leitfaden [hier](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"

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
- [AUSWÄHLEN... IN][] 
- [sp_spaceused()][] zeigt, wie viel Speicherplatz verwendet oder in einer Tabelle oder Datenbank reserviert.
- [Breite Tabellen][] Unterstützung entspricht dem SQL Server 2016. Der vorherige Grenzwert von 32 KB für die Zeilengröße ist nicht mehr vorhanden. 

**Datentypen**

- [VARCHAR(max)][], [NVARCHAR(MAX)][] und [VARBINARY(MAX)][]. Diese LOB-Datentypen haben eine Maximalgröße von 2 GB. Um diese zu laden Objekten [bcp Utility][]. Polybase und Dwloader unterstützen derzeit diese Datentypen. 
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
- [ZUFALLSZAHL)][]

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
[AUSWÄHLEN... IN]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Breite Tabellen]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp Utility]:/sql/tools/bcp-utility
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
[ZUFALLSZAHL)]:/sql/t-sql/functions/rand-transact-sql


  

  


