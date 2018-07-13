---
title: Anforderungen für die Verwendung speicheroptimierter Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2014
ms.assetid: 47d9a7e8-c597-4b95-a58a-dcf66df8e572
caps.latest.revision: 53
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f4b47ee3a3f4274ca94175060f10722fa45b6693
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190390"
---
# <a name="requirements-for-using-memory-optimized-tables"></a>Anforderungen für die Verwendung von speicheroptimierten Tabellen
  Zusätzlich zu den [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md), im folgenden sind die Voraussetzungen zum Verwenden von In-Memory-OLTP:  
  
-   64-Bit Enterprise, Developer oder Evaluation Edition von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigt ausreichend Arbeitsspeicher zum Speichern der Daten in speicheroptimierten Tabellen und Indizes. Um auch Zeilenversionen zu berücksichtigen, sollten Sie doppelt so viel Arbeitsspeicher wie die zu erwartende Größe der speicheroptimierten Tabellen und Indizes bereitstellen. Die tatsächlich erforderliche Arbeitsspeichergröße ist jedoch abhängig von der Arbeitsauslastung. Überwachen Sie die Speicherauslastung, und nehmen Sie bei Bedarf geeignete Anpassungen vor. Die Datengröße in speicheroptimierten Tabellen darf den für den Pool zulässigen Prozentsatz nicht überschreiten. Um die Größe einer speicheroptimierten Tabelle ermitteln zu können, finden Sie unter [Sys. dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql).  
  
     Wenn die Datenbank datenträgerbasierte Tabellen enthält, müssen Sie genügend Arbeitsspeicher für den Pufferpool und die Abfrageverarbeitung in diesen Tabellen bereitstellen.  
  
     Dazu müssen Sie wissen, wie viel Arbeitsspeicher die In-Memory OLTP-Anwendung erfordert. Weitere Informationen finden Sie unter [Schätzen der Arbeitsspeicheranforderungen speicheroptimierter Tabellen](memory-optimized-tables.md) .  
  
-   Geben Sie Speicherplatz frei, der zweimal der Größe der dauerhaften speicheroptimierten Tabellen entspricht.  
  
-   Der Prozessor muss die **cmpxchg16b** -Anweisung unterstützen, um In-Memory OLTP verwenden zu können. Alle modernen 64-Bit-Prozessoren unterstützen **cmpxchg16b**.  
  
     Wenn Sie eine VM-hostanwendung verwenden und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zeigt einen Fehler verursacht hat, von einem älteren Prozessor, finden Sie unter verfügt die Anwendung eine Konfigurationsoption zum **cmpxchg16b**. Andernfalls können Sie Hyper-V verwenden, das **cmpxchg16b** ohne Änderung einer Konfigurationsoption unterstützt.  
  
-   Wählen Sie zum Installieren von In-Memory OLTP **Database Engine Services** bei der Installation [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
     Zum Installieren der berichtgenerierung ([bestimmen, ob eine Tabelle oder eine gespeicherte Prozedur portiert werden soll, In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) und [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (zum Verwalten von In-Memory-OLTP über [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Objekt-Explorer) auf **Management Tools, grundlegende** oder **Verwaltungstools – erweitert** bei der Installation [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
## <a name="important-notes-on-using-includehek2includeshek-2-mdmd"></a>Wichtige Anmerkungen zur Verwendung von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]  
  
-   Die Gesamtgröße aller dauerhaften Tabellen in einer Datenbank sollte im Arbeitsspeicher maximal 250 GB betragen. Weitere Informationen finden Sie unter [Dauerhaftigkeit für Speicheroptimierte Tabellen](durability-for-memory-optimized-tables.md).  
  
-   Diese Version von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] kann auf Systemen mit 2 oder 4 Sockets und weniger als 60 Kernen optimal ausgeführt werden.  
  
-   Prüfpunktdateien dürfen nicht manuell gelöscht werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt automatisch eine Garbage Collection für nicht benötigte Prüfpunktdateien aus. Weitere Informationen finden Sie unter der Erläuterung für das Zusammenführen von Daten- und Änderungsdateien Dateien im [Dauerhaftigkeit für Speicheroptimierte Tabellen](durability-for-memory-optimized-tables.md).  
  
-   In dieser ersten Version von In-Memory-OLTP (in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]), die einzige Möglichkeit zum Entfernen einer speicheroptimierten Dateigruppe ist die Datenbank zu löschen.  
  
-   Wenn Sie versuchen, eine große Anzahl von Zeilen zu löschen, während gleichzeitig eine Arbeitsauslastung zum Einfügen oder Aktualisieren für den Zeilenbereich ausgeführt wird, den Sie löschen möchten, verursacht der Löschvorgang u. U. einen Fehler. Um das Problem zu umgehen, muss die Arbeitsauslastung zum Einfügen/Aktualisieren vor dem Löschvorgang beendet werden. Alternativ könnten Sie die Transaktion in kleinere Transaktionen aufteilen, bei denen es weniger wahrscheinlich ist, von einer gleichzeitigen Arbeitsauslastung unterbrochen zu werden. Wenn alle Vorgänge in speicheroptimierten Tabellen schreiben, verwenden von wiederholungsversuchlogik ([Richtlinien zur Wiederholungslogik für Transaktionen in speicheroptimierten Tabellen](../../database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)).  
  
-   Wenn Sie eine oder mehrere Datenbanken mit speicheroptimierten Tabellen erstellen, sollten Sie die sofortige Dateiinitialisierung für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz aktivieren (also dem Dienststartkonto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Benutzerrecht SE_MANAGE_VOLUME_NAME erteilen). Ohne die sofortige Dateiinitialisierung werden speicheroptimierte Speicherdateien (Daten- und Änderungsdateien) bei der Erstellung initialisiert, was sich negativ auf die Leistung der Arbeitsauslastung auswirken kann. Weitere Informationen zur sofortigen Dateiinitialisierung finden Sie unter [Datenbankdatei-Initialisierung](http://msdn.microsoft.com/library/ms175935\(SQL.105\).aspx). Informationen dazu, wie die sofortige Dateiinitialisierung aktiviert wird, finden Sie unter [Wie und warum die sofortige Dateiinitialisierung aktiviert werden sollte](http://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx).  
  
## <a name="did-this-article-help-you-were-listening"></a>Fanden Sie diesen Artikel nützlich? Wir hören Ihnen zu  
 Welche Informationen suchen Sie, und haben Sie sie gefunden? Wir nehmen uns Ihr Feedback zu Herzen, um unsere Inhalte zu verbessern. Bitte senden Sie Ihre Kommentare zu [ sqlfeedback@microsoft.com ](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Requirements%20for%20Using%20Memory-Optimized%20Tables%20page).  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
