---
title: sys. dm_fts_index_keywords_by_document (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_index_keywords_by_document_TSQL
- dm_fts_index_keywords_by_document_TSQL
- sys.dm_fts_index_keywords_by_document
- dm_fts_index_keywords_by_document
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], troubleshooting
- sys.dm_fts_index_keywords_by_document dynamic management function
- full-text search [SQL Server], viewing keywords
ms.assetid: 793b978b-c8a1-428c-90c2-a3e49d81b5c9
author: pmasl
ms.author: pelopes
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86ab3a31f53f480713ae27a70bfe59d3817af017
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078563"
---
# <a name="sysdm_fts_index_keywords_by_document-transact-sql"></a>sys.dm_fts_index_keywords_by_document (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Gibt Informationen über den Inhalt auf Dokumentebene von einem Volltextindex zurück, der der angegebenen Tabelle zugeordnet ist.  
  
 sys.dm_fts_index_keywords_by_document ist eine dynamische Verwaltungsfunktion.  
  
 **So zeigen Sie Informationen zu einem Volltextindex auf höherer Ebene an**  
  
-   [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)  
  
 **So zeigen Sie Informationen zu Inhalten auf Eigenschaftenebene an, die sich auf eine Dokumenteigenschaft beziehen**  
  
-   [sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.dm_fts_index_keywords_by_document  
(   
    DB_ID('database_name'),     OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Argumente  
 DB_ID ('*database_name*')  
 Ein Aufrufder [DB_ID ()](../../t-sql/functions/db-id-transact-sql.md) -Funktion. Diese Funktion akzeptiert einen Datenbanknamen und gibt die Datenbank-ID zurück, die von sys.dm_fts_index_keywords_by_document für die Suche nach der angegebenen Datenbank verwendet wird. Wenn *database_name* nicht angegeben ist, wird die aktuelle Datenbank-ID zurückgegeben.  
  
 object_id ('*table_name*')  
 Ein Aufrufder [object_id ()](../../t-sql/functions/object-id-transact-sql.md) -Funktion. Diese Funktion akzeptiert einen Tabellennamen und gibt die Tabellen-ID der Tabelle zurück, die den zu überprüfenden Volltextindex enthält.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Column|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|Schlüsselwort (keyword)|**nvarchar(4000)**|Die hexadezimale Darstellung des Schlüsselworts, das im Volltextindex gespeichert ist.<br /><br /> Hinweis: OxFF stellt das Sonderzeichen dar, das das Ende einer Datei oder eines Datasets angibt.|  
|display_term|**nvarchar(4000)**|Die Klartextform des Schlüsselworts. Dieses Format wird vom internen Format abgeleitet, das im Volltextindex gespeichert ist.<br /><br /> Hinweis: OxFF stellt das Sonderzeichen dar, das das Ende einer Datei oder eines Datasets angibt.|  
|column_id|**int**|Die ID der Spalte für die Volltextindizierung des aktuellen Schlüsselworts.|  
|document_id|**int**|Die ID des Dokuments bzw. der Zeile für die Volltextindizierung des aktuellen Ausdrucks. Diese ID entspricht dem Volltextschlüsselwert dieses Dokuments bzw. dieser Zeile.|  
|occurrence_count|**int**|Anzahl der Vorkommen des aktuellen Schlüssel Worts in dem Dokument oder der Zeile, das durch **document_id**angegeben wird. Wenn "*search_property_name*" angegeben wird, zeigt occurrence_count nur die Anzahl der Vorkommen des aktuellen Schlüssel Worts in der angegebenen Such Eigenschaft innerhalb des Dokuments oder der Zeile an.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die von sys.dm_fts_index_keywords_by_document zurückgegebenen Informationen dienen u. a. zum Abrufen der folgenden Ergebnisse:  
  
-   Die Gesamtzahl der Schlüsselwörter in einem Volltextindex  
  
-   Ob ein Schlüsselwort Teil eines bestimmten Dokuments bzw. einer Zeile ist  
  
-   Wie oft ein Schlüsselwort im gesamten Volltextindex vorkommt, d. h.:  
  
     ([Sum](../../t-sql/functions/sum-transact-sql.md)(**occurrence_count**) WHERE- **Schlüsselwort**=*keyword_value* )  
  
-   Wie oft ein Schlüsselwort in einem bestimmten Dokument bzw. in einer Zeile vorkommt  
  
-   Wie viele Schlüsselwörter ein bestimmtes Dokument bzw. eine Zeile enthält  
  
 Darüber hinaus können Sie anhand der von sys.dm_fts_index_keywords_by_document zurückgegebenen Informationen alle Schlüsselwörter eines gegebenen Dokuments oder einer gegebenen Zeile abrufen.  
  
 Wenn die Volltextschlüsselspalte wie empfohlen mit dem integer-Datentyp definiert ist, kann die document_id direkt dem Volltextschlüsselwert in der Basistabelle zugeordnet werden.  
  
 Wenn als Datentyp für die Volltextschlüsselspalte jedoch ein anderer Typ als Integer festgelegt ist, stellt document_id nicht den Volltextschlüsselwert in der Basistabelle dar. Um in diesem Fall die Zeile in der Basistabelle zu identifizieren, die von dm_fts_index_keywords_by_document zurückgegeben wird, müssen Sie diese Ansicht mit den von [sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)zurückgegebenen Ergebnissen verknüpfen. Speichern Sie jedoch zuvor die Ausgabe der gespeicherten Prozedur in eine temporäre Tabelle. Anschließend können Sie die Spalte document_id von dm_fts_index_keywords_by_document mit der von der gespeicherten Prozedur zurückgegebenen Spalte DOCID verknüpfen. Beachten Sie, dass eine **Zeitstempel** -Spalte keine Werte zum Zeitpunkt des Einfügens empfangen kann, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]da Sie von automatisch generiert werden. Daher muss die **Zeitstempel** -Spalte in **varbinary (8)** -Spalten konvertiert werden. Das folgende Beispiel zeigt die erforderlichen Schritte: In diesem Beispiel ist *table_id* die ID der Tabelle, *database_name* der Name der Datenbank und *table_name* der Name der Tabelle ist.  
  
```  
USE database_name;  
GO  
CREATE TABLE #MyTempTable   
   (  
      docid INT PRIMARY KEY ,  
      [key] INT NOT NULL  
   );  
DECLARE @db_id int = db_id(N'database_name');  
DECLARE @table_id int = OBJECT_ID(N'table_name');  
INSERT INTO #MyTempTable EXEC sp_fulltext_keymappings @table_id;  
SELECT * FROM sys.dm_fts_index_keywords_by_document   
   ( @db_id, @table_id ) kbd  
   INNER JOIN #MyTempTable tt ON tt.[docid]=kbd.document_id;  
GO  
  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert CREATE FULLTEXT CATALOG-Berechtigungen und die SELECT-Berechtigung für die vom Volltextindex abgedeckten Spalten.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-full-text-index-content-at-the-document-level"></a>A. Anzeigen des Inhalts eines Volltextindexes auf Dokumentebene  
 Im folgenden Beispiel wird der Inhalt des Volltextindexes auf Dokumentebene in der `HumanResources.JobCandidate`-Tabelle der `AdventureWorks2012`-Beispieldatenbank angezeigt.  
  
> [!NOTE]  
>  Sie können diesen Index erstellen, indem Sie das Beispiel ausführen, `HumanResources.JobCandidate` das für die-Tabelle in [CREATE FULLTEXT Index &#40;Transact-SQL-&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)bereitgestellt wird.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_by_document(db_id('AdventureWorks'),   
object_id('HumanResources.JobCandidate'));  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten und Funktionen für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Voll Text Suche](../../relational-databases/search/full-text-search.md)   
 [sys. dm_fts_index_keywords &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [sp_fulltext_keymappings &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)   
 [Verbessern der Leistung von Volltextindizes](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)  
  
  
