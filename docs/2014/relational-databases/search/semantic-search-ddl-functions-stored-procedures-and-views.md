---
title: Semantische Such-DDL, Funktionen, gespeicherte Prozeduren und Sichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d61854f57214212d079b4d32ae69b0bc6e8c5cce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160470"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a>Semantische Such-DDL, Funktionen, gespeicherte Prozeduren und Sichten
  Im Folgenden finden Sie eine Liste der Transact-SQL-Anweisungen und Datenbankobjekte, die die statistische semantische Suche in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützen.  
  
 Eine Liste der Anweisungen und Datenbankobjekte, die die Volltextsuche unterstützen, finden Sie unter [DDL, Funktionen, gespeicherte Prozeduren und Sichten für Volltextsuche](../views/views.md).  
  
##  <a name="ddl"></a> Transact-SQL-DDL-Anweisungen (Data Definition Language, Datendefinitionssprache)  
  
|Objekt|Weitere Informationen|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)|[Aktivieren der semantischen Suche in Tabellen und Spalten](enable-semantic-search-on-tables-and-columns.md)|  
|[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)|[Aktivieren der semantischen Suche in Tabellen und Spalten](enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="func"></a> Systemfunktionen  
  
|Objekt|Weitere Informationen|  
|------------|----------------------|  
|[semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)|[Suchen von Schlüsselausdrücken in Dokumenten mit der semantischen Suche](find-key-phrases-in-documents-with-semantic-search.md)|  
|[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)|[Suchen von ähnlichen und verwandten Dokumenten mit semantischer Suche](find-similar-and-related-documents-with-semantic-search.md)|  
|[semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)|[Suchen von ähnlichen und verwandten Dokumenten mit semantischer Suche](find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="meta"></a> Systemmetadatenfunktionen  
  
|Objekt|Weitere Informationen|  
|------------|----------------------|  
|[COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql)|[Aktivieren der semantischen Suche in Tabellen und Spalten](enable-semantic-search-on-tables-and-columns.md)|  
|[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql)|[Aktivieren der semantischen Suche in Tabellen und Spalten](enable-semantic-search-on-tables-and-columns.md)|  
|[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|[Verwalten und Überwachen der semantischen Suche](manage-and-monitor-semantic-search.md)|  
|[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql)|[Verwalten und Überwachen der semantischen Suche](manage-and-monitor-semantic-search.md)|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)|[Aktivieren der semantischen Suche in Tabellen und Spalten](enable-semantic-search-on-tables-and-columns.md)|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)|[Installieren und Konfigurieren der semantischen Suche](install-and-configure-semantic-search.md)|  
  
##  <a name="sproc"></a> Gespeicherte Systemprozeduren  
  
|Objekt|Weitere Informationen|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql)|[Installieren und Konfigurieren der semantischen Suche](install-and-configure-semantic-search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql)|[Installieren und Konfigurieren der semantischen Suche](install-and-configure-semantic-search.md)|  
  
##  <a name="cv"></a> Systemsichten – Katalogsichten  
  
|Objekt|Weitere Informationen|  
|------------|----------------------|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|[Verwalten und Überwachen der semantischen Suche](manage-and-monitor-semantic-search.md)|  
|[sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)|[Installieren und Konfigurieren der semantischen Suche](install-and-configure-semantic-search.md)|  
|[sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)|[Installieren und Konfigurieren der semantischen Suche](install-and-configure-semantic-search.md)|  
  
##  <a name="dmv"></a> Systemsichten – Dynamische Verwaltungssichten  
  
|Objekt|Weitere Informationen|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)|[Verwalten und Überwachen der semantischen Suche](manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|[Verwalten und Überwachen der semantischen Suche](manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)|[Verwalten und Überwachen der semantischen Suche](manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten und Überwachen der semantischen Suche](manage-and-monitor-semantic-search.md)  
  
  
