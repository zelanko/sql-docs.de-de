---
title: Unterstützt SQL Server-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c39f03a7-e223-4fd7-bd30-142e28f51654
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 660515f10797e1f11fac22c1baf4ed74e9f67c0c
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53375032"
---
# <a name="supported-sql-server-features"></a>Unterstützte SQL Server-Funktionen
  In diesem Thema werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen erläutert, bei denen die Verwendung mit speicheroptimierten Objekte unterstützt bzw. nicht unterstützt wird.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-features-supported-for-in-memory-oltp"></a>Unterstützte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen für In-Memory OLTP  
 Die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen werden in einer Datenbank unterstützt, die speicheroptimierte Objekte enthält, einschließlich einer speicheroptimierten Dateigruppe.  
  
 Informationen zu unterstützten Datentypen finden Sie unter [Supported Data Types](supported-data-types-for-in-memory-oltp.md).  
  
-   Bei speicheroptimierten Tabellen unterstützte Optionen und Vorgänge. Weitere Informationen finden Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).  
  
-   Bei systemintern kompilierten gespeicherten Prozeduren unterstützte Optionen und Vorgänge. Weitere Informationen finden Sie unter [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).  
  
-   Fähigkeit, mit interpretiertem [!INCLUDE[tsql](../../../includes/tsql-md.md)] auf speicheroptimierte Tabellen zuzugreifen. Interpretiertes [!INCLUDE[tsql](../../../includes/tsql-md.md)] stellt eine Oberflächenentsprechung zum Zugriff auf Tabellen bereit, die nicht mithilfe von gespeicherten Prozeduren speicheroptimiert wurden, die nicht systemintern kompiliert wurden und [!INCLUDE[tsql](../../../includes/tsql-md.md)]verwenden. Weitere Informationen finden Sie unter [Zugreifen auf speicheroptimierte Tabellen mit interpretiertem Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
-   Multiversionsverwaltung und optimistische Nebenläufigkeitssteuerung. Weitere Informationen finden Sie unter [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).  
  
-   Sicherung und Wiederherstellung einer Datenbank, die eine speicheroptimierte Datendateigruppe enthält. Weitere Informationen finden Sie unter [Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
-   Katalogsichten, dynamische Verwaltungssichten und erweiterte Ereignisse für Unterstützbarkeit. Weitere Informationen finden Sie unter [Systemsichten, gespeicherte Prozeduren, DMVs und Wartetypen für In-Memory OLTP](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects. Weitere Informationen finden Sie unter [SQL Server Management Objects-Unterstützung für In-Memory OLTP](sql-server-management-objects-support-for-in-memory-oltp.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. installiert haben. Weitere Informationen finden Sie unter [SQL Server Management Studio-Unterstützung für In-Memory OLTP](sql-server-management-studio-support-for-in-memory-oltp.md).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Weitere Informationen finden Sie unter [Übersicht über SQL Server PowerShell](https://msdn.microsoft.com/library/cc281954\(SQL.105\).aspx).  
  
-   Importieren und Exportieren von Massendaten mithilfe des Hilfsprogramms bcp. Weitere Informationen finden Sie unter [Importieren und Exportieren von Massendaten mithilfe des bcp-Hilfsprogramms &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md).  
  
-   Wiederherstellung nach einem Systemabsturz.  
  
-   Mehrere Container in einer speicheroptimierten Datendateigruppe, um In-Memory OLTP-Objekte zu speichern und das Wiederherstellungszeitziel (RTO) zu reduzieren.  
  
-   Berechnung der Prüfsumme und Überprüfung durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Transaktionsprotokollblöcke.  
  
-   Der neue SNAPSHOT-Tabellenhinweis. Weitere Informationen finden Sie unter [Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).  
  
-   DB COMPAT-Ebene.  
  
-   Teilweise eigenständige Datenbank. Die Authentifizierung eigenständiger Datenbanken wird unterstützt. Allerdings werden alle In-Memory OLTP-Objekte in den "dm_db_uncontained_entities" der dynamischen Verwaltungssicht als "breaking containment" gekennzeichnet.  
  
-   Service Broker, mit Einschränkungen. Kann über eine systemintern kompilierte gespeicherte Prozedur nicht auf eine Warteschlange zugreifen. Kann in einer Transaktion, die auf speicheroptimierte Tabellen zugreift, nicht auf eine Warteschlange in einer Remotedatenbank zugreifen.  
  
-   Failoverclustering: Als Teil der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn-Angebots nutzen AlwaysOn-Failoverclusterinstanzen Windows Server Failover Clustering (WSFC)-Funktionen, um lokale hochverfügbarkeit durch Redundanz auf den Server-Instanz auf einen Failovercluster -Instanz (FCI). Weitere Informationen finden Sie unter [ Always On-Failoverclusterinstanzen (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
-   Integration in AlwaysOn: In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind mehrere Optionen zum Einrichten von Hochverfügbarkeit für einen Server oder eine Datenbank, einschließlich AlwaysOn, verfügbar. Weitere Informationen finden Sie unter [Lösungen mit hoher Verfügbarkeit &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md).  
  
-   Protokollversand: Mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Protokollversand können Sie Transaktionsprotokollsicherungen von einer primären Datenbank auf einer primären Serverinstanz automatisch an eine oder mehrere sekundäre Datenbanken auf getrennten sekundären Serverinstanzen senden. Weitere Informationen finden Sie unter [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
-   Die Transaktionsreplikation in speicheroptimierte Tabellen auf Abonnenten wird eingeschränkt unterstützt. Weitere Informationen finden Sie unter [Replikation mit Abonnenten von speicheroptimierten Tabellen](../replication/replication-to-memory-optimized-table-subscribers.md).  
  
-   Ressourcenkontrolle: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resource Governor ist ein Feature, das Sie verwenden können, zum Verwalten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] arbeitsauslastung und den Systemressourcenverbrauch. Über die Ressourcenkontrolle legen Sie Grenzwerte für die CPU, physische E/A sowie den Arbeitsspeicher fest, die für eingehende Anwendungsanforderungen zur Verfügung stehen. Weitere Informationen finden Sie unter [Managing Memory for In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md) und [Resource Governor](../resource-governor/resource-governor.md).  
  
-   In-Memory OLTP weist Einschränkungen für unterstützte Codepages für (var)char-Spalten in speicheroptimierten Tabellen und unterstützten Sortierungen auf, die in Indizes und in systemintern kompilierten gespeicherten Prozeduren verwendet werden. Weitere Informationen finden Sie unter [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).  
  
-   BACPAC-Unterstützung.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-features-not-supported-for-in-memory-oltp"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen, die für In-Memory-OLTP nicht unterstützt werden  
 Die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen werden in einer Datenbank nicht unterstützt, die speicheroptimierte Objekte (einschließlich einer speicheroptimierten Dateigruppe) enthält.  
  
|Nicht unterstützte Funktion|Funktionsbeschreibung|  
|-------------------------|-------------------------|  
|Datenkomprimierung bei speicheroptimierten Tabellen|Sie können die Datenkomprimierungsfunktion verwenden, um die Komprimierung der Daten innerhalb einer Datenbank sowie die Reduzierung der Datenbankgröße zu vereinfachen. Weitere Informationen finden Sie unter [Data Compression](../data-compression/data-compression.md).|  
|Partitionierung von speicheroptimierten Tabellen und HASH-Indizes.|Die Daten partitionierter Tabellen und Indizes werden in Einheiten aufgeteilt, die über mehrere Dateigruppen in einer Datenbank verteilt sein können. Weitere Informationen finden Sie unter [partitionierte Tabellen und Indizes](../partitions/partitioned-tables-and-indexes.md).|  
|Die transparente Datenverschlüsselung (TDE) für die speicheroptimierte Datendateigruppe einer Datenbank.|Die transparente Datenverschlüsselung (TDE) führt die E/A-Verschlüsselung und -Entschlüsselung der Daten und der Protokolldateien in Echtzeit durch. Weitere Informationen finden Sie unter [Transparente Datenverschlüsselung &#40;TDE&#41;](../security/encryption/transparent-data-encryption.md).<br /><br /> TDE kann auf einer Datenbank aktiviert werden, die über In-Memory OLTP-Objekte verfügt. In-Memory OLTP-Protokolldatensätze werden verschlüsselt, wenn TDE aktiviert ist. Die Prüfpunktdateien für permanente Tabellen werden nicht verschlüsselt, auch wenn TDE für die Datenbank aktiviert ist.|  
|Replikation|Replikationskonfigurationen, die keine Transaktionsreplikation in speicheroptimierte Tabellen auf Abonnenten darstellen, sind mit Tabellen oder Sichten, die auf speicheroptimierte Tabellen verweisen, nicht kompatibel. Replikation mit Sync_mode = 'Database Snapshot' wird nicht unterstützt, wenn eine Speicheroptimierte Dateigruppe vorhanden ist. Weitere Informationen finden Sie unter [Replikation mit Abonnenten von speicheroptimierten Tabellen](../replication/replication-to-memory-optimized-table-subscribers.md).|  
|Multiple Active Result Sets (MARS)|Multiple Active Result Sets (MARS) werden für speicheroptimierte Tabellen nicht unterstützt. Dieser Fehler kann auch auf die Verwendung eines Verbindungsservers hinweisen. Ein Verbindungsserver kann MARS verwenden. Verbindungsserver werden für speicheroptimierte Tabellen nicht unterstützt. Stattdessen müssen Sie eine direkte Verbindung mit dem Server und der Datenbank herstellen, die die speicheroptimierten Tabellen hostet.|  
|Spiegelung|Die Datenbankspiegelung ist eine Lösung zum Verbessern der Verfügbarkeit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank. Weitere Informationen finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).|  
|Protokollneuerstellung|Die Neuerstellung des Protokolls, entweder durch Anfügen oder mithilfe von ALTER DATABASE, wird für Datenbanken mit einer MEMORY_OPTIMIZED_DATA-Dateigruppe nicht unterstützt.|  
|Verbindungsserver|Weitere Informationen finden Sie unter [Verbindungsserver &#40;Datenbank-Engine&#41;](../linked-servers/linked-servers-database-engine.md).|  
|Massenprotokollierung|Unabhängig vom Wiederherstellungsmodell der Datenbank werden alle Vorgänge in dauerhaften speicheroptimierten Tabellen immer vollständig protokolliert.|  
|Minimale Protokollierung|Die minimale Protokollierung wird für speicheroptimierte Tabellen nicht unterstützt. Weitere Informationen zur minimalen Protokollierung finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) und [Voraussetzungen für die minimale Protokollierung beim Massenimport](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).|  
|Änderungsnachverfolgung|Die Änderungsnachverfolgung kann in einer Datenbank mit In-Memory OLTP-Objekten aktiviert werden. Änderungen in speicheroptimierten Tabellen werden allerdings nicht nachverfolgt.|  
|DDL-Trigger|DDL-Trigger auf Datenbankebene und Serverebene werden bei In-Memory OLTP-Tabellen und systemintern kompilierten gespeicherten Prozeduren nicht unterstützt.|  
|Change Data Capture (CDC)|CDC sollte nicht für eine Datenbank aktiviert werden, die über In-Memory OLTP-Objekte verfügt, da es bestimmte Vorgänge wie DROP verhindert.|  
|Datenbankkapselung|Datenbankkapselung wird nicht in Datenbanken unterstützt, die über systemintern kompilierte gespeicherte Prozeduren und speicheroptimierte Tabellen verfügen. Weitere Informationen finden Sie unter [Contained Databases](../databases/contained-databases.md).|  
|Kontextverbindungen|Zugreifen auf speicheroptimierte Tabellen mithilfe der Kontextverbindung aus CLR-gespeicherten Prozeduren wird nicht unterstützt.|  
|Cursor|Keysetgesteuerte und dynamische Cursor für Abfragen, die auf speicheroptimierte Tabellen zugreifen. Diese Abfragen werden zu "statisch" herabgestuft und sind schreibgeschützt.|  
|TABLESTAMP|TABLESTAMP wird nicht unterstützt. Weitere Informationen finden Sie unter [FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql).|  
|AUTO_CLOSE|AUTO_CLOSE wird nicht unterstützt. Weitere Informationen finden Sie unter [Set the AUTO_CLOSE Database Option to OFF](../policy-based-management/set-the-auto-close-database-option-to-off.md).|  
|Datenbank-Momentaufnahmen|Datenbankmomentaufnahmen werden nicht unterstützt. Weitere Informationen finden Sie unter [Datenbankmomentaufnahmen &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).|  
|Transaktions-DDL|Transaktions-DDL wird in In-Memory OLTP nicht unterstützt.|  
|Ereignisbenachrichtigungen|Ereignisbenachrichtigungen werden nicht unterstützt. Weitere Informationen finden Sie unter [Event Notifications](../service-broker/event-notifications.md).|  
|Fibermodus|Der Fibermodus wird für In-Memory OLTP nicht unterstützt.|  
|Richtlinienbasierte Verwaltung.|Der "Prevent"- und der "Log Only"-Modus der richtlinienbasierten Verwaltung werden nicht unterstützt. Das Vorhandensein solcher Richtlinien auf dem Server verhindert möglicherweise, dass In-Memory OLTP-DDL erfolgreich ausgeführt wird. Der "On Demand"- und der "On Schedule"-Modus werden unterstützt.|  
|DACFX deploy/extract|Das Bereitstellen oder Extrahieren von DAC Framework wird in In-Memory OLTP nicht unterstützt.|  
  
 Datenbankübergreifende Transaktionen werden bis auf einige Ausnahmen nicht unterstützt. In der folgenden Tabelle werden unterstützte Szenarien und entsprechende Einschränkungen beschrieben. (Siehe auch [Datenbankübergreifende Abfragen](cross-database-queries.md).)  
  
|Datenbanken|Zulässig|Description|  
|---------------|-------------|-----------------|  
|Benutzerdatenbanken, Modell- und msdb-Datenbank|Nein|Datenbankübergreifende Abfragen und Transaktionen werden nicht unterstützt.<br /><br /> Abfragen und Transaktionen, die auf speicheroptimierte Tabellen oder systemintern kompilierte gespeicherte Prozeduren zugreifen, können nicht auf andere Datenbanken zugreifen. Eine Ausnahme bilden der Systemdatenbankmaster (schreibgeschützter Zugriff) und "tempdb".|  
|Ressourcendatenbank und tempdb|Ja|Es gibt keine Einschränkungen für datenbankübergreifende Transaktionen, die, außer bei einer einzelnen Benutzerdatenbank, nur die Ressourcendatenbank und tempdb verwenden.|  
|master|Schreibgeschützt|Für datenbankübergreifende Transaktionen, die In-Memory OLTP und die Masterdatenbank betreffen, wird kein Commit ausgeführt, wenn Schreibvorgänge in die Masterdatenbank enthalten sind. Datenbankübergreifende Transaktionen, die nur vom Master lesen und nur eine Benutzerdatenbank verwenden, sind zulässig.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Unterstützung für In-Memory OLTP](sql-server-support-for-in-memory-oltp.md)  
  
  
