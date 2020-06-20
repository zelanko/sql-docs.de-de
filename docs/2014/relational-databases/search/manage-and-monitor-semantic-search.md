---
title: Verwalten und Überwachen der semantischen Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16e3af1d37f177dfe6d4e0cb090e7b8b0a4988d9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85003933"
---
# <a name="manage-and-monitor-semantic-search"></a>Verwalten und Überwachen der semantischen Suche
  In diesem Thema werden der Prozess der semantischen Indizierung sowie die Tasks im Zusammenhang mit der Verwaltung und Überwachung der Indizes beschrieben.  
  
##  <a name="how-to-check-the-status-of-semantic-indexing"></a><a name="HowToMonitorStatus"></a>Vorgehensweise: Überprüfen des Status der semantischen Indizierung  
 **Ist die erste Phase der semantischen Indizierung abgeschlossen?**  
 Fragen Sie die dynamische Verwaltungssicht ab, [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql), und überprüfen Sie die **status**- und **status_description**-Spalten.  
  
 Die erste Phase der Indizierung umfasst die Auffüllung des Volltextschlüsselwortindexes und des semantischen Schlüsselausdruckindexes sowie die Extraktion der Dokumentähnlichkeitsdaten.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 **Ist die zweite Phase der semantischen Indizierung abgeschlossen?**  
 Fragen Sie die dynamische Verwaltungssicht ab, [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql), und überprüfen Sie die **status**- und **status_description**-Spalten.  
  
 Die zweite Phase der Indizierung umfasst die Auffüllung des semantischen Dokumentähnlichkeitsindexes.  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="how-to-check-the-size-of-the-semantic-indexes"></a><a name="HowToCheckSize"></a>Gewusst wie: Überprüfen der Größe der semantischen Indizes  
 **Was ist die logische Größe eines semantischen Schlüsselausdruckindexes oder eines semantischen Dokumentähnlichkeitsindexes?**  
 Fragen Sie die dynamische Verwaltungssicht ab, [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql).  
  
 Die logische Größe wird in Anzahl von Indexseiten angezeigt.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 **Wie groß sind die Volltext- und die semantischen Indizes für einen Volltextkatalog insgesamt?**  
 Fragen Sie die Eigenschaft **IndexSize** der Metadatenfunktion [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) ab.  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 **Wie viele Elemente werden in den Volltext- und den semantischen Indizes für einen Volltextkatalog indiziert?**  
 Fragen Sie die Eigenschaft **ItemCount** der Metadatenfunktion [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) ab.  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="how-to-force-the-population-of-the-semantic-indexes"></a><a name="HowToForcePopulation"></a>Gewusst wie: Erzwingen der Auffüllung der semantischen Indizes  
 Sie können die Auffüllung der Volltextindizes und semantischen Indizes mit der START/STOP/PAUSE-Klausel oder der RESUME POPULATION-Klausel mit der gleichen Syntax und dem für Volltextindizes beschriebenen Verhalten erzwingen. Weitere Informationen finden Sie unter [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) und [Auffüllen von Volltextindizes](../indexes/indexes.md).  
  
 Da die semantische Indizierung von der Volltextindizierung abhängig ist, werden semantische Indizes nur dann aufgefüllt, wenn die zugeordneten Volltextindizes aufgefüllt werden.  
  
 **Beispiel: Starten einer vollständigen Auffüllung von Volltext- und semantischen Indizes**  
  
 Im folgenden Beispiel wird die vollständige Auffüllung von sowohl Volltext- als auch semantischen Indizes gestartet, indem ein vorhandener Volltextindex in der **Production.Document** -Tabelle in der AdventureWorks2012-Beispieldatenbank geändert wird.  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="how-to-disable-or-re-enable-semantic-indexing"></a><a name="HowToDisableIndexing"></a>Vorgehensweise: deaktivieren oder erneutes Aktivieren der semantischen Indizierung  
 Sie können die Volltextindizierung oder semantische Indizierung mit der ENABLE/DISABLE-Klausel mit der gleichen Syntax und dem für Volltextindizes beschriebenen Verhalten deaktivieren. Weitere Informationen finden Sie unter [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).  
  
 Wenn die semantische Indizierung deaktiviert und angehalten wurde, funktionieren Abfragen über semantische Daten weiterhin und geben zuvor indizierte Daten zurück. Dieses Verhalten ist nicht konsistent mit dem Verhalten der Volltextsuche.  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="phases-of-semantic-indexing"></a><a name="SemanticIndexing"></a>Phasen der semantischen Indizierung  
 Bei der semantischen Suche werden zwei Arten von Daten für jede Spalte indiziert, für die sie aktiviert wurde:  
  
1.  **Schlüsselbegriffe**  
  
2.  **Dokumentähnlichkeit**  
  
 Die semantische Indizierung erfolgt in zwei Phase, in Verbindung mit der Volltextindizierung:  
  
1.  **Phase 1**. Der Volltextschlüsselwortindex und der semantische Schlüsselausdruckindex werden zur gleichen Zeit parallel aufgefüllt. Die zur Indizierung der Dokumentähnlichkeit erforderlichen Daten werden ebenfalls zu diesem Zeitpunkt extrahiert.  
  
2.  **Phase 2**. Anschließend wird der semantische Dokumentähnlichkeitsindex aufgefüllt. Dieser Index ist von beiden Indizes abhängig, die in der vorherigen Phase aufgefüllt wurden.  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-semantic-indexes-are-not-populated"></a><a name="ProblemNotPopulated"></a>Problem: semantische Indizes werden nicht aufgefüllt.  
 **Werden die zugeordneten Volltextindizes aufgefüllt?**  
 Da die semantische Indizierung von der Volltextindizierung abhängig ist, werden semantische Indizes nur dann aufgefüllt, wenn die zugeordneten Volltextindizes aufgefüllt werden.  
  
 **Sind die Volltextsuche und die semantische Suche ordnungsgemäß installiert und konfiguriert?**  
 Weitere Informationen finden Sie unter [Installieren und Konfigurieren der semantischen Suche](install-and-configure-semantic-search.md).  
  
 **Ist der FDHOST-Dienst nicht verfügbar, oder gibt es eine andere Bedingung, aufgrund der die Volltextindizierung fehlschlagen würde?**  
 Weitere Informationen finden Sie unter [Behandeln von Problemen mit der Volltextindizierung](troubleshoot-full-text-indexing.md).  
  
  
