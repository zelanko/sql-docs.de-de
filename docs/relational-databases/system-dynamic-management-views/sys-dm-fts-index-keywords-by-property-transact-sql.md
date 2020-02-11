---
title: sys. dm_fts_index_keywords_by_property (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords_by_property
- dm_fts_index_keywords_by_property_TSQL
- sys.dm_fts_index_keywords_by_property
- sys.dm_fts_index_keywords_by_property_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], troubleshooting
- search property lists [SQL Server], viewing keywords by property
- full-text search [SQL Server], viewing keywords
- sys.dm_fts_index_keywords_by_property dynamic management view
ms.assetid: fa41e052-a79a-4194-9b1a-2885f7828500
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 82f433d18ff0940c9283f93cfa5e3f87179d31ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078552"
---
# <a name="sysdm_fts_index_keywords_by_property-transact-sql"></a>sys.dm_fts_index_keywords_by_property (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt alle eigenschaftsbezogenen Inhalte im Volltextindex einer angegebenen Tabelle zurück. Dies schließt alle Daten ein, die zu Eigenschaften gehören, die von der diesem Volltextindex zugeordneten Sucheigenschaftenliste registriert wurden.  
  
 sys. dm_fts_index_keywords_by_property ist eine dynamische Verwaltungsfunktion, mit der Sie erkennen können, welche registrierten Eigenschaften von IFilters bei der Index Zeit ausgegeben wurden, sowie den genauen Inhalt jeder Eigenschaft in jedem indizierten Dokument.  
  
 **So zeigen Sie alle Inhalte auf Dokumentebene (einschließlich eigenschaftsbezogener Inhalte) an**  
  
-   [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
 **So zeigen Sie Informationen zu einem Volltextindex auf höherer Ebene an**  
  
-   [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)  
  
> [!NOTE]  
>  Weitere Informationen zu Such Eigenschaften Listen finden Sie unter [Durchsuchen von Dokumenteigenschaften mit Such Eigenschaften Listen](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.dm_fts_index_keywords_by_property  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Argumente  
 DB_ID ('*database_name*')  
 Ein Aufrufder [DB_ID ()](../../t-sql/functions/db-id-transact-sql.md) -Funktion. Diese Funktion akzeptiert einen Datenbanknamen und gibt die Datenbank-ID zurück, die sys. dm_fts_index_keywords_by_property verwendet, um die angegebene Datenbank zu suchen. Wenn *database_name* nicht angegeben ist, wird die aktuelle Datenbank-ID zurückgegeben.  
  
 object_id ('*table_name*')  
 Ein Aufrufder [object_id ()](../../t-sql/functions/object-id-transact-sql.md) -Funktion. Diese Funktion akzeptiert einen Tabellennamen und gibt die Tabellen-ID der Tabelle zurück, die den zu überprüfenden Volltextindex enthält.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Column|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|Schlüsselwort (keyword)|**nvarchar(4000)**|Die hexadezimale Darstellung des Schlüsselworts, das im Volltextindex gespeichert ist.<br /><br /> Hinweis: OxFF stellt das Sonderzeichen dar, das das Ende einer Datei oder eines Datasets angibt.|  
|display_term|**nvarchar(4000)**|Die Klartextform des Schlüsselworts. Dieses Format wird vom internen Format abgeleitet, das im Volltextindex gespeichert ist.<br /><br /> Hinweis: OxFF stellt das Sonderzeichen dar, das das Ende einer Datei oder eines Datasets angibt.|  
|column_id|**int**|Die ID der Spalte für die Volltextindizierung des aktuellen Schlüsselworts.|  
|document_id|**int**|Die ID des Dokuments bzw. der Zeile für die Volltextindizierung des aktuellen Ausdrucks. Diese ID entspricht dem Volltextschlüsselwert dieses Dokuments bzw. dieser Zeile.|  
|property_id|**int**|Interne Eigenschaften-ID der Such Eigenschaft im Volltextindex der Tabelle, die Sie im object_id Parameter ('*table_name*') angegeben haben.<br /><br /> Wenn einer Sucheigenschaftenliste eine angegebene Eigenschaft hinzugefügt wird, registriert die Volltext-Engine die Eigenschaft und weist ihr eine interne Eigenschaften-ID zu, die für diese Eigenschaftenliste spezifisch ist. Die interne Eigenschaften-ID stellt eine ganze Zahl dar und ist für eine bestimmte Sucheigenschaftenliste eindeutig. Wenn eine bestimmte Eigenschaft für mehrere Sucheigenschaftenlisten registriert wird, kann für jede Sucheigenschaftenliste eine andere interne Eigenschaften-ID zugewiesen werden.<br /><br /> Hinweis: die interne Eigenschaften-ID unterscheidet sich vom ganzzahligen Eigenschafts Bezeichner, der angegeben wird, wenn die Eigenschaft der Such Eigenschaften Liste hinzugefügt wird. Weitere Informationen finden Sie unter [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md).<br /><br /> So zeigen Sie die Zuordnung zwischen property_id und dem Eigenschaftsnamen an:<br />                    [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese dynamische Verwaltungs Sicht kann Fragen wie die folgenden beantworten:  
  
-   Welcher Inhalt wird in einer angegebenen Eigenschaft für eine angegebene DocID gespeichert?  
  
-   Wie gängig ist eine angegebene Eigenschaft im Hinblick auf indizierte Dokumente?  
  
-   Welche Dokumente enthalten eigentlich eine angegebene Eigenschaft? Dies ist nützlich, wenn die Abfrage in einer angegebenen Sucheigenschaft nicht wie erwartet ein Dokument zurückgibt.  
  
 Wenn die Volltextschlüsselspalte wie empfohlen mit dem integer-Datentyp definiert ist, kann die document_id direkt dem Volltextschlüsselwert in der Basistabelle zugeordnet werden.  
  
 Wenn als Datentyp für die Volltextschlüsselspalte jedoch ein anderer Typ als Integer festgelegt ist, stellt document_id nicht den Volltextschlüsselwert in der Basistabelle dar. Um in diesem Fall die Zeile in der Basistabelle zu identifizieren, die von dm_fts_index_keywords_by_property zurückgegeben wird, müssen Sie diese Ansicht mit den von [sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)zurückgegebenen Ergebnissen verknüpfen. Speichern Sie jedoch zuvor die Ausgabe der gespeicherten Prozedur in eine temporäre Tabelle. Anschließend können Sie die Spalte document_id dm_fts_index_keywords_by_property mit der DocId-Spalte verknüpfen, die von dieser gespeicherten Prozedur zurückgegeben wird. Beachten Sie, dass eine **Zeitstempel** -Spalte keine Werte zum Zeitpunkt des Einfügens empfangen kann, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]da Sie von automatisch generiert werden. Daher muss die **Zeitstempel** -Spalte in **varbinary (8)** -Spalten konvertiert werden. Das folgende Beispiel zeigt die erforderlichen Schritte: In diesem Beispiel ist *table_id* die ID der Tabelle, *database_name* der Name der Datenbank und *table_name* der Name der Tabelle ist.  
  
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
SELECT * FROM sys.dm_fts_index_keywords_by_property   
   ( @db_id, @table_id ) kbd  
   INNER JOIN #MyTempTable tt ON tt.[docid]=kbd.document_id;  
GO  
  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert CREATE FULLTEXT CATALOG-Berechtigungen und die SELECT-Berechtigung für die vom Volltextindex abgedeckten Spalten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Schlüsselwörter in der `Author`-Eigenschaft im Volltextindex der `Production.Document`-Tabelle der `AdventureWorks`-Beispieldatenbank zurückgegeben. Im Beispiel wird der Alias `KWBPOP` für die von **sys. dm_fts_index_keywords_by_property**zurückgegebene Tabelle verwendet. Im Beispiel werden innere Joins zum Kombinieren von Spalten aus [sys. registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) und [sys. fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)verwendet.  
  
```  
-- Once the full-text index is configured to support property searching  
-- on the Author property, return any keywords indexed for this property.  
USE AdventureWorks2012;  
GO   
SELECT KWBPOP.* FROM   
   sys.dm_fts_index_keywords_by_property( DB_ID(),   
   object_id('Production.Document') ) AS KWBPOP  
   INNER JOIN  
      sys.registered_search_properties AS RSP ON(   
         (KWBPOP.property_id = RSP.property_id)   
         AND (RSP.property_name = 'Author') )  
   INNER JOIN  
      sys.fulltext_indexes AS FTI ON(   
         (FTI.[object_id] = object_id('Production.Document'))   
         AND (RSP.property_list_id = FTI.property_list_id) );  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Voll Text Suche](../../relational-databases/search/full-text-search.md)   
 [Verbessern der Leistung von voll Text Indizes](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [sp_fulltext_keymappings &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)   
 [sys. dm_fts_index_keywords_by_document &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)   
 [sys. dm_fts_index_keywords &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)   
 [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
