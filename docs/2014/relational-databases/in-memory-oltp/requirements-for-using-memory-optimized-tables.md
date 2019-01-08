---
title: Anforderungen für die Verwendung speicheroptimierter Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47d9a7e8-c597-4b95-a58a-dcf66df8e572
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9b9e442fb97245d32c398602cdfd727de8239cb8
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53352423"
---
# <a name="requirements-for-using-memory-optimized-tables"></a>Anforderungen für die Verwendung von speicheroptimierten Tabellen
  Zusätzlich zu den [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md), im folgenden sind die Voraussetzungen zum Verwenden von In-Memory-OLTP:  
  
-   64-Bit Enterprise, Developer oder Evaluation Edition von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigt ausreichend Arbeitsspeicher, um die Daten in speicheroptimierten Tabellen und Indizes aufnehmen zu können. Um auch Zeilenversionen zu berücksichtigen, sollten Sie doppelt so viel Arbeitsspeicher wie die zu erwartende Größe der speicheroptimierten Tabellen und Indizes bereitstellen. Die tatsächlich erforderliche Arbeitsspeichergröße ist jedoch abhängig von der Arbeitsauslastung. Überwachen Sie die Speicherauslastung, und nehmen Sie bei Bedarf geeignete Anpassungen vor. Die Datengröße in speicheroptimierten Tabellen darf den für den Pool zulässigen Prozentsatz nicht überschreiten. Um die Größe einer speicheroptimierten Tabelle ermitteln zu können, finden Sie unter [Sys. dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql).  
  
     Wenn die Datenbank datenträgerbasierte Tabellen enthält, müssen Sie genügend Arbeitsspeicher für den Pufferpool und die Abfrageverarbeitung in diesen Tabellen bereitstellen.  
  
     Dazu müssen Sie wissen, wie viel Arbeitsspeicher die In-Memory OLTP-Anwendung erfordert. Weitere Informationen finden Sie unter [Schätzen der Arbeitsspeicheranforderungen speicheroptimierter Tabellen](memory-optimized-tables.md) .  
  
-   Geben Sie Speicherplatz frei, der zweimal der Größe der dauerhaften speicheroptimierten Tabellen entspricht.  
  
-   Der Prozessor muss die **cmpxchg16b** -Anweisung unterstützen, um In-Memory OLTP verwenden zu können. Alle modernen 64-Bit-Prozessoren unterstützen **cmpxchg16b**.  
  
     Wenn Sie eine VM-Hostanwendung verwenden und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Fehler anzeigt, der von einem älteren Prozessor verursacht wird, sollten Sie überprüfen, ob die Anwendung eine Konfigurationsoption zum Aktivieren von **cmpxchg16b**. Andernfalls können Sie Hyper-V verwenden, das **cmpxchg16b** ohne Änderung einer Konfigurationsoption unterstützt.  
  
-   Zur Installation von In-Memory OLTP wählen Sie bei der Installation von die Option **Database Engine Services** aus [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
     Zum Installieren der berichtgenerierung ([bestimmen, ob eine Tabelle oder eine gespeicherte Prozedur portiert werden soll, In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) und [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (zum Verwalten von In-Memory-OLTP über [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Objekt-Explorer) auf **Management Tools – Basic** oder **Verwaltungstools – erweitert** bei der Installation [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
## <a name="important-notes-on-using-includehek2includeshek-2-mdmd"></a>Wichtige Anmerkungen zur Verwendung von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]  
  
-   Die Gesamtgröße aller dauerhaften Tabellen in einer Datenbank sollte im Arbeitsspeicher maximal 250 GB betragen. Weitere Informationen finden Sie unter [Dauerhaftigkeit für Speicheroptimierte Tabellen](durability-for-memory-optimized-tables.md).  
  
-   Diese Version von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] kann auf Systemen mit 2 oder 4 Sockets und weniger als 60 Kernen optimal ausgeführt werden.  
  
-   Prüfpunktdateien dürfen nicht manuell gelöscht werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt automatisch eine Garbage Collection für nicht benötigte Prüfpunktdateien aus. Weitere Informationen finden Sie unter der Erläuterung für das Zusammenführen von Daten- und Änderungsdateien Dateien im [Dauerhaftigkeit für Speicheroptimierte Tabellen](durability-for-memory-optimized-tables.md).  
  
-   In dieser ersten Version von In-Memory OLTP (in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) besteht die einzige Möglichkeit, eine speicheroptimierte Dateigruppe zu entfernen, im Löschen der Datenbank.  
  
-   Wenn Sie versuchen, eine große Anzahl von Zeilen zu löschen, während gleichzeitig eine Arbeitsauslastung zum Einfügen oder Aktualisieren für den Zeilenbereich ausgeführt wird, den Sie löschen möchten, verursacht der Löschvorgang u. U. einen Fehler. Um das Problem zu umgehen, muss die Arbeitsauslastung zum Einfügen/Aktualisieren vor dem Löschvorgang beendet werden. Alternativ könnten Sie die Transaktion in kleinere Transaktionen aufteilen, bei denen es weniger wahrscheinlich ist, von einer gleichzeitigen Arbeitsauslastung unterbrochen zu werden. Sie sollten wie bei allen Schreibvorgängen für speicheroptimierte Tabellen Wiederholungslogik verwenden ([Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../../database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)).  
  
-   Wenn Sie eine oder mehrere Datenbanken mit speicheroptimierten Tabellen erstellen, sollten Sie die sofortige Dateiinitialisierung für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz aktivieren (also dem Dienststartkonto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Benutzerrecht SE_MANAGE_VOLUME_NAME erteilen). Ohne die sofortige Dateiinitialisierung werden speicheroptimierte Speicherdateien (Daten- und Änderungsdateien) bei der Erstellung initialisiert, was sich negativ auf die Leistung der Arbeitsauslastung auswirken kann. Weitere Informationen zur sofortigen Dateiinitialisierung finden Sie unter [Datenbankdatei-Initialisierung](../databases/database-instant-file-initialization.md). Informationen dazu, wie die sofortige Dateiinitialisierung aktiviert wird, finden Sie unter [Wie und warum die sofortige Dateiinitialisierung aktiviert werden sollte](https://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx).  
  
## <a name="did-this-article-help-you-were-listening"></a>Fanden Sie diesen Artikel nützlich? Wir hören Ihnen zu  
 Welche Informationen suchen Sie, und haben Sie sie gefunden? Wir hören Ihnen, Ihr Feedback zur Verbesserung des Inhalts. Bitte senden Sie Ihre Kommentare an [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Requirements%20for%20Using%20Memory-Optimized%20Tables%20page).  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
