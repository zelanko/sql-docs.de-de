---
title: In-Memory OLTP (Arbeitsspeicheroptimierung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- In-Memory OLTP
- memory-optimized tables
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 87ad093d5be6f4fa394e934e6c0d88796a22e196
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74401651"
---
# <a name="in-memory-oltp-and-memory-optimization"></a>In-Memory-OLTP und Arbeitsspeicheroptimierung

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] kann die Leistung beim Verarbeiten von Transaktionen, Erfassen und Laden von Daten sowie in vorübergehenden Datenszenarien erheblich verbessern.  Informationen zum grundlegenden Code und Wissen, den bzw. das Sie für einen schnellen Test Ihrer eigenen speicheroptimierten Tabelle und nativ kompilierten gespeicherten Prozedur benötigen, finden Sie unter
 -  [Schnellstart 1: In-Memory-OLTP-Technologien für höhere Transact-SQL-Leistung](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md).  
 
Wir haben ein [**17-minütiges Video**](#anchorname-17minute-video) auf YouTube hochgeladen, das In-Memory-OLTP für SQL Server erläutert und die Leistungsvorteile aufzeigt.

Eine detailliertere Übersicht über In-Memory-OLTP und die Szenarien, in denen die Technologie Leistungsvorteile bringt, finden Sie unter:

- [Übersicht und Verwendungsszenarien](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)
 
 Beachten Sie, dass [!INCLUDE[hek_2](../../includes/hek-2-md.md)] die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Technologie zur Verbesserung der Leistung der Transaktionsverarbeitung ist. Zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Technologie, die die Leistung von Berichts- und Analyseabfragen verbessert, siehe [Beschreibung von Columnstore-Indizes](../../relational-databases/indexes/columnstore-indexes-overview.md).
  
 Mehrere Verbesserungen wurden an In-Memory-OLTP sowohl in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] als auch in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] vorgenommen. Die Transact-SQL-Oberfläche wurde verbessert, um das Migrieren von Datenbanken zu vereinfachen. Unterstützung für die Ausführung von ALTER-Vorgängen für speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren wurde hinzugefügt, um Anwendungen einfacher zu verwalten.
  
> [!NOTE]  
>  **Ausprobieren**  
>   
>  In-Memory OLTP ist in den SQL-Datenbank- und elastischen Pool-Tarifen Premium und Unternehmenskritisch verfügbar. Zum Einstieg in In-Memory-OLTP sowie Columnstore in Azure SQL-Datenbank finden Sie Informationen unter [Optimieren der Leistung mithilfe von In-Memory-Technologien in SQL-Datenbank](https://azure.microsoft.com/documentation/articles/sql-database-in-memory/).  
  

## <a name="in-this-section"></a>In diesem Abschnitt  
 Dieser Abschnitt enthält die folgenden Themen:  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Schnellstart 1: In-Memory-OLTP-Technologien für höhere Transact-SQL-Leistung](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)|Tauchen Sie direkt in In-Memory-OLTP ein.|
|[Übersicht und Verwendungsszenarien](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)|Übersicht über die Aufgaben von In-Memory-OLTP und die Szenarien, die hinsichtlich Leistung davon profitieren.|
|[Anforderungen für die Verwendung speicheroptimierter Tabellen](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)|Erläutert Hardware- und Softwareanforderungen und Richtlinien zum Verwenden von speicheroptimierten Tabellen.|  
|[Codebeispiele für In-Memory OLTP](../../relational-databases/in-memory-oltp/in-memory-oltp-code-samples.md)|Enthält Codebeispiele, die das Erstellen und Verwenden einer speicheroptimierten Tabelle veranschaulichen.|  
|[Speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)|Bietet eine Einführung in speicheroptimierte Tabellen.|  
|[Speicheroptimierte Tabellenvariablen](https://msdn.microsoft.com/library/bd102e95-53e2-4da6-9b8b-0e4f02d286d3)|Ein Codebeispiel, das veranschaulicht, wie eine speicheroptimierte Tabellenvariable anstelle einer herkömmlichen Tabellenvariable verwendet wird, um die Verwendung von tempdb zu reduzieren.|  
|[Indizes für speicheroptimierte Tabellen](https://msdn.microsoft.com/library/86805eeb-6972-45d8-8369-16ededc535c7)|Bietet eine Einführung in speicheroptimierte Indizes.|  
|[Nativ kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)|Führt systemintern kompilierte gespeicherte Prozeduren ein.|  
|[Verwalten des Arbeitsspeichers für In-Memory-OLTP](https://msdn.microsoft.com/library/d82f21fa-6be1-4723-a72e-f2526fafd1b6)|Erläutert die Funktionsweise und Verwaltung der Speicherverwendung im System.|  
|[Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)|Erläutert Daten- und Änderungsdateien, die Informationen zu Transaktionen in speicheroptimierten Tabellen speichern.|  
|[Sichern und Wiederherstellen speicheroptimierter Tabellen](https://msdn.microsoft.com/library/3f083347-0fbb-4b19-a6fb-1818d545e281)|Erläutert die Sicherung und Wiederherstellung von speicheroptimierten Tabellen.|  
|[Transact-SQL-Unterstützung für OLTP im Arbeitsspeicher](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)|Erläutert die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Unterstützung für [!INCLUDE[hek_2](../../includes/hek-2-md.md)].|  
|[Unterstützung für Hochverfügbarkeit für In-Memory OLTP-Datenbanken](../../relational-databases/in-memory-oltp/high-availability-support-for-in-memory-oltp-databases.md)|Erläutert Verfügbarkeitsgruppen und Failoverclustering in [!INCLUDE[hek_2](../../includes/hek-2-md.md)].|  
|[SQL Server-Unterstützung für In-Memory OLTP](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)|Listet neue und aktualisierte Syntax und Funktionen auf, die speicheroptimierte Tabellen unterstützen.|  
|[Migrieren zu In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)|Erläutert, wie datenträgerbasierte Tabellen zu speicheroptimierten Tabellen migriert werden.|  
| &nbsp; | &nbsp; |

## <a name="links-to-other-websites"></a>Links zu anderen Websites

Dieser Abschnitt enthält Links zu anderen Websites, die Informationen zu In-Memory-OLTP für SQL Server enthalten.

- [**Video**, in dem In-Memory-OLTP erläutert wird und Leistungsvorteile veranschaulicht werden](#anchorname-17minute-video)

- [In-Memory OLTP Performance Demo v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)

-   [SQL Server In-Memory-OLTP: Internes technisches Whitepaper](https://msdn.microsoft.com/library/mt764316.aspx)  

-   [Vergleich zwischen SQL Server In-Memory-OLTP und Columnstore-Funktion](https://download.microsoft.com/download/D/0/0/D0075580-6D72-403D-8B4D-C3BD88D58CE4/SQL_Server_2016_In_Memory_OLTP_and_Columnstore_Comparison_White_Paper.pdf)

-   Neuigkeiten bei In-Memory-OLTP in SQL Server 2016 – [Teil 1](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/11/12/in-memory-oltp-whats-new-in-sql2016-ctp3/) und [Teil 2](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/25/whats-new-for-in-memory-oltp-in-sql-server-2016-since-ctp3/)
  
-   [In-Memory OLTP - Common Workload Patterns and Migration Considerations (In-Memory-OLTP: Allgemeine Workloadmuster und Überlegungen zur Migration)](https://msdn.microsoft.com/library/dn673538.aspx)  
  
-   [In-Memory-OLTP-Blog](https://go.microsoft.com/fwlink/?LinkId=311696)  

## <a name="anchorname-17minute-video"></a>17-minütiges Video, indiziert

- _Videotitel:_ &nbsp; **In-Memory-OLTP in SQL Server 2016**
- _Veröffentlichungsdatum:_ &nbsp; 10.03.2019, auf `YouTube.com`.
- _Dauer:_ &nbsp; 17:32 &nbsp; &nbsp; (Links zum Video finden Sie im folgenden [**Index**](#anchorname-index-17minute-video).)
- _Gehostet von:_ &nbsp; Jos de Bruijn, Senior Program Manager für SQL Server

### <a name="demo-can-be-downloaded"></a>Die Demo kann heruntergeladen werden.

Bei Zeitmarke 08:09 führt das Video eine Demonstration zwei Mal aus. Sie können den Quellcode für die ausführbare Leistungsdemo, die im Video verwendet wird, über den folgenden Link herunterladen:

- [In-Memory OLTP Performance Demo v1.0, Quellcode](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)

Die folgenden allgemeinen Schritte sind im Video zu sehen:

1. Zunächst wird die Demo mit einer regulären Tabelle ausgeführt.
2. Als nächstes sehen wir eine speicheroptimierte Version der Tabelle, die mit wenigen Mausklicks erstellt und in SQL Server Management Studio („SSMS. exe“) mit Daten aufgefüllt wird.
3. Anschließend wird die Demo mit der speicheroptimierten Tabelle erneut ausgeführt. Es wird eine enorme Geschwindigkeitsverbesserung gemessen.

### <a name="anchorname-index-17minute-video"></a>Index für jeden Abschnitt im Video

| Link zu Zeitmarken | Titel des Abschnitts |
| :------------- | :------------ |
| A.&nbsp; [00:00](https://www.youtube.com/watch?v=l5l5eophmK4&t=0) | Die Einführung. |
| <br/>B.&nbsp; [00:56](https://www.youtube.com/watch?v=l5l5eophmK4&t=56) | <br/>Warum sich Kunden mit In-Memory-OLTP auseinandersetzen sollten. |
| &nbsp; &nbsp; [01:03](https://www.youtube.com/watch?v=l5l5eophmK4&t=63) | Moderne Hardware erfordert eine moderne Architektur des Datenbanksystems. |
| &nbsp; &nbsp; [02:10](https://www.youtube.com/watch?v=l5l5eophmK4&t=130) | Explosion der generierten Daten. Vorgänge müssen sofort (geringe Latenzzeit) ausgeführt werden. |
| &nbsp; &nbsp; [03:19](https://www.youtube.com/watch?v=l5l5eophmK4&t=199) | Verringerung der Gesamtkosten: Nutzen Sie die vorhandenen Ressourcen effizienter. |
| <br/>C.&nbsp; [03:33](https://www.youtube.com/watch?v=l5l5eophmK4&t=213) | <br/>Vorstellung von In-Memory-OLTP.<br/>Leistungsoptimierung durch Verwenden von speicheroptimierten Technologien. |
| &nbsp; &nbsp; [05:03](https://www.youtube.com/watch?v=l5l5eophmK4&t=303) | Bis zu 30-fach schnellere Transaktionsverarbeitung. |
| &nbsp; &nbsp; [05:22](https://www.youtube.com/watch?v=l5l5eophmK4&t=322) | Vollständig dauerhaft: Daten überstehen Serverfehler. |
| &nbsp; &nbsp; [06:15](https://www.youtube.com/watch?v=l5l5eophmK4&t=375) | Vollständig in SQL Server integriert. Daher sind keine neuen Sprachen oder Tools zu erlernen. |
| &nbsp; &nbsp; [07:22](https://www.youtube.com/watch?v=l5l5eophmK4&t=442) | Zuerst in SQL Server 2014 veröffentlicht, wichtige Verbesserungen in 2016. |
| &nbsp; &nbsp; [07:58](https://www.youtube.com/watch?v=l5l5eophmK4&t=558) | Aich in Azure SQL-Datenbank (in der Cloud) verfügbar. |
| <br/>D.&nbsp; [08:09](https://www.youtube.com/watch?v=l5l5eophmK4&t=489) | <br/>Leistungsdemonstration.<br/> Ausführen der Demo mit einer regulären Tabelle. |
| &nbsp; &nbsp; [09:11](https://www.youtube.com/watch?v=l5l5eophmK4&t=551) | SSMS-Kontextmenü: **Berichte** &gt; **Transaktionsleistungsanalyse** |
| &nbsp; &nbsp; [10:38](https://www.youtube.com/watch?v=l5l5eophmK4&t=638) | SSMS-Kontextmenü: **Advisor für die Speicheroptimierung**<br/> &nbsp; &nbsp; Tatsächliches Erstellen einer speicheroptimierten Tabelle aus einer regulären Tabelle und Migrieren der Daten. |
| &nbsp; &nbsp; [11:28](https://www.youtube.com/watch?v=l5l5eophmK4&t=688) | Führen Sie die Demo erneut aus. Sie erkennen eine 45-fache Leistungsverbesserung. |
| <br/>E.&nbsp; [12:17](https://www.youtube.com/watch?v=l5l5eophmK4&t=737) | <br/>Einfachere Verwendung von In-Memory-OLTP in SQL Server 2016 (im Vergleich zu 2014). |
| &nbsp; &nbsp; [12:43](https://www.youtube.com/watch?v=l5l5eophmK4&t=763) | Vereinfachte Analyse zur Unterstützung der App-Migration. |
| &nbsp; &nbsp; [13:03](https://www.youtube.com/watch?v=l5l5eophmK4&t=783) | Geringere Komplexität der App-Migration durch erweiterte Transact-SQL-Sprachunterstützung (z.B. mit Fremdschlüsseln und Triggern). |
| &nbsp; &nbsp; [13:56](https://www.youtube.com/watch?v=l5l5eophmK4&t=836) | Verbesserte Verwaltbarkeit.<br/> &nbsp; &nbsp; Beispiele: Ändern von Schema und Indizes, automatische Aktualisierung von Statistiken. |
| <br/>F.&nbsp; [14:46](https://www.youtube.com/watch?v=l5l5eophmK4&t=886) | <br/>Verbesserte Skalierbarkeit. |
| &nbsp; &nbsp; [15:12](https://www.youtube.com/watch?v=l5l5eophmK4&t=912) | Große speicheroptimierte Tabellen (bis zu 2 TB pro Datenbank). |
| &nbsp; &nbsp; [15:34](https://www.youtube.com/watch?v=l5l5eophmK4&t=934) | Noch bessere Skalierung. |
| &nbsp; &nbsp; [16:41](https://www.youtube.com/watch?v=l5l5eophmK4&t=1001) | Nutzen Sie die vorhandenen Ressourcen effizienter! |
| <br/>G.&nbsp; [16:53](https://www.youtube.com/watch?v=l5l5eophmK4&t=1013) | <br/>Abschließende Kommentare. (Endet bei 17:32.) |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Weitere Informationen  
 [Datenbankfunktionen](../../relational-databases/database-features.md)  
  
  
