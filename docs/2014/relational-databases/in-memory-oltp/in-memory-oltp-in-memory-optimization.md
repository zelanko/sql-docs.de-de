---
title: In-Memory OLTP (Arbeitsspeicheroptimierung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- In-Memory OLTP
- memory-optimized tables
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
author: rothja
ms.author: jroth
ms.openlocfilehash: 22faed7d9505c1ad487b5300a46a565379512091
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050157"
---
# <a name="in-memory-oltp-in-memory-optimization"></a>In-Memory OLTP (Arbeitsspeicheroptimierung)

  [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]wurde in [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] neu eingeführt und kann die Leistung der OLTP-Datenbank erheblich verbessern. [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] ist eine speicheroptimierte Datenbank-Engine, die in die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Engine integriert und für OLTP optimiert wurde.

|||
|-|-|
|![Virtueller Azure-Computer](../../master-data-services/media/azure-virtual-machine.png "Virtueller Azure-Computer")|Möchten Sie SQL Server 2016 testen? Melden Sie sich für Microsoft Azure an, und wechseln Sie dann **[hier](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftsqlserver.sql2017-ws2019?tab=Overview)** , um einen virtuellen Computer zu starten, auf dem bereits SQL Server 2016 installiert ist. Sie können den virtuellen Computer löschen, wenn Sie fertig sind.|

 Zur Verwendung von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]definieren Sie eine Tabelle, auf die viel zugegriffen wird, als speicheroptimiert. Speicheroptimierte Tabellen sind vollständig transaktionsfähig und dauerhaft, und der Zugriff erfolgt genau wie bei datenträgerbasierten Tabellen über [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Eine Abfrage kann sowohl auf speicheroptimierte Tabellen als auch auf datenträgerbasierte Tabellen verweisen. Eine Transaktion kann Daten in speicheroptimierten Tabellen und in datenträgerbasierten Tabellen aktualisieren. Gespeicherte Prozeduren, die nur auf speicheroptimierte Tabellen verweisen, können zur weiteren Leistungsverbesserung systemintern in Computercode kompiliert werden. Die [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]-Engine ist für außerordentlich hohe Sitzungsparallelität für Transaktionen vom OLTP-Typ konzipiert, die von einer hochgradigen Skalierung auf mittlerer Ebene gesteuert werden. Um dies zu erreichen, werden Datenstrukturen ohne Latches, jedoch mit Multiversionsverwaltung und optimistischer Nebenläufigkeitssteuerung verwendet. Das Ergebnis ist eine vorhersehbare niedrige Latenz unter einer Millisekunde sowie ein hoher Durchsatz mit linearer Skalierung für Datenbanktransaktionen. Der tatsächliche Leistungszuwachs hängt von vielen Faktoren ab, jedoch kann mit Leistungsverbesserungen um das 5- bis 20-fache gerechnet werden.

 In der folgenden Tabelle sind die Arbeitsauslastungsmuster aufgeführt, die am meisten von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]profitieren:

|Implementierungsszenario|Implementierungsszenario|Vorteile von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]|
|-----------------------------|-----------------------------|-------------------------------------|
|Hohe Dateneinfügungsrate durch mehrere gleichzeitige Verbindungen|Hauptsächlich Nur anhängen-Speicherung<br /><br /> Nicht in der Lage, mit der Einfügen-Arbeitslast Schritt zu halten|Konfliktbeseitigung<br /><br /> Reduzierung der Protokollierung|
|Leseleistung und Skalierung mit periodischen Batcheinfügungen und -updates|Hochleistungs-Lesevorgänge, besonders wenn jede Serveranforderung mehrere Lesevorgänge ausführen muss<br /><br /> Skalierungsanforderungen können nicht erfüllt werden|Konfliktbeseitigung beim Eintreffen neuer Daten<br /><br /> Niedrigere Latenz bei Datenabruf<br /><br /> Minimierung der Codeausführungszeit|
|Intensive Geschäftslogikverarbeitung im Datenbankserver|Einfügen, Aktualisieren und Löschen der Arbeitslast<br /><br /> Intensive Berechnungsvorgänge innerhalb von gespeicherten Prozeduren<br /><br /> Lese-/Schreibkonflikte|Konfliktbeseitigung<br /><br /> Minimierung der Codeausführungszeit für reduzierte Latenz und verbesserten Durchsatz|
|Niedrige Latenz|Erfordert Geschäftstransaktionen mit niedriger Latenz, die typische Datenbanklösungen nicht erzielen können|Konfliktbeseitigung<br /><br /> Minimierung der Codeausführungszeit<br /><br /> Codeausführungszeit mit niedriger Latenz<br /><br /> Effizienter Datenabruf|
|Sitzungsstatusverwaltung|Häufige Einfügungen, Aktualisierungen und Punktsuchen<br /><br /> Hohe Skalierungslast durch zahlreiche statuslose Webserver|Konfliktbeseitigung<br /><br /> Effizienter Datenabruf<br /><br /> Optionale E/A-Reduzierung oder Eliminierung durch Verwendung von nicht dauerhaften Tabellen|

 Weitere Informationen zu Szenarien, in denen zu [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] den größten Leistungssteigerungen führt, finden Sie unter [in-Memory OLTP-allgemeine Arbeits Auslastungs Muster und Überlegungen zur Migration](https://msdn.microsoft.com/library/dn673538.aspx).

 Durch [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] wird die Leistung vor allem bei OLTP-Transaktionen mit kurzer Ausführungsdauer verbessert.

 Zu den Programmierschemata, die durch [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] optimiert werden, zählen Parallelitätsszenarien, Punktsuchen, Arbeitsauslastungen mit vielen Einfügungen und Updates sowie Geschäftslogik in gespeicherten Prozeduren.

 Durch die Integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Sie speicheroptimierte Tabellen und datenträgerbasierte Tabellen in derselben Datenbank verwenden und Abfragen über beide Tabellentypen ausführen.

 In [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] gibt es Einschränkungen bei der [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Oberfläche, die für [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]unterstützt wird.

 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] erzielt signifikante Leistungs- und Skalierbarkeitsgewinne, indem Folgendes verwendet wird:

-   Algorithmen, die für den Zugriff auf arbeitsspeicherresidente Daten optimiert sind.

-   Optimistische Nebenläufigkeitssteuerung, die logische Sperren entfernt.

-   Sperren von freien Objekten, die alle physischen Sperren und Latches eliminieren. Threads, die Transaktions Aufgaben ausführen, verwenden keine Sperren oder Latches für die Parallelitäts Steuerung.

-   Systemintern kompilierte gespeicherte Prozeduren, die beim Zugriff auf speicheroptimierte Tabellen deutlich bessere Leistung als interpretierte gespeicherte Prozeduren zeigen.

> [!IMPORTANT]
>  Um [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]verwenden zu können, sind einige Syntaxänderungen an den Tabellen und gespeicherten Prozeduren erforderlich. Weitere Informationen finden Sie unter [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md). Bevor Sie versuchen, eine datenträgerbasierte Tabelle zu einer speicheroptimierten Tabelle zu migrieren, informieren Sie sich unter [Bestimmen, ob eine Tabelle oder eine gespeicherte Prozedur zu In-Memory OLTP portiert werden soll](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) darüber, welche Tabellen und gespeicherten Prozeduren von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] profitieren.

## <a name="in-this-section"></a>In diesem Abschnitt
 In diesem Abschnitt finden Sie Informationen zu den folgenden Konzepten:

|Thema|BESCHREIBUNG|
|-----------|-----------------|
|[Anforderungen für die Verwendung von speicheroptimierten Tabellen](memory-optimized-tables.md)|Erläutert Hardware- und Softwareanforderungen und Richtlinien zum Verwenden von speicheroptimierten Tabellen.|
|[Verwenden von In-Memory-OLTP in einer VM-Umgebung](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)|Erläutert die Verwendung von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] in einer virtualisierten Umgebung.|
|[Codebeispiele für In-Memory OLTP](in-memory-oltp-code-samples.md)|Enthält Codebeispiele, die das Erstellen und Verwenden einer speicheroptimierten Tabelle veranschaulichen.|
|[Speicheroptimierte Tabellen](memory-optimized-tables.md)|Bietet eine Einführung in speicheroptimierte Tabellen.|
|[Speicher optimierte Tabellen Variablen](../../database-engine/memory-optimized-table-variables.md)|Ein Codebeispiel, das veranschaulicht, wie eine speicheroptimierte Tabellenvariable anstelle einer herkömmlichen Tabellenvariable verwendet wird, um die Verwendung von tempdb zu reduzieren.|
|[Indizes für Speicher optimierte Tabellen](../../database-engine/indexes-on-memory-optimized-tables.md)|Bietet eine Einführung in speicheroptimierte Indizes.|
|[System intern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)|Führt systemintern kompilierte gespeicherte Prozeduren ein.|
|[Verwalten des Arbeitsspeichers für In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md)|Erläutert die Funktionsweise und Verwaltung der Speicherverwendung im System.|
|[Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)|Erläutert Daten- und Änderungsdateien, die Informationen zu Transaktionen in speicheroptimierten Tabellen speichern.|
|[Sichern und Wiederherstellen speicheroptimierter Tabellen](restore-and-recovery-of-memory-optimized-tables.md)|Erläutert die Sicherung und Wiederherstellung von speicheroptimierten Tabellen.|
|[Transact-SQL-Unterstützung für In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md)|Erläutert die [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Unterstützung für [!INCLUDE[hek_2](../../../includes/hek-2-md.md)].|
|[Unterstützung für Hochverfügbarkeit für In-Memory OLTP-Datenbanken](high-availability-support-for-in-memory-oltp-databases.md)|Erläutert Verfügbarkeitsgruppen und Failoverclustering in [!INCLUDE[hek_2](../../../includes/hek-2-md.md)].|
|[SQL Server-Unterstützung für In-Memory OLTP](sql-server-support-for-in-memory-oltp.md)|Listet neue und aktualisierte Syntax und Funktionen auf, die speicheroptimierte Tabellen unterstützen.|
|[Migrieren zu in-Memory-OLTP](migrating-to-in-memory-oltp.md)|Erläutert, wie datenträgerbasierte Tabellen zu speicheroptimierten Tabellen migriert werden.|

 Weitere Informationen zu [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] finden Sie unter:

-   [Microsoft? SQL Server?? 2014-Produkthandbuch](https://www.microsoft.com/download/confirmation.aspx?id=39269)

-   [In-Memory-OLTP-Blog](https://cloudblogs.microsoft.com/sqlserver/2013/06/26/sql-server-2014-in-memory-technologies-blog-series-introduction/)

-   [In-Memory-OLTP-allgemeine Arbeits Auslastungs Muster und Migrations Überlegungen](https://msdn.microsoft.com/library/dn673538.aspx)

-   [Übersicht über die Merkmale von SQL Server In-Memory OLTP](https://download.microsoft.com/download/8/3/6/8360731A-A27C-4684-BC88-FC7B5849A133/SQL_Server_2016_In_Memory_OLTP_White_Paper.pdf)
    <!--
         (https://download.microsoft.com/download/8/3/6/8360731A-A27C-4684-BC88-FC7B5849A133/SQL_Server_2016_In_Memory_OLTP_White_Paper.pdf)
         (/sql/relational-databases/in-memory-oltp/sql-server-in-memory-oltp-internals-for-sql-server-2016?view=sql-server-2016)
    -->

## <a name="see-also"></a>Weitere Informationen
 [Datenbankfunktionen](../database-features.md)


