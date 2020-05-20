---
title: Grundlegende Änderungen an der voll Text Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], breaking changes
- full-text catalogs [SQL Server], breaking changes
- breaking changes [full-text search]
- full-text indexes [SQL Server], breaking changes
ms.assetid: c55a6748-e5d9-4fdb-9a1f-714475a419c5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9a223060768c35b2daf00837153e59218ff1c50e
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2020
ms.locfileid: "83001020"
---
# <a name="breaking-changes-to-full-text-search"></a>Fehlerhafte Änderungen der Volltextsuche
  In diesem Thema werden fehlerhafte Änderungen im Verhalten der Volltextsuche beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade auftreten. Weitere Informationen finden Sie unter [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-full-text-search-in-sssql14"></a>Wichtige Änderungen an der Volltextsuche in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informationen werden später bereitgestellt.  
  
## <a name="breaking-changes-in-full-text-search-in-sssql11"></a>Wichtige Änderungen an der Volltextsuche in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="collation-changed-for-name-column-in-sysfulltext_languages"></a>Sortierung in sys.fulltext_languages für Namensspalte geändert  
 Die Sortierung der **name**-Spalte in der Katalogsicht [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) wurde von der festen Sortierung der Ressourcendatenbank zur für die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausgewählten Standardsortierung geändert. Diese Änderung ermöglicht den Vergleich der Werte in der **name**-Spalte, wenn Sie die [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql)-Sicht mit **sys.fulltext_languages** verknüpfen. Sie können z. B. für alle Datenbanken abfragen, wo sich die Standardvolltextsprache von der Standarddatenbanksprache unterscheidet.  
  
## <a name="breaking-changes-in-full-text-search-in-sql-server-2008"></a>Aktuelle Änderungen an der Volltextsuche in SQL Server 2008  
 Die folgenden aktuellen Änderungen gelten zwischen [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] und [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] und höheren Versionen der Volltextsuche.  
  
|Feature|Szenario|SQL Server 2005|Nur in SQL Server 2008 und höheren Versionen.|  
|-------------|--------------|---------------------|----------------------------------------|  
|[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) mit benutzerdefinierten Typen (UDTs)|Der Volltextschlüssel ist ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] benutzerdefinierter Typ, z. B. `MyType = char(1)`.|Der zurückgegebene Schlüssel entspricht dem Typ, der dem benutzerdefinierten Typ zugewiesen wurde.<br /><br /> Im Beispiel wäre dies **char (1)**.|Der zurückgegebene Schlüssel entspricht dem benutzerdefinierten Typ. Im Beispiel wäre dies **MyType**.|  
|*top_n_by_rank* -Parameter (der "CONTAINSTABLE"-und " [fretexfähige](/sql/relational-databases/system-functions/freetexttable-transact-sql) "- [!INCLUDE[tsql](../includes/tsql-md.md)] Anweisungen)|*top_n_by_rank* Abfragen, die 0 als Parameter verwenden.|Erzeugt einen Fehler, da – wie in der Fehlermeldung angegeben – ein Wert größer als 0 (null) verwendet werden muss.|Wird erfolgreich ausgeführt und gibt 0 (null) Zeilen zurück.|  
|CONTAINSTABLE und **ItemCount**|Löschen Sie Zeilen aus der Basistabelle, bevor Änderungen an MSSearch übermittelt werden.|CONTAINSTABLE gibt einen inaktiven Datensatz zurück. **ItemCount** wird nicht geändert.|CONTAINSTABLE gibt keine inaktiven Datensätze zurück.|  
|**ItemCount**|Tabelle enthält keine Dokumente oder Typspalten.|Zusätzlich zu indizierten Dokumenten werden Dokumente, die NULL sind oder NULL-Typen aufweisen, im **ItemCount** -Wert gezählt.|Nur indizierte Dokumente werden im **ItemCount** -Wert gezählt.|  
|Katalog- **ItemCount**|BLOB-Spalte mit einer NULL-Erweiterung.|Der Wert wird in **ItemCount** des Katalogs gezählt.|Er wird nicht in **ItemCount** des Katalogs gezählt.|  
|**UniqueKeyCount**|Abfragen einer eindeutigen Anzahl von Schlüsseln von einem Katalog, z. B. zwei Tabellen (table1 und table2) mit jeweils drei Wörtern (word1, word2 und word3).|**UniqueKeyCount** = 9. In der folgenden Tabelle wird zusammengefasst, wie dieser Wert erreicht wird:<br /><br /> table1 = 3<br /><br /> EOF für Volltextindex von table1 = 1<br /><br /> table2 = 3<br /><br /> EOF für Volltextindex von table2 = 1<br /><br /> Volltextkatalog = 1|Für jede Tabelle ist **UniqueKeyCount** die Anzahl der unterschiedlichen Schlüsselwörter + 1 (0xFF).  Diese Wörter werden in > 1-doc nicht als neuer eindeutiger Schlüssel behandelt.<br /><br /> Bei einem Katalog ist **UniqueKeyCount** die Summe von **UniqueKeyCount** für jede der Tabellen im Katalog. Identische Wörter aus verschiedenen Tabellen werden als eindeutige Schlüssel behandelt. In diesem Fall entspricht die Anzahl der eindeutigen Schlüssel 8.|  
|**Rang Voraus berechnen** -Option auf Serverebene|Leistungsoptimierung von FREETEXTTABLE-Abfragen.|Wenn die Option auf 1 festgelegt ist, verwenden die mit *top_n_by_rank* angegebenen frei wählbaren Abfragen Voraus berechnete Rang Daten, die in den Volltextkatalogen gespeichert sind.|Wird nicht unterstützt.|  
|beim Aktualisieren der Schlüssel Spalte [sp_fulltext_pendingchanges](/sql/relational-databases/system-stored-procedures/sp-fulltext-pendingchanges-transact-sql)|Aktualisieren Sie die Volltextschlüsselspalte in einer Zeile einer zweizeiligen Tabelle, und führen Sie sp_fulltext_pendingchanges aus.|Beide Zeilen werden angezeigt.|Nur eine Zeile wird angezeigt.|  
|Inlinefunktionen|Inlinefunktionen mit einem Volltextoperator|Rückgabe einer Fehlermeldung.|Rückgabe der relevanten Zeilen.|  
|[sp_fulltext_database](/sql/relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql)|Aktivieren oder deaktivieren Sie die Volltextsuche mit sp_fulltext_database.|Bei Volltextabfragen werden keine Ergebnisse zurückgegeben. Wenn Volltext für die Datenbank deaktiviert wurde, können keine Volltextvorgänge ausgeführt werden.|Gibt Ergebnisse für Volltextabfragen zurück, und Volltextvorgänge können auch dann ausgeführt werden, wenn Volltext für die Datenbank deaktiviert wurde.|  
|Gebietsschemaspezifische Stoppwörter|Fragt nicht Gebiets Schema spezifische Varianten einer übergeordneten Sprache ab, wie z. b. Französisch (Belgien) und Französisch (Kanada).|Abfragen in Gebiets Schema spezifischen Varianten werden von den Komponenten (Wörter Trennung, Wort Stamm Erkennung und Stoppwörter) der übergeordneten Sprache verarbeitet. Beispielsweise wird Französisch (Belgien) mit den Komponenten von Französisch (Frankreich) analysiert.|Stoppwörter müssen jedem Gebietsschemabezeichner (LCID) explizit hinzugefügt werden. Beispielsweise müssen Sie eine LCID für Belgien, Kanada und Frankreich angeben.|  
|Thesaurus-Wortstammerkennung|Verwendung von Thesaurus und Flexionsformen (Wortstammerkennung).|Nach der Erweiterung wird für Thesauruswörter automatisch eine Wortstammerkennung durchgeführt.|Wenn Sie die flektierte Form in der Erweiterung verwenden möchten, müssen Sie diese explizit hinzufügen.|  
|Volltext-Katalogpfad und -Dateigruppe|Verwendung von Volltextkatalogen.|Jeder Volltextkatalog weist einen physischen Pfad auf und gehört einer Dateigruppe an. Volltextkataloge werden als Datenbankdateien behandelt.|Ein Volltextkatalog ist ein virtuelles Objekt und gehört keiner Dateigruppe an. Ein Volltextkatalog ist ein logisches Konzept, das auf eine Gruppe von Volltextindizes verweist.<br /><br /> Hinweis: [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] DDL-Anweisungen, die voll Text Kataloge angeben, funktionieren ordnungsgemäß.|  
|[sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql)|Verwendung des Pfads, der data_space_id, der file_id der Katalogsicht.|Diese Spalten geben einen spezifischen Wert zurück.|Diese Spalten geben NULL zurück, da sich der Volltextkatalog nicht mehr im Dateisystem befindet.|  
|[sys.sysfulltextcatalogs](/sql/relational-databases/system-compatibility-views/sys-sysfulltextcatalogs-transact-sql)|Verwendung der Pfadspalte für die veraltete Systemtabelle.|Gibt den Dateisystempfad des Volltextkatalogs zurück.|Gibt NULL zurück, da sich der Volltextkatalog nicht mehr im Dateisystem befindet.|  
|[sp_help_fulltext_catalogs](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql)<br /><br /> [sp_help_fulltext_catalogs_cursor](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql)|Verwendung der Spalte PATH für die veralteten gespeicherten Prozeduren.|Gibt den Dateisystempfad des Volltextkatalogs zurück.|Gibt NULL zurück, da sich der Volltextkatalog nicht mehr im Dateisystem befindet.|  
|[sp_help_fulltext_catalog_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalog-components-transact-sql)|Verwendung von sp_help_fulltext_catalog_components für diese gespeicherte Prozedur.|Gibt eine Liste aller Komponenten (Filter, Wörtertrennung und Protokollhandler) zurück, die für alle Volltextkataloge in der aktuellen Datenbank verwendet werden.|Gibt leere Zeilen zurück.|  
|[DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql)|Verwenden der **IsFullTextEnabled** -Eigenschaft.|Mit der Einstellung " **IsFullTextEnabled** " wird angegeben, ob die Volltextsuche in einer bestimmten Datenbank aktiviert ist.|Der Wert dieser Spalte hat keine Auswirkungen. In Benutzerdatenbanken ist die Volltextsuche standardmäßig aktiviert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verhaltensänderungen der voll Text Suche](../relational-databases/search/full-text-search.md)   
 [Voll Text Suche](../relational-databases/search/full-text-search.md)  
  
  
